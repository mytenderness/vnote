# gemm_power

5.2 生成校验值

```bash
./gemmPower -s 12000 -g 0 -f kernel/km/dgemm_dp4x.co -o golden/km/dgemm_s12000.dat
./gemmPower -s 12000 -g 1 -f kernel/km/sgemm.co -o golden/km/sgemm_s12000.dat
./gemmPower -s 12000 -g 2 -f kernel/km/hgemm.co -o golden/km/hgemm_s12000.dat
./gemmPower -s 12000 -g 3 -f kernel/km/i8gemm.co -o golden/km/i8gemm_s12000.dat
./gemmPower -s 12000 -g 4 -f kernel/km/i4gemm.co -o golden/km/i4gemm_s12000.dat
./gemmPower -s 12000 -g 5 -f kernel/km/i16gemm.co -o golden/km/i16gemm_s12000.dat
./gemmPower -s 12000 -g 6 -f kernel/km/i32gemm.co -o golden/km/i32gemm_s12000.dat
```