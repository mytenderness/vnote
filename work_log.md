# work_log

- ZF diagslim v06.01.19 更新
    - 更新支持vbios升级后数据检查，确保测试后标卡中vbios为发布版本
    

- 曙光环境 KM gen1 vbios mp0 死机测试
  - 屏蔽RSMU中断测试正常，具体原因待查
  - 对比测试发现和vbios中rsmu 中断处理流程相关：
    - gen1 时曙光环境会产生一个swus_link_reset中断
    - PASS: RSMU SECINTR中断在中断处理函数中处理，没有hang死
    - FAIL:RSMU SECINTR中断在main函数中处理（中断处理函数中只记录中断标记），mp0 hang死
  
