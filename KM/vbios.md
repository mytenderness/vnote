# vbios
0x398,0x100
# KM VBIOS GDBSTUB
echo "hygon123;" | ./hygonvbflash -p a dcu_vbios.bin -l fix.cfg --passwd
dcu_vbios.bin 换成你的 vbios
fix.cfg里面写0x398,0x100