vega20c_ft4232.tcl
vega20c_common_init.tcl
vega20c_toolset.tcl
vega20c_board_config.tcl

vega20c_ft4232_a5.tcl
ftdi_common_init.tcl

cevpn.hygon.cn

hygon.cn

setpci -s 43:00.0 0x4.b=0x7

# 专利

1. 一种芯片efuse数据烧写方法、装置及存储介质
读取所述efuse地址中所述检测地址上烧写的数据；
确定读取的数据与所述预设检测数据是否相同；
若读取的数据与所述预设检测数据相同，则确定烧写有所述芯片的基本数据的地址，
并根据确定的地址对烧写的所述芯片的基本数据进行正确性校验；若校验结果通过，则确
定所述芯片为良品；若校验结果未通过，则确定所述芯片为非良品；

2. 基于硬件电路的数据校验方法及装置



### bc_ats

run : `python run_test.py -d ../../case/zifang -j 10.65.56.51 -s 10.65.46.142 -r`




## PDE交流目标

- 昆山
  - 了解昆山的测试环境
    - 测试流程
    - 应用范围（谁在使用，如何使用）
  - 提前学习KM SLT主板的调测流程

- 苏州
  - 认识PDE同事 xuhongsi、zhangruiping、guixiaofeng
  - PDE部门人员面对面交流学习
     - 了解筛片效率，良率
     - 当前SLT套件问题，稳定性，修改建议
     - 芯片库存管理流程了解
     - 了解PDE与通富的工作关系，PDE拿到SLT之后的部署流程，PDE面对的生产问题
     - Fuse 烧录流程以及方式
     - JAR的使用现状，使用情况
     - kongming的生产需求
     - PDE实验室SLT测试环境状态
     - 与HCSW的环境差异
     - 与产线上环境的差异
  - 参观通富生产工厂
    - 了解ZIFANG SLT测试环境
      - 评估KONGMING的生产测试环境可能的差异性
    - 了解CPU生产测试环境
      - 对比DCU和CPU的生产差异

- 文档总结与分享