iwe项目实现的微信个人号通道，使用ipad协议登录，该协议能获取到wxid，能发送语音条消息，相比itchat协议更稳定。
为了大家稳定运行，限制只能登录2个微信。

程序免费使用

## Docker 部署

使用 Docker 快速部署 iwd 服务端：

```
docker run -d --name iwe --restart=always -p 8849:8849 registry.cn-wulanchabu.aliyuncs.com/iwe/iwe:v2.6
```

## 软件配置

系统需要安装 curl

mac_myapp 为 Mac 系统下的执行文件

myapp 为 Linux 系统下的执行文件

myapp.exe 为 Windows 系统下的执行文件

> `assets/setting.json`：全局配置
> 修改 mysql 数据库连接信息
> 修改 redis 数据库连接信息

执行 ./myapp 启动服务

> `assets/owner.json`：管理员/所有者 配置

### setting.json

> 你能修改的字段如下，其他字段**不用修改！不用修改！**；
>
> - debug：是否开启 debug 日志；
> - port：当前服务端口号；
> - apiVersion：当前服务 API 版本，例如这里的`/v849`就是 API 版本，`http://127.0.0.1:8848/v849`；可以设为空简化 URL，此时服务 BASE_URL 为`http://127.0.0.1:8848`；
> - ghWxid：要引流关注的微信公众号的 wxid；新用户登录时自动关注；默认为空，不关注任何公众号；
> - redisConfig.Port：Redis 服务端口号；
> - redisConfig.Db：要使用的 Redis 几号数据库；
> - redisConfig.Pass：Redis 服务密码；
> - mySqlConnectStr：`用户名:密码@tcp(127.0.0.1:3306)/数据库名?charset=utf8mb4&parseTime=true&loc=Local`；
> -
> - kafka: false 是否使用 Kafka 作为消息队列，默认 false 不使用，true 使用；
> - rabbitMq: false 是否使用 RabbitMQ 作为消息队列，默认 false 不使用，true 使用；

> - newsSynWxId: false 是否同步微信 id (默认 false)，true 同步，false 不同步 ；
> - topic:wx_sync_msg_topic 同步消息的 topic 名称，默认 wx_sync_msg_topic ；

## 更新日志

[2025-05-28]

- iwe v2.6 优化docker 日志，减少无用日志信息
- iwe v2.6 修复开启rabbitmq 消息还会存到redis 问题

[2025-05-20]

- iwe v2.5 增加文件助手管理命令
- iwe v2.5 更新版本号

[2025-05-18]

- iwe v2.4 修复bug

[2025-05-08]

- iwe v2.3 修复回调接口 HTTP 客户端连接未正确复用导致的协程泄漏 bug
- iwe v2.2 修复若干已知 bug
- iwe v2.0 增加回调地址设置，设置前请确保回调地址可用；开启回调消息不会保存到 Redis

[2025-05-07]

- iwe v1.0 直接可用，运行成功后查看日志，获取管理密码 ADMIN_KEY
- 访问：http://ip:8489 即可查看 API 接口信息，其他请自行探索！
