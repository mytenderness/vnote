# build_rel

# ems v04 release(20230330)
当前版本使用的是EMU team的资源,HBM 测试PASS
资源说明：
 - fuse 为全0
 - romstrap invalid
 - vbios 未加载

## soc only
 - 启动方式: ems_emu_run
 - build: bowen_soc_only_cl404289_20230323
 - 24 avbs,312 kHz
### soc 初始化方式：
 - 步骤1：加载unitest驱动
 - 步骤2：执行/home/hygon/liaochenghuan/work/bowen/unitest/v1/bw_unitest/demo/init_seq_0324.py 文件  

## gc (需要3排资源)
 - 启动方式: ems_emu_run gc
 - build: bowen_lite_cl405736_20230327_full
 - 42 avbs,322 kHz
### gc 初始化方式:
 - 步骤1：加载unitest驱动
 - 步骤2：执行/home/hygon/liaochenghuan/work/bowen/unitest/v1/bw_unitest/demo/init_seq_0324.py 文件  
 - 步骤3：执行/home/hygon/bowena0_vbios/HygonVBios/pcie/build/hygon_vbios_pcie_bowen_gc_only_mmhub_0331
   
## 待更新
  - 使用 golden fuse / romstrap (gen5 dis)
  - 调试中，状态：bar size不对, hbm 访问错误
 

## soc 最新build(bld_bw_v08_20230329)初始化方式：
cd /home/hygon/bowena0_vbios/
./soc_only_vbios.sh
更新日志：
1.更新umc ucode
2.更新DF goldensetting


## gc 最新build(未裁剪版本)初始化方式：
cd /home/hygon/bowena0_vbios/
./gc_vbios.sh
更新日志：
1.更新umc ucode
2.更新DF goldensetting


# gc v05 release(20230418)
 - build版本：bowen_lite_cl414376
 - 问题：romstrap会导致testpc无法启动
 - 解决方案：通过配置fuse disable romstrap后testpc启动正常
 - 状态：
    - pcie 相关fuse暂未验证
    - vbios: gdbstub support
    - bar size 512M

gc v05 已更新到 `ems_emu_run gc`,上个版本运行参考`ems_emu_run gc_v04`

# EMS 更新 (v08)
ems_emu_run 命令更新
 - 新增 `ems_emu_run -h`，查询命令使用说明
 - 新增 `ems_emu_run <case> -l`， 查询对应case信息
 - 新增 `ems_emu_run <case> -t hours`， 定时退出emu
 
# gc v06 release(20230504)
 - build版本：bowen_lite_cl417617 , 42 avbs
 - 状态:
    - pcie: gen4
    - fuse/romstrap: golden v2
    - vbios: gdbstub support
    - bar size: 32G
 - 启动：`ems_emu_run gc` or `ems_emu_run gc_v06`
  
# qemu v06 release(20230504)
 - build版本：bowen_lite_cl417617 , 42 avbs (virtual)
 - 状态: 未验证
    - pcie: gen5
    - fuse/romstrap: golden v2
    - vbios: gdbstub support
    - bar size: 32G
 - 启动：`ems_emu_run qemu` or `ems_emu_run qemu_v06`
 - 退出：emu 终端输入`exit` (不支持ems_emu_end)
 
# soc v06 release(20230525)
 - build版本：bowen_soc_only_cl426125_16density , 26 avbs
 - 状态:
    - pcie: gen4
    - fuse/romstrap: golden v2
    - vbios: gdbstub support
    - bar size: 32G
 - 启动：`ems_emu_run soc` or `ems_emu_run soc_v06`
 
# GC v07 release(20230606)
 - build版本：build_bowen_lite_cl426126_areaopt , 40 avbs
 - 状态:
    - pcie: gen4
    - fuse/romstrap: golden v2
    - vbios: gdbstub support
    - bar size: 32G
 - 启动：`ems_emu_run gc` or `ems_emu_run gc_v07`
 
# GC v08 release(20230609)
 - build版本：build_bowen_lite_cl430097_0 , 40 avbs
 - 状态:
    - pcie: gen4
    - fuse/romstrap: golden v2
    - vbios: gdbstub support
    - bar size: 32G
 - 启动：`ems_emu_run gc` or `ems_emu_run gc_v08`