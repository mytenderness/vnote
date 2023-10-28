# git remote

## 驱动
 - http://172.18.228.101:9900/zifang/radeonopencompute/rock-kernel-refactory.git
    - hygon-4.5.2

## hydqst
 - http://172.18.228.101:9900/DCU/eco/hyd-quantify-stress.git
    - hygon-4.5.2
    
## unittest
 - http://172.18.228.101:9900/DCU/unittest.git
    - KM_B0_UNITTEST_MASTER
    
## minicode
 - http://172.18.228.101:9900/yangxiong/minicode.git
    - regdumptool
    
## ats
 - http://172.18.228.101:9900/mayu/ats_post_silicon.git
    - km_b0
    
## SLT
 - http://172.18.228.101:9900/DCU/tools/dcu_pts.git
 - beijn: http://10.60.44.20:9900/DCU/tools/dcu_pts.git
    - git clone -b dcu_pts http://172.18.228.101:9900/DCU/tools/dcu_pts.git
    
## pptable
 -  http://172.18.228.101:9900/liuzhuo/pptable_tool.git
    - master

## rocm_bandwidth_test
 - http://172.18.228.101:9900/zifang/radeonopencompute/rocm_bandwidth_test.git
     - hygon-4.5

## gemm-stress
 - http://172.18.228.101:9900/DCU/eco/gemm-stress.git

```bash
mkdir build; cd build;
cmake .. ; make
export HYD_INTERNAL=1
./gemm-stress --mode=compute -test-type 1
./gemm-stress --mode=compute -test-type 2
cp datac_midpower.h datac_balance.h ../data/
cmake ..
make
```

## HygonDCUPerfStressTestSuite 
 - http://172.18.228.101:9900/DCU/tools/hygondcuperfstresstestsuite.git
 