# 企业微信Jenkins构建通知插件

[![Build Status](https://ci.jenkins.io/buildStatus/icon?job=Plugins%2Fqy-wechat-notification-plugin%2Fmaster)](https://ci.jenkins.io/job/Plugins/job/qy-wechat-notification-plugin/job/master/)
[![Jenkins Plugin](https://img.shields.io/jenkins/plugin/v/qy-wechat-notification.svg)](https://plugins.jenkins.io/qy-wechat-notification)

> 该插件适用于使用"企业微信"工作的小伙伴，在Jenkins项目构建时使用群机器人进行状态通知
>
> 需要不低于企业微信 2.8.7版本

## 添加群机器人

任意群成员，都可以通过`右键`群名称的进行添加群机器人

![添加微信群机器人](https://user-images.githubusercontent.com/16626084/113484812-ddcf5300-94dc-11eb-83ee-9ed7ced2b3f4.png)


企业微信会给新增加的群机器人分配一个Webhook，作为通知接口
![添加微信群机器人](https://user-images.githubusercontent.com/16626084/113484800-ce500a00-94dc-11eb-9727-de9e1581ee4e.png)


## 项目配置

在Jenkins项目底部的`构建后操作`，添加`企业微信通知配置`
![image](https://user-images.githubusercontent.com/16626084/113484817-e758bb00-94dc-11eb-9c80-a08c800c09ae.png)



将Webhook地址信息输入Jenkins中，即可完成最简单配置
![将地址信息输入Jenkins中1](https://user-images.githubusercontent.com/16626084/113484741-8204ca00-94dc-11eb-8add-d81941987a4d.png)


可配置的控制项（可多选）：
- 是否仅失败才发送信息
- 是否仅成功才发送信息
- 是否仅中断才发送信息
- 是否仅不稳定构建才发送信息
- 是否仅失败才@
- 是否发送开始构建信息

## 运行效果

在构建开始的时候，群机器人会执行开始构建通知 (需勾选"发送开始构建信息")
![构建开始通知](https://user-images.githubusercontent.com/16626084/113484863-26870c00-94dd-11eb-91fc-b6cbe3aee0d5.png)


构建成功后，群机器人会执行构建成功的通知 (需勾选"仅成功才发送信息")
![构建成功通知](https://user-images.githubusercontent.com/16626084/113484867-2be45680-94dd-11eb-8b04-415cabd1e4b1.png)


构建失败时，群机器人则会执行失败的通知 (需勾选"仅失败才发送信息")

![构建失败通知1](https://user-images.githubusercontent.com/16626084/113484762-9cd73e80-94dc-11eb-829e-f5edc3bb1720.png)
![构建失败通知](https://user-images.githubusercontent.com/16626084/113484873-37d01880-94dd-11eb-84d3-8f4548754c50.png)




## 项目开发

配置单独的maven仓库（不然没办法开发）
```
https://stackoverflow.com/a/43690775
https://mvnrepository.com/artifact/org.jenkins-ci.plugins/git?repo=jenkins-releases
```

```
mvn org.jenkins-ci.tools:maven-hpi-plugin:run
```

打开Jenkins地址
```
http://127.0.0.1:8080/jenkins
```

项目DEBUG
````
set MAVEN_OPTS=-Xdebug -Xrunjdwp:transport=dt_socket,server=y,address=8000,suspend=n
````

项目打包
````
mvn package
````
