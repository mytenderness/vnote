# reg
SQ_CONFIG: 0x8C00
SPI_CONFIG_CNTL_2: 0x31108
CP_SAVE_RESTORE_CNTL: 0x86DC

# dp4x

```bash
SQ_CONFIG |= (0x1 << 6)
SPI_CONFIG_CNTL_2 |= (0x1 << 8)
CP_SAVE_RESTORE_CNTL = 0x1
```

# dp2x

```bash
SQ_CONFIG &= ~(0x1 << 6)
SPI_CONFIG_CNTL_2 &= ~(0x1 << 8)
CP_SAVE_RESTORE_CNTL = 0x0
```