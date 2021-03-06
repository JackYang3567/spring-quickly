# 简介

**查找域名所对应的 IP 地址**

打开[https://www.ipaddress.com/](https://www.ipaddress.com/)

## 0、STS

Spring Tool Suite 简称 STS,  是Spring开发所用的IDE, 有以下三种类型。

* Spring Tools 4 for Eclipse
* Spring Tools 4 for Visual Studio Code
* Spring Tools 4 for Theia

### 0.1、SpringBoot集成H2Database

H2是一个用Java开发的嵌入式数据库

使用 H2 控制台（Spring Boot DevTools 在 [localhost:8080/h2-console](http://localhost:8080/h2-console) 启用）连接到数据库

设置几个属性来确定数据库名称是个好主意 `application.yml：`

```
spring:
  datasource:
    generate-unique-name: false
    name: tacocloud
```

[http://localhost:8080/h2-console/](http://localhost:8080/h2-console/)

[`JDBC URL`](http://localhost:8080/h2-console/login.jsp?jsessionid=754dc67e7db7f39a75c33c21e1803444#)`: jdbc:h2:mem:tacocloud`

#### 0.1.1、配置 MySQL

##### 1、pom.xml文件中增加依赖：

```
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```

##### 2、在application.properties中加入配置

```
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/tacocloud
spring.datasource.username=root
spring.datasource.password=123456
```

##### 3、Mysql创建数据库并设置字符集编码

    create database `tacocloud` character set utf8 collate utf8_general_ci;

4、在数据库中，新建一张表，放入一丢丢的数据（注意：设计表时，要改表的字符集，排序规则，否则乱码）

    DROP TABLE IF EXISTS `users`;
    CREATE TABLE `users` (
      `id` int NOT NULL AUTO_INCREMENT,
      `username` varchar(50) NOT NULL DEFAULT '' COMMENT '管理员名',
      `password` varchar(256) NOT NULL DEFAULT '' COMMENT '密码',
      `fullname` varchar(256) NOT NULL DEFAULT '' COMMENT '姓名',
      `email` varchar(50) DEFAULT NULL COMMENT '邮箱',
      `status` int NOT NULL DEFAULT '0' COMMENT '状态',
      PRIMARY KEY (`id`)
    ) ENGINE=InnoDB AUTO_INCREMENT=0 DEFAULT CHARSET=UTF8MB4 COMMENT='用户表';



    INSERT INTO `users`
    (`id`,`username`,`password`,
    `fullname`,`email`,`status`)
    VALUES
    ('0','user','$2a$10$FnoSppxTFWMH0y/yY1b.DeNYbWROJI83pC7wLbiS3l2qhjFhf1HYC',
    'Jack Yang','user@163.com','0');

##### 5、在项目中DemoApplication启动类中增加以下代码

### 0.2、安装Spring Boot CLI

## 1、SpringTool Suite4 for Eclipse

### 1.0、安装lombok

#### 1.0.1、lombok简介

lombok是一个可以通过简单的注解的形式来帮助我们简化 Java 代码

#### 1.0.2、lombok安装

下载lombok插件：[https://www.projectlombok.org/download](https://www.projectlombok.org/download)![](assets/images/lombok-download.png)![](assets/images/lombok-path.png)

cmd窗口运行命令:

```
C:\Users\86138>d:

D:\>cd D:\vswork\Tools\java

D:\vswork\Tools\java>java -jar lombok.jar
```

##### ![](/assets/images/lombok-select.png)![](/assets/lombok-install.png)

##### 查看D:\Program Files \(x86\)\sts-4.11.1.RELEASE\SpringToolSuite4.ini

,出现如下表示成功，然后重启IDE：

![](/assets/lombok-end.png)

### 1.1、如何设置 代码自动提示

由于 STS / Eclipse 的代码自动提醒是关闭的，只有在输入 . 的时候才会有代码的提醒。这对于经常使用其他 IDE 自动提醒的人很不友好（IDEA 和 VSCode 都是默认输入任何字符都会自动提醒）

Eclipse 需要设置后才可代码自动提醒

##### 解决方案

首先打开Eclipse, 在顶部菜单栏点击Window-&gt; Preferences ，

弹出窗口，然后选择 Java / Editor / Content Assist

将其中的 Auto activation triggers for Java 后面的 . 替换为 abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ.

替换完成后点击 `Apply`之后就可以通过输入任何字母来实现代码自动提醒

### 1.2、在eclipse中打开命令行窗口

##### window-&gt;show view-&gt;Terminal 然后 按 组合键 \[Ctr\] + \[Alt\] + \[Shift\] + \[T\] 在弹窗中选择 Local Terminal

### 1.3、console buffer size too low

Eclipse 设置console显示更多的输出内容：

> Windows &gt; Perferences &gt; Run/Debug &gt; Console
>
> 里面有个Console buffer size\(characters\)
>
> 默认数值只有80000
>
> 我们可以设置到1000000

## 2、Spring Boot + Swagger2 自动生成api接口文档

### 2.1、什么是Swagger

**swagger**就是一个在你开发编写接口的时候自动帮你生成接口文档的东西，只要你遵循它的规范并写一些接口的说明注解即可。

* 自动生成文档，只需要在接口中使用注解进行标注，就能生成对应的接口文档。
* 自动更新文档，由于是动态生成的，所以如果你修改了接口，文档也会自动对应修改（如果你也更新了注解的话）。这样就不会发送我修改了接口，却忘记更新接口文档的情况。
* 支持在线调试，swagger提供了在线调用接口的功能。

由于存在多终端的情况（移动端，web前端，小程序等），所以会用Spring Boo来构建RESTful API

### 2.2、在SpringBoot中使用Swagger

#### 2.2.1、 在pom中添加swagger的依赖

在项目的pom.xml中添加swagger依赖，添加的依赖主要有两个，分别是swagger和swagger-ui

```
<!--swagger  begging-->
   <dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-boot-starter</artifactId>
    <version>3.0.0</version>
</dependency>
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>3.0.0</version>
</dependency>
<!--swagger  end-->
```

#### 2.2.2、 添加swagger配置类

在项目中创建SwaggerConfig.java类

```
package tacos;

import org.springframework.context.annotation.Bean; 
import org.springframework.context.annotation.Configuration;
import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

/**
 * @Description: swagger 配置类
 * @Author Jack Yang
 * @Date 2021/08/10 3:39 下午
 */

@Configuration  // 标明是配置类
@EnableSwagger2 //开启swagger功能
public class SwaggerConfig {

     @Bean
     public Docket createRestApi() {
           // 指定扫描包路径
            return new Docket(DocumentationType.SWAGGER_2)  // 指定生成的文档的类型是Swagger2
                 // .groupName("分布式任务系统") // 如果配置多个文档的时候，那么需要配置groupName来分组标识
                    .apiInfo(apiInfo()) // 用于生成API信息
                    .select() // select()函数返回一个ApiSelectorBuilder实例,用来控制接口被swagger做成文档
                    // 用于指定扫描哪个包下的接口
                    .apis(RequestHandlerSelectors.basePackage("tacos")) 
                    // 选择所有的API,如果你想只为部分API生成文档，可以配置这里
                    .paths(PathSelectors.any()) 
                    .build();
        }

        /**
         * 用于定义API主界面的信息，比如可以声明所有的API的总标题、描述、版本
         * @return
         */
        private ApiInfo apiInfo() {
            return new ApiInfoBuilder()
                    // 设置标题
                    .title("XXXX服务") 
                     // 描述
                    .description("XXXX服务应用接口API") 
                     // 用于定义服务的域名
                    .termsOfServiceUrl("")                     
                    // 可以用来定义版本。
                    .version("Version: 1.0.1")                      
                    .build(); //
        }

}
```

> * @Configuration 配置类，启动时加载此类
> * @EnabledSwagger2 标识项目启动 SwaggerApi 文档
> * ApiInfo 这个类时Swagger 页面展示的一些基础信息
> * RequestHandlerSelectors.basePackage\("tacos“\) 这里的tacos是扫描包的路径
> * 输入访问路径 /swagger-ui/index.html



