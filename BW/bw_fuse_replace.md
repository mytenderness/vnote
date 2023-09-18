# bw_fuse_replace

## pub_replace_addr row 137-1006
- org:
row 521, 0x209 n_reserved_1
val = 1

- replace:
row 1010, 0x3f2 not used
val = 0x2

replace 数据规则:
new_data[21:0] | org_addr[9:0]
new_data_1[11:0] | org_addr_1[9:0] | new_data[31:22]
xxxx | new_data_1[31:12]

replace_row 0x3f2 = `0x209 | (0x2 << 10)`
replace_row 0x3f2 = 0xA09

- pub_replace_addr
row 137, 0x89 bit:0:19
val = 0x3f2 (0x3f2 << 0)

## 配置流程

```bash
fuse_override 0x209 0x1 # row 521 box2+10
fuse_override 0x3f2 0xA09 # row 1010 box3+243
fuse_override 0x89 0x3f2 # row 137
```

## scu_replace_addr row 0-102
- org:
row 35, 0x23 y_reserved_0
val = 1

- replace:
row 1010, 0x3f2 not used
val = 0x2

replace 数据规则:
new_data[21:0] | org_addr[9:0]
new_data_1[11:0] | org_addr_1[9:0] | new_data[31:22]
xxxx | new_data_1[31:12]

replace_row 0x3f2 = `0x23 | (0x2 << 10)`
replace_row 0x3f2 = 0x823

0x3f2,0x823

- pub_replace_addr
row 0, 0x0  bit 6:25
val = 0xFC87 (0x3f2 << 6 | 0x7)

## 配置流程

```bash
fuse_override 0x23 0x1 # row 35 box0+36
fuse_override 0x3f2 0x823 # row 1010 box3+243
fuse_override 0x0 0xFC87 # row 0 box0+1
```

## root_replace_addr row 104-123
- org:
row 116, 0x74 ROOT_KEY_ECC_0
val = 1

- replace:
row 1010, 0x3f2 not used
row 1011, 0x3f3 not used
val = 0x2

replace 数据规则:
new_data[21:0] | org_addr[9:0]
new_data_1[11:0] | org_addr_1[9:0] | new_data[31:22]
xxxx | new_data_1[31:12]

replace_row 0x3f2 = `0x74 | (0x2 << 10)`
replace_row 0x3f2 = 0x874

0x3f2,0x874

- pub_replace_addr
row 103, 0x67  bit 3:22
val = 0x1F90 (0x3f2 << 3)

## 配置流程

```bash
fuse_override 0x74 0x1 # row 116 box0+117
fuse_override 0x3f2 0x874 # row 1010 box3+243
fuse_override 0x67 0x1F90 # row 103 box0+104
```
