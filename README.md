# Aliyun-DDNS-CentOS-RPM
使用超简单的阿里云DDNS, 省的折腾

## 说明
适合家用服务器,前提是分配了公网IP,阿里云申请了域名,痛点是公网ip变幻莫测

## 前提
创建了RAM AccessKey, 安装Java环境

## 安装
```
rpm -ivh https://github.com/niebinxiao/ddns-centos-rpm/releases/download/v1.0-alpha/ddns-1.0-release.noarch.rpm
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
自动启动, 热更新, 日志在 /etc/ddns/log/ddns.log
```
tail -f /etc/ddns/log/ddns.log
2020-05-22 04:02:06.990 [main] ERROR cloud.tools.aliyun.sdk.tool.SDKTools - AccessKeyId和AccessSecret未配置或配置异常
2020-05-22 04:03:08.160 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [当前公网IP: 157.0.xx.xxx, 当前域名解析IP: 169.x.xx.87]
2020-05-22 04:03:08.589 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - {"recordId":"19738875704xxx","requestId":"xxxxx-E2F4-4729-A77A-xxxxxx"}
2020-05-22 04:03:08.589 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 解析域名已修改
```
