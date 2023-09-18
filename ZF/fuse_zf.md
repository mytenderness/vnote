# fuse_zf

## harvest
use_override 0xa5 0xval[8:31] # DEBE_0
fuse_override 0xa6 0xval[0:31] # DEBE_1
fuse_override 0xa7 0xval[0:7] # DEBE_2

### ZF GC_DEBE

64CU harvet 分别对应 DEBE_0[31:8],DEBE_1[31:0],DEBE_2[7:0]
smn addr(0x5d294~0x5d2a0) >> 2 = 0x174A5~0x174A7

| Value | StartRow | StartBit | Size | StartPos | EndPos |  Smn  | IP  | Category |  Name  |
| ----- | -------- | -------- | ---- | -------- | ------ | ----- | --- | -------- | ------ |
| 0x0   | 165      | 8        | 32   | 5288     | 5319   | 5d294 | GC  | GC_DEBE  | DEBE_0 |
| 0x0   | 166      | 8        | 32   | 5320     | 5351   | 5d298 | GC  | GC_DEBE  | DEBE_1 |
| 0x0   | 167      | 8        | 32   | 5352     | 5383   | 5d29c | GC  | GC_DEBE  | DEBE_2 |
| 0x0   | 168      | 8        | 32   | 5384     | 5415   | 5d2a0 | GC  | GC_DEBE  | DEBE_3 |


## OPN FUSE ADDR
row: 436, hex: 0x1b4
smn: 0x5d6d0

## JTAG DISROM

```bash
fuse_override 0x8b 0x4000
```

## JTAG OPN SET

OPN
```bash
# 8180
fuse_override 0x1b4 0x8180
# 8176
fuse_override 0x1b4 0x8176
# 8171
fuse_override 0x1b4 0x8171
```

## JTAG DP4X/DP2X SET

DP2X
```bash
# DP4X
mp0_write_smn 0x8c00 0x01180040
# DP2X
mp0_write_smn 0x8c00 0x01180000
```

## SKIP PCIe IN BC

zifang skip pcie init by fastsim
```bash
# set MP0_FW_MISC_CTRL 0x1
# baco_reset
# set MP0_ROM_SCRATCH_6[16] 0x1, 0x10000
# set MP0_FW_MISC_CTRL 0x0
mp0_write_axi32 0x3200184 0x1
baco_reset
mp0_write_axi32 0x3260024 0x10000
mp0_write_axi32 0x3200184 0x0
```

zifang skip pcie load ucode by fuse
```bash
# BOOTCODE_SKIP_PCIE_PHY_UCODE_LOAD row 140 bit:0
# DISTRIBUTE_PCIE_FUSES row:139 bit:30
# SKIP_WAITING_FOR_PCIE_PHY_CALIBRATION_DONE row:139 bit:15

fuse_override 0x8c 0x1
fuse_override 0x8b 0x40008000
```
