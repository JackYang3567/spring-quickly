## 简介

## 0、STS

Spring Tool Suite 简称 STS,  是Spring开发所用的IDE, 有以下三种类型。

* Spring Tools 4 for Eclipse
* Spring Tools 4 for Visual Studio Code
* Spring Tools 4 for Theia

## 1、SpringTool Suite4 for Eclipse

### 1.1、如何设置 代码自动提示

由于 STS / Eclipse 的代码自动提醒是关闭的，只有在输入 . 的时候才会有代码的提醒。这对于经常使用其他 IDE 自动提醒的人很不友好（IDEA 和 VSCode 都是默认输入任何字符都会自动提醒）

Eclipse 需要设置后才可代码自动提醒

##### 解决方案

首先打开Eclipse, 在顶部菜单栏点击Window-&gt; Preferences ，

弹出窗口，然后选择 Java / Editor / Content Assist

将其中的 Auto activation triggers for Java 后面的 . 替换为 abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ.

替换完成后点击 `Apply`之后就可以通过输入任何字母来实现代码自动提醒

## 2、Spring Boot + Swagger2 自动生成api接口文档

### 2.1、什么是Swagger

**swagger**就是一个在你开发编写接口的时候自动帮你生成接口文档的东西，只要你遵循它的规范并写一些接口的说明注解即可。

* 自动生成文档，只需要在接口中使用注解进行标注，就能生成对应的接口文档。
* 自动更新文档，由于是动态生成的，所以如果你修改了接口，文档也会自动对应修改（如果你也更新了注解的话）。这样就不会发送我修改了接口，却忘记更新接口文档的情况。
* 支持在线调试，swagger提供了在线调用接口的功能。

由于存在多终端的情况（移动端，web前端，小程序等），所以会用Spring Boo来构建RESTful API

### 2.2、在SpringBoot中使用Swagger



