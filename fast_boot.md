# fast_boot

## 查询已开启服务
`systemctl list-unit-files | grep enable`

## 关闭服务
`systemctl disable xxx`

## 开启服务
`systemctl enable xxx`

## 分析流程

`systemd-analyze blame`
`systemd-analyze time`
`systemd-analyze critical-chain`
`/etc/fstab`
`sysv-rc-conf`

## 关闭online service
`systemctl mask systemd-networkd-wait-online.service`