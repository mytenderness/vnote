# romstrap
## barsize 修改
vim dgpu_ext_rom.hex +103
bit 6 -9 , 
1000  64G
0111  32G
0110 16G
0001 512M
0000 256M

| BarSize | BitVal | HexVal |
| ------- | ------ | ------ |
| 64G     | 1000   | 0x7E00 |
| 32G     | 0111   | 0x7DC0 |
| 16G     | 0110   | 0x7D80 |
| 512M    | 0001   | 0x7C40 |
| 256M    | 0000   | 0x7C00 |

## ems 信息修改 0x1100030
vim dgpu_ext_rom.hex +25
bit0-1 : HBM_SIZE, 1:16G 2:32G 3:64G
bit2-7 : RESERVED
bit8-9 : Build VER, 1:SOC_ONLY 2:GC 3:QEMU
bit10-31 RESERVED

|  Bit  |   Info    |          VAL           |
| ----- | --------- | ---------------------- |
| 0-1   | HBM_SIZE  | 1:16G 2:32G 3:64G      |
| 2-7   | RESERVED  |                        |
| 8-9   | Build VER | 1:SOC_ONLY 2:GC 3:QEMU |
| 10-31 | RESERVED  |                        |