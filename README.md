# Aliyun-DDNS-CentOS-RPM
使用超简单的阿里云DDNS, 省的折腾

## 说明
适合家用服务器,前提是分配了公网IP,阿里云申请了域名,创建了RAM AccessKey,痛点是域名变幻莫测

## 安装
```
rpm -ivh ddns-1.0-release.noarch.rpm
```

## 配置
```
vim /etc/ddns/conf/ddns.conf

AccessKeyId= # AccessKeyId
AccessSecret= # AccessSecret
DomainName= # 主域名
RRKeyWord= # 子域名
Type=A
RunOnMinutes=5 # 多长时间运行一次

# 邮箱可选, 不通知可以不配
MailAddress=443753501@qq.com # 发件人地址
MailHost=smtp.qq.com # 邮箱主机
MainEncipher=tls # 加密协议 ssl or tls
MainProtocol=smtp # 通讯协议 smtp or pop3
MainPort=25 # 通讯端口
MailAccout=443753501@qq.com # 邮箱账号
MailPassword= # 密码
MailReceivers=443753501@qq.com # 接收人邮箱地址
```


## 使用
完事了, 自动启动, 热更新, 日志在 /etc/ddns/log/ddns.log








```
