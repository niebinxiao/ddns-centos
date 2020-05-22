# Aliyun-dDNS-CentOS
使用超简单的阿里云DDNS, 省的折腾

## 说明
适合家用服务器,前提是分配了公网IP,阿里云申请了域名,痛点是公网ip变幻莫测

## 前提
创建了RAM AccessKey, 安装Java环境

## 安装
```
rpm -ivh https://github.com/niebinxiao/ddns-centos/releases/download/v1.0-alpha/ddns-1.0-release.noarch.rpm
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
2020-05-23 07:02:51.638 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - DDNS服务启动成功
2020-05-23 07:02:51.651 [main] ERROR cloud.tools.aliyun.sdk.tool.SDKTools - AccessKeyId和AccessSecret未配置或配置异常
2020-05-23 07:03:01.650 [Thread-0] INFO  cloud.tools.aliyun.sdk.tool.SDKTools - 检测到配置文件有更新, 正在重新加载
2020-05-23 07:04:00.435 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [域名: isp.xxx.com,当前公网IP: 157.0.xx.210, 当前域名解析IP: 157.0.xx.210]
2020-05-23 07:04:01.654 [Thread-0] INFO  cloud.tools.aliyun.sdk.tool.SDKTools - 检测到配置文件有更新, 正在重新加载
2020-05-23 07:09:01.276 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [域名: bms.xxx.com,当前公网IP: 157.0.xx.210, 当前域名解析IP: 157.0.xx.21]
2020-05-23 07:09:01.715 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 解析域名已修改
2020-05-23 07:10:03.914 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [域名: bms.xxx.com,当前公网IP: 157.0.xx.210, 当前域名解析IP: 157.0.xx.210]
2020-05-23 07:11:04.722 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [域名: bms.xxx.com,当前公网IP: 157.0.xx.210, 当前域名解析IP: 157.0.xx.210]
2020-05-23 07:11:51.693 [Thread-0] INFO  cloud.tools.aliyun.sdk.tool.SDKTools - 检测到配置文件有更新, 正在重新加载
2020-05-23 07:12:05.520 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [域名: isp.xxx.com,当前公网IP: 157.0.xx.210, 当前域名解析IP: 157.0.xx.210]
2020-05-23 07:12:31.698 [Thread-0] INFO  cloud.tools.aliyun.sdk.tool.SDKTools - 检测到配置文件有更新, 正在重新加载
2020-05-23 07:13:06.303 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [域名: isp.xxx.com,当前公网IP: 157.0.xx.210, 当前域名解析IP: 157.0.xx.210]
2020-05-23 07:16:07.096 [main] INFO  cloud.tools.aliyun.sdk.ddns.DDNS - 检测结果: [域名: isp.xxx.com,当前公网IP: 157.0.xx.210, 当前域名解析IP: 157.0.xx.210]
```
