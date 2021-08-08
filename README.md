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

