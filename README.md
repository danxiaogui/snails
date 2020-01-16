<h1 align="center"><a href="https://gitee.com/kuzan/snails">snails</a></h1>
一个基于 Spring-Boot + Angular + Ng-Zorro 前后端分离项目的简单实现


- [snails 框架](https://gitee.com/kuzan/snails)：编程入门，新手礼赞
- [snails-web 前端](https://gitee.com/kuzan/snails-web)：Angular + Ng-Zorro + Ng-Alain
- [snails-api 后台](https://gitee.com/kuzan/snails-api)：Spring-Boot + JPA + lombok + Java8 + Mysql


## Further
* [ ]  首页设计
* [ ]  菜单支持权限配置和控制


## 系统功能
* [x]  登陆、登出
* [x]  用户管理
* [x]  组织管理
* [x]  菜单管理，支持菜单动态配置
* [x]  在线用户
* [x]  登陆日志，记录系统用户的登陆登出行为
* [x]  http请求，将系统的所有请求进行拦截，并记录到数据库中
* [x]  系统异常，全局拦截系统的异常，并记录到数据库中
* [x]  支持系统数据初始化
* [x]  支持 Http Api 权限控制
* [x]  [snails-api 后台](https://gitee.com/kuzan/snails-api) 支持 Docker 部署
* [x]  [snails-web 前端](https://gitee.com/kuzan/snails-web) 支持 Docker 部署


## 系统搭建过程
- [1、简介](https://gitee.com/kuzan/snails-api/blob/master/document/introduction/a%E7%AE%80%E4%BB%8B.md)
- [2、创建工程项目](https://gitee.com/kuzan/snails-api/blob/master/document/introduction/b%E5%88%9B%E5%BB%BA%E5%B7%A5%E7%A8%8B%E9%A1%B9%E7%9B%AE.md)
- [3、JPA使用](https://gitee.com/kuzan/snails-api/blob/master/document/introduction/cJPA%E4%BD%BF%E7%94%A8.md)
- [4、权限拦截器](https://gitee.com/kuzan/snails-api/blob/master/document/introduction/d%E6%9D%83%E9%99%90%E6%8B%A6%E6%88%AA%E5%99%A8.md)


## 开发环境要求
- Java 8
- Maven
- Mysql
- Node


## 启动系统前提
[需要有一个 Mysql 数据库](https://gitee.com/kuzan/snails-api/blob/master/src/main/resources/application.yml)
* ip: localhost
* port: 3306
* username: root
* password: 123456
* database: snails


## 启动系统 - 方法1 【docker】
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

## 启动系统 - 方法2 【Linux or MacBook】
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


## 系统运行截图
### 登陆页面
![](https://images.gitee.com/uploads/images/2020/0116/115529_4c6de3e2_2129289.jpeg)

### 首页
![](https://images.gitee.com/uploads/images/2020/0116/115529_1495144d_2129289.jpeg)

### 用户管理
![](https://images.gitee.com/uploads/images/2020/0116/115529_c0fc1cb6_2129289.jpeg)

### 组织管理
![](https://images.gitee.com/uploads/images/2020/0116/115530_d4588fb6_2129289.jpeg)

### 菜单管理
![](https://images.gitee.com/uploads/images/2020/0116/115530_b7cd92de_2129289.jpeg)

### 在线用户
![](https://images.gitee.com/uploads/images/2020/0116/115530_8f3b0019_2129289.jpeg)

### 登陆日志
![](https://images.gitee.com/uploads/images/2020/0116/115530_32bf531e_2129289.jpeg)

### http请求
![](https://images.gitee.com/uploads/images/2020/0116/115530_bfaa1874_2129289.jpeg)

### 系统异常
![](https://images.gitee.com/uploads/images/2020/0116/115530_b9fb8f87_2129289.jpeg)

### G2图表
![](https://images.gitee.com/uploads/images/2020/0116/115530_a062fb8a_2129289.jpeg)


## 学习资源
- [Angular快速上手](https://angular.cn/guide/quickstart)
- [Ng-Zorro](https://ng.ant.design/docs/introduce/zh)
- [Ng-Alain](https://ng-alain.com/)
- [Spring系列-程序员DD](http://blog.didispace.com/)
- [Spring系列-纯洁的微笑](http://www.ityouknow.com/spring-boot.html)
- [Java8](https://zhuanlan.zhihu.com/java8)
- [lombok](https://www.jianshu.com/p/365ea41b3573)
- [SpringBoot 中 JPA 的使用](https://www.jianshu.com/p/c14640b63653)
