# slt
5.2 环境测试转4.5环境修改
rm -rf /etc/profile.d/hygon-env.sh

echo "blacklist hydcu" > /etc/modprobe.d/blacklist-hydcu.conf

