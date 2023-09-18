# add_net_dis

```bash
[root@cbd46n116 ~]# cat /etc/fstab

#
# /etc/fstab
# Created by anaconda on Thu Sep 17 22:28:06 2020
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/centos_bogon-root /                       xfs     defaults        0 0
UUID=f17f31f5-5b5c-449e-b13e-9ab173240c3b /boot                   xfs     defaults        0 0
UUID=B358-6FB0          /boot/efi               vfat    umask=0077,shortname=winnt 0 0
/dev/mapper/centos_bogon-home /home                   xfs     defaults        0 0
/dev/mapper/centos_bogon-swap swap                    swap    defaults        0 0
10.65.42.75:/home/power_test  /home/power_test nfs auto,rw,tcp,vers=4.1 0 0
```