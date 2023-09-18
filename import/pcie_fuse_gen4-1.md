# gen1-4 fuse

STRAP_BIF_STRAP_BIF_KILL_GEN4 	row:252 (0xFC) bit:12(0x1000)  EP,DP 8GT/s UP 16GT/s
STRAP_BIF_STRAP_BIF_KILL_GEN3	row:252 (0xFC) bit:1(0x2) EP,DP 5GT/s UP 16GT/s
fuse_override 0xfc 0x02341016   # kill gen 3/4

STRAP_BIF_STRAP_GEN2_EN_DEV0	row:259 (0x103) bit:14(0x4000)
STRAP_BIF_STRAP_GEN2_COMPLIANCE_DEV0	row:259 (0x103) bit:13(0x2000)
EP,DP 2.5GT/s UP 16GT/s
fuse_override 0xfc 0x02341016   # kill gen 3/4
fuse_override 0x103 0x8E3790DE

STRAP_BIF_STRAP_TARGET_LINK_SPEED_DEV0	row:259 (0x103) bit:17(0x60000),val=3
设置成0/1/2/3 仅修改EP,DP
fuse_override 0x103 0x8E31F0DE

STRAP_BIF_GEN4_COMPLIANCE = 1	row:283 (0x11b) bit:25(0x2000000)    设置无效
STRAP_BIF_STRAP_BIF_KILL_GEN4 = 0	row:252 (0xFC) bit:12(0x1000)
STRAP_BIF_STRAP_GEN4_COMPLIANCE_DEV0 = 1	row:259 (0x103) bit:16(0x10000)  设置无效
fuse_override 0x103 0x8E36F0DE

STRAP_BIF_GEN2_EN_w_A row:278 (0x116) bit:15(0x8000)  设置UP有效
STRAP_BIF_GEN3_EN_w_A row:278 (0x116) bit:16(0x10000)
STRAP_BIF_GEN4_EN_w_A row:278 (0x116) bit:17(0x20000)
fuse_override 0x116 0x20000

STRAP_BIF_KILL_GEN4 = 1	row:289 (0x121) bit:9(0x200) 设置无效
STRAP_BIF_KILL_GEN3 = 1 row:289 (0x121) bit:8(0x100) 设置无效
fuse_override 0x121 0x483E070E

STRAP_BIF_FORCE_GEN2_MODE row:283 (0x11b) bit:19(0x80000) 无效
STRAP_BIF_FORCE_GEN3_MODE row:283 (0x11b) bit:20(0x100000)
fuse_override 0x11b 0x9B885C23

STRAP_BIF_GEN2_COMPLIANCE row:283 (0x11b) bit:23(0x800000) 设置无效
STRAP_BIF_GEN3_COMPLIANCE row:283 (0x11b) bit:24(0x1000000)
STRAP_BIF_GEN4_COMPLIANCE row:283 (0x11b) bit:25(0x2000000)
fuse_override 0x11b 0x98005C23


romstrap:
STRAP_BIF_KILL_GEN4 = 1	rom echo "0x104,0x2018" >> fix.cfg 有效

## 背景：
bring up时需要准备不同预案，确保能够快速完成bring up，针对pcie需要准备gen4~gen1对应的fuse,默认配置为gen4

## 测试环境：
1. 需要CPU BIOS waite
2. 需要Jtag
3. vbios disable

## 测试步骤：

### pcie 设备信息查询
1. 获取设备id(Upstream) `01:00.0`
```bash
root@ubuntu:~# lspci -n | grep b7
01:00.0 0604: 1d94:23b7 (rev 01)
```
2. lspci 查询
```bash
lspci -vvvs 01:00.0
```

![lspci](E:\git\work_log\2022\picture\lspci.png)

### 配置为Gen3

fuse(zifang):
```txt
STRAP_BIF_GEN2_EN_w_A = 0 row:278 (0x116) bit:15
STRAP_BIF_GEN3_EN_w_A = 0 row:278 (0x116) bit:16
STRAP_BIF_GEN4_EN_w_A = 1 row:278 (0x116) bit:17
```

Jtag cmd:
```bash
fuse_override 0x116 0x20000
baco_reset
```

result:

```bash
root@ubuntu:~# lspci -vvvs 01:00.0 | grep LnkSta
                LnkSta: Speed 8GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
root@ubuntu:~# lspci -vvvs 02:00.0 | grep LnkSta
                LnkSta: Speed 16GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
root@ubuntu:~# lspci -vvvs 03:00.0 | grep LnkSta
                LnkSta: Speed 16GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
```

### 配置为Gen2

fuse(zifang):
```txt
STRAP_BIF_GEN2_EN_w_A = 0 row:278 (0x116) bit:15
STRAP_BIF_GEN3_EN_w_A = 1 row:278 (0x116) bit:16
STRAP_BIF_GEN4_EN_w_A = 1 row:278 (0x116) bit:17
```

Jtag cmd:
```bash
fuse_override 0x116 0x30000
baco_reset
```

result:

```bash
root@ubuntu:~# lspci -vvvs 01:00.0 | grep LnkSta
                LnkSta: Speed 5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
root@ubuntu:~# lspci -vvvs 02:00.0 | grep LnkSta
                LnkSta: Speed 16GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
root@ubuntu:~# lspci -vvvs 03:00.0 | grep LnkSta
                LnkSta: Speed 16GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
```

### 配置为Gen2

fuse(zifang):
```txt
STRAP_BIF_GEN2_EN_w_A = 0 row:278 (0x116) bit:15
STRAP_BIF_GEN3_EN_w_A = 1 row:278 (0x116) bit:16
STRAP_BIF_GEN4_EN_w_A = 1 row:278 (0x116) bit:17
```

Jtag cmd:
```bash
fuse_override 0x116 0x30000
baco_reset
```

result:

```bash
root@ubuntu:~# lspci -vvvs 01:00.0 | grep LnkSta
                LnkSta: Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
root@ubuntu:~# lspci -vvvs 02:00.0 | grep LnkSta
                LnkSta: Speed 16GT/s, Width x16, TrErr- Train- SlotClk+ DLActive+ BWMgmt+ ABWMgmt-
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
root@ubuntu:~# lspci -vvvs 03:00.0 | grep LnkSta
                LnkSta: Speed 16GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                LnkSta2: Current De-emphasis Level: -3.5dB, EqualizationComplete+, EqualizationPhase1+
```