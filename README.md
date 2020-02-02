# Snails 框架
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/b_dashboard.jpg)

基于 [SpringBoot](https://spring.io/projects/spring-boot) + [Ng-Alain](https://ng-alain.com/) `前后端分离`的实现，可以作为新手入门项目，也可以作为小项目的`基础框架`去扩展。目前 [Snails](https://zhuanlan.zhihu.com/p/103187754) 系统框架已支持基本的后台功能，基于`简单`、`实用`设计，并且已支持 [Docker](https://www.docker.com/) 进行项目部署。

- `Snails 框架`：编程入门，新手礼赞
- `snails-web 前端`：[Angular](https://angular.cn/) + [Ng-Zorro](https://ng.ant.design/docs/introduce/zh) + [Ng-Alain](https://ng-alain.com)
- `snails-api 后台`：[SpringBoot](https://spring.io/projects/spring-boot) + [JPA ](https://spring.io/guides/gs/accessing-data-jpa/)+ [lombok](https://projectlombok.org/) + [Java8](https://zhuanlan.zhihu.com/java8) + Mysql

**基于国内访问速度考虑，建议使用 [码云](https://gitee.com/kuzan/snails) 进行访问 [https://gitee.com/kuzan/snails](https://gitee.com/kuzan/snails) **

|      `框架源码`     | Gitee                                                        | GitHub                                                       |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Snails** 框架      | [https://gitee.com/kuzan/snails](https://gitee.com/kuzan/snails) | [https://github.com/danxiaogui/snails](https://github.com/danxiaogui/snails) |
| **Snails-web** 前端  | [https://gitee.com/kuzan/snails-web](https://gitee.com/kuzan/snails-web) | [https://github.com/danxiaogui/snails-web](https://github.com/danxiaogui/snails-web) |
| **Snails-api**  后台 | [https://gitee.com/kuzan/snails-api](https://gitee.com/kuzan/snails-api) | [https://github.com/danxiaogui/snails-api](https://github.com/danxiaogui/snails-api) |

欢迎到 `Gitee` 或者 `GitHub` 上提 `issue`

| `issue 渠道` | 访问地址                                                     |
| ------------ | ------------------------------------------------------------ |
| **Gitee**    | [https://gitee.com/kuzan/snails/issues](https://gitee.com/kuzan/snails/issues) |
| **GitHub**   | [https://github.com/danxiaogui/snails/issues](https://github.com/danxiaogui/snails/issues) |


## 1、系统功能

* [x]  登陆、登出
* [x]  用户管理
* [x]  组织管理
* [x]  菜单管理，支持菜单配置、菜单权限配置、用户菜单权限预览功能
* [x]  在线用户
* [x]  登陆日志，记录系统用户的登陆登出行为
* [x]  http请求，将系统的所有请求进行拦截，并记录到数据库中
* [x]  系统异常，全局拦截系统的异常，并记录到数据库中
* [x]  支持系统数据初始化
* [x]  支持 `Docker` 部署



## 2、启动系统前提 `Mysql`

Mysql 配置文件地址：`/snails-api/src/main/resources/application.yml`

| IP        | Port | Username | Password | Database |
| --------- | ---- | -------- | -------- | -------- |
| localhost | 3306 | root     | 123456   | snails   |



## 3、启动系统 

### 3.1、方法一 `Docker`

前提：系统已安装和配置 `Java8`、`Git`、`Maven`、`Docker`

```shell
# 1、打包 snails-web 镜像
git clone https://gitee.com/kuzan/snails-web.git
cd snails-web
docker build -t snails-web .

# 2、打包 snails-api 镜像
git clone https://gitee.com/kuzan/snails-api.git
cd snails-api
# 根据步骤 2 所示，修改代码中的 Mysql 配置 /snails-api/src/main/resources/application.yml
# 使用部署系统中 Docker 的 Mysql 作为数据库连接可能导致启动报错
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
### 3.2、方法二

前提：系统已安装和配置 `Java8`、`Git`、`Maven`、`Node`

```shell
# 1、运行 snails-web
git clone https://gitee.com/kuzan/snails-web.git
cd snails-web
yarn
npm run start

# 2、运行 snails-api
git clone https://gitee.com/kuzan/snails-api.git
cd snails-api
# 根据步骤 2 所示，修改代码中的 Mysql 配置 /snails-api/src/main/resources/application.yml
mvn package
java -jar target/snails-0.1.jar

# 3、浏览器访问 localhost:4200 即可
```



## 4、系统截图 
> 浏览器访问 localhost:4200

### 4.1、登陆页面

>  系统默认用户、账号、密码信息，数据在 **snails-api** 启动后初始化到数据库中，源码在 snails-api/src/main/java/com/kuzank/snails/init/InitPerson.java

| 用户名     | 账号       | 密码   | 备注                             |
| ---------- | ---------- | ------ | -------------------------------- |
| kuzank     | kuzank     | 123456 | 所属组织：Snails Studio > 技术部 |
| danxiaogui | danxiaogui | 123456 | 所属组织：Snails Studio > 财务部 |

![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/a_login.jpg)

### 4.2、首页
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/b_dashboard.jpg)

### 4.3、用户管理
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/b_dashboard.jpg)

### 4.4、组织管理
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/d_orgunitManage.jpg)

### 4.5、菜单管理
> 菜单配置及菜单权限配置

![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/e_menuManage.jpg)

> 用户菜单权限预览

![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/f_menuPermissionPreview.jpg)

### 4.6、在线用户
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/g_onlineUser.jpg)

### 5.7、登陆日志
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/h_loginLog.jpg)

### 4.8、http请求
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/i_httpRequest.jpg)

### 4.9、系统异常
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/j_systemException.jpg)

### 4.10、G2图表
![](https://gitee.com/kuzan/Resource/raw/master/Snails/picture/k_g2Custom.jpg)


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
