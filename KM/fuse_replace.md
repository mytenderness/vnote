# fuse_replace


## pub_replace_addr
- org:
row 370, 0x172 reserved
val = 1

- replace:
row 800, 0x320 not used
row 801, 0x321 not used

val: bit 31- 1
replace 数据规则

org_data[21:0] | org_addr[9:0]
rep_data[11:0] | rep_addr[9:0] | org_data[31:22]
xxxx | rep_data[31:12]

0x320,0x572
0x321,0x2c8000

- pub_replace_addr
row 137, 0x89
val = 0x320

# 配置流程

```bash
fuse_override 0x172 0x1
fuse_override 0x320 0x572
fuse_override 0x321 0x2c8000

fuse_override 0x89 0x320
```
