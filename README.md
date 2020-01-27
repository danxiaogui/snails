# Snails 框架
![](https://tva1.sinaimg.cn/large/006tNbRwgy1gb31ak9yfqj31h20u047a.jpg)

基于 [SpringBoot](https://spring.io/projects/spring-boot) + [Ng-Alain](https://ng-alain.com/) 前后端分离的实现，可以作为新手入门项目，也可以作为小项目的基础框架去扩展。目前 [Snails](https://zhuanlan.zhihu.com/p/103187754) 系统框架已支持基本的后台功能，基于简单、实用设计，并且已支持 [Docker](https://www.docker.com/) 进行项目部署。

- [Snails 框架](https://gitee.com/kuzan/snails)：编程入门，新手礼赞
- [snails-web 前端](https://gitee.com/kuzan/snails-web)：[Angular](https://angular.cn/) + [Ng-Zorro](https://ng.ant.design/docs/introduce/zh) + [Ng-Alain](https://ng-alain.com)
- [snails-api 后台](https://gitee.com/kuzan/snails-api)：[SpringBoot](https://spring.io/projects/spring-boot) + [JPA ](https://spring.io/guides/gs/accessing-data-jpa/)+ [lombok](https://projectlombok.org/) + [Java8](https://zhuanlan.zhihu.com/java8) + Mysql

### 源码
* 前端 snails-web
> Gitee：[https://gitee.com/kuzan/snails-web](https://gitee.com/kuzan/snails-web)
GitHub：[https://github.com/danxiaogui/snails-web](https://github.com/danxiaogui/snails-web)
* 后台 snails-api
> Gitee：[https://gitee.com/kuzan/snails-api](https://gitee.com/kuzan/snails-api)
 github：[https://github.com/danxiaogui/snails-api](https://github.com/danxiaogui/snails-api)


## 1、系统功能
* [x]  登陆、登出
* [x]  用户管理
* [x]  组织管理
* [x]  菜单管理，支持菜单动态配置
* [x]  在线用户
* [x]  登陆日志，记录系统用户的登陆登出行为
* [x]  http请求，将系统的所有请求进行拦截，并记录到数据库中
* [x]  系统异常，全局拦截系统的异常，并记录到数据库中
* [x]  支持系统数据初始化
* [x]  [snails-api 后台](https://gitee.com/kuzan/snails-api) 支持 Docker 部署
* [x]  [snails-web 前端](https://gitee.com/kuzan/snails-web) 支持 Docker 部署



## 2、启动系统前提 - Mysql

Mysql 配置文件地址：[application.yml](https://gitee.com/kuzan/snails-api/blob/master/src/main/resources/application.yml)

| IP        | Port | Username | Password | Database |
| --------- | ---- | -------- | -------- | -------- |
| localhost | 3306 | root     | 123456   | snails   |



## 3、启动系统 

### 3.1、方法1 【docker】

```shell
# 1、打包 snails-web 镜像
git clone https://gitee.com/kuzan/snails-web.git
cd snails-web
docker build -t snails-web .

# 2、打包 snails-api 镜像
git clone https://gitee.com/kuzan/snails-api.git
cd snails-api
mvn package docker:build

# 3、启动 docker 镜像
# 查看 docker 镜像
docker images | grep snails
# 运行 snails-web
docker run -d --name snails-web -p 4200:4200 snails-web
# 运行 snails-api
docker run -d --name snails-api -p 8081:8081 -t snails-api
# 查看运行中的 docker 实例
docker ps -a | grep snails

# 4、浏览器访问 localhost:4200 即可
```
![](https://images.gitee.com/uploads/images/2020/0116/171913_40cc02d7_2129289.jpeg)

### 3.2、方法2 

```shell
# 1、运行 snails-web
git clone https://gitee.com/kuzan/snails-web.git
cd snails-web
yarn
npm run start

# 2、运行 snails-api
git clone https://gitee.com/kuzan/snails-api.git
cd snails-api
mvn package
java -jar target/snails-0.1.jar

# 3、浏览器访问 localhost:4200 即可
```



## 4、系统截图 localhost:4200

### 4.1、登陆页面，账号：kuzank，密码：123456
![](https://images.gitee.com/uploads/images/2020/0116/115529_4c6de3e2_2129289.jpeg)

### 4.2、首页
![](https://tva1.sinaimg.cn/large/006tNbRwgy1gb31ak9yfqj31h20u047a.jpg)

### 4.3、用户管理
![](https://images.gitee.com/uploads/images/2020/0116/115529_c0fc1cb6_2129289.jpeg)

### 4.4、组织管理
![](https://images.gitee.com/uploads/images/2020/0116/115530_d4588fb6_2129289.jpeg)

### 4.5、菜单管理
![](https://images.gitee.com/uploads/images/2020/0116/115530_b7cd92de_2129289.jpeg)

### 4.6、在线用户
![](https://images.gitee.com/uploads/images/2020/0116/115530_8f3b0019_2129289.jpeg)

### 5.7、登陆日志
![](https://images.gitee.com/uploads/images/2020/0116/115530_32bf531e_2129289.jpeg)

### 4.8、http请求
![](https://images.gitee.com/uploads/images/2020/0116/115530_bfaa1874_2129289.jpeg)

### 4.9、系统异常
![](https://images.gitee.com/uploads/images/2020/0116/115530_b9fb8f87_2129289.jpeg)

### 4.10、G2图表
![](https://images.gitee.com/uploads/images/2020/0116/115530_a062fb8a_2129289.jpeg)


## 5、学习资源

- [Angular快速上手](https://angular.cn/guide/quickstart)
- [Ng-Zorro](https://ng.ant.design/docs/introduce/zh)
- [Ng-Alain](https://ng-alain.com/)
- [Spring系列-程序员DD](http://blog.didispace.com/)
- [Spring系列-纯洁的微笑](http://www.ityouknow.com/spring-boot.html)
- [Java8](https://zhuanlan.zhihu.com/java8)
- [lombok](https://www.jianshu.com/p/365ea41b3573)
- [SpringBoot 中 JPA 的使用](https://www.jianshu.com/p/c14640b63653)


## 开源许可证
MIT
