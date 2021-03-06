# phpChat
laravel + swoole + vue 直播聊天互动

###安装要求
1. laravel 版本比较高5.6.16 ，需要PHP 版本不小于 7.1.3
2. 安装swoole，同时swoole 配置选项支持协程，包括mysql 协程、redis 协程,请参考swoole 官网
3. npm 版本大于3.0.0，node 版本大于4.0.0


###项目实现目标
1. 实现直播用户发言互动
2. 使用nginx 代理转发websocket 请求，不开放websocket 端口对外访问，减少攻击入口
3. 通过文件，来进行swoole 重启，（通过swoole 定时器实现）不需要每次更新代码，找运维进行沟通，减少沟通成本，以及对程序掌控能力
4. 采用前后端分离方式进行开发，加深对项目合作过程中，对项目理解
5. 程序自动修复，如果swoole 挂断，自动重启，通过定时脚本
6. websocket 断线重连及心跳检测
7. 程序安装及相关配置，请分别参考backend、frontend 下read.me

* backend 是后端laravel 项目
* frontend 是前端vue 项目
* chat.2345.com.conf 是nginx 配置文件

#### 这次采用前后端分离方式单独实现
* 后端采用laravel 框架 ，使用swoole websocket 长链通信
* 前端采用vue.js + vuex + vue router + ele UI + webpack 实现 
#### nginx 代理转发
* [参考 链接](https://wiki.swoole.com/wiki/page/326.html)

### 缺陷
* 实际使用，laravel 框架比较重，可选用其他轻量级框架
* websocket 链接不建议保存为redis 里键值对
