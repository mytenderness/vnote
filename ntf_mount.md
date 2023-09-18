# ntf_mount
# unbuntu

```bash
sudo apt-get install nfs-kernel-server  # 安装 NFS服务器端
sudo apt-get install nfs-common         # 安装 NFS客户端

mkdir -p /home/slt_share
chmod 777 -R /home/slt_share

sudo vim /etc/exports
# 写入如下行
/home/slt_share *(rw,sync,no_root_squash,no_subtree_check)

sudo service nfs-server start //首次启动
sudo service nfs-server restart //重启

showmount -e
Export list for ubuntu1804:
/home/slt_share *

# clinet mount slt_share
mount -t nfs 10.65.46.218:/home/slt_share /mnt/share
```

## exportfs 命令用法
-a 全部挂载或卸载
-r 重新读取/etc/exports 中的信息 ，并同步更新/etc/exports、/var/lib/nfs/xtab
-u 卸载单一目录（和-a一起使用为卸载所有/etc/exports文件中的目录）
-v 在屏幕输出详细信息

## showmount 命令用法
-a 显示已经于客户端连接上的目录信息
-e IP或者hostname 显示此IP地址分享出来的目录
