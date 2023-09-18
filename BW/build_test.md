# buidl_test

# pcie info

```bash
lspci -n | grep 6310
lspci -s 65:00.0 -nvv
# upstream port
lspci -s 63:00.0 -nvv
# 0x6a 配置空间对应 speed ，0x5 对应gen5
lspci -s 63:00.0 -xxx

```

# unittest

```bash
source source_env.sh
source env_setup.sh
```

# df 

```bash
pt ITTest/df/it_df_ncm.py::test_ncm0_access_hbm_by_sdma
pt ITTest/df/it_df_gcm.py
```

# GC
```bash
pt SystemTest/test_aql_kdisp_T001.py
pt SystemTest/test_sysMem_aql.py
```