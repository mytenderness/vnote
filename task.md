# TODO
* [ ] 5-5 vbios 台达A01 board type = 3

# task
612项目需要更新一版软件，解决前期发现的Jira 问题（https://conf.hygon.cn/pages/viewpage.action?pageId=81573988）以及新的功能需求
上午讨论纪要如下：
参加人员: ruanyin ray xiaoliang mayu xiaoping
讨论事项：
1 612 主板和VR 说明
Board    V A01   台达A01  V 02
线序      1       2       2
VR      victor    inf     victor

2 需要合入功能
1 Baco Reset - 驱动
2 mem 功耗读不出来  - ruanyin 拉SG提供现场给Ray
3 双VR：  --  2个VBIOS （15号不一定）
4 第2款VR 校准； -- liubo/lich 先同步；

3 VBIOS 版本
给线序2板子， 2个VR  - 12G  ECCOFF mayu vbios    pptable-ray

版本： hygon4.5V1.8 , 因为主板原因，该版本只给612项目，不是目前成都通用环境；对应主板和VR为： 线序2主板， 2种VR, 验证环境需要联系北京同事协调  
版本集成时间：5月10号 各自完成上库后，mingliang开始构建测试
版本构建后：
xiaoliang 组织复测612 的jira 问题
