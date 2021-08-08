# 1、Spring 入门

Spring开发面向云的由微服务组成的应用，其关注点是反应式编程，致力于通过非阻塞操作提供更好的扩展性并提升性能。

任何重要的应用程序都由许多组件组成，每个组件负责整个应用程序功能的一部分，并与其他应用程序元素协调以完成工作。

## 1.1、什么是Spring

任何重要的应用程序都由许多组件组成，每个组件负责整个应用程序功能的一部分，并与其他应用程序元素协调以完成工作。

当应用程序运行时，这些组件需要以某种方式被创建并相互引入。

在其核心，Spring 提供了一个容器，通常称为Spring 应用程序上下文，用于创建和管理应用程序组件。

这些组件（或beans）在 Spring 应用程序上下文中连接在一起以构成一个完整的应用程序，就像砖、灰浆、

木材、钉子、管道和布线捆绑在一起构成一个房子一样。

将 bean 连接在一起的行为称为 依赖注入（DI）。与其让组件创建和维护它们所依赖的其他 bean 的生命周期，

依赖注入的应用程序依赖于一个单独的实体（容器）来创建和维护所有组件，并将它们注入到需要它们的 bean 中。

这通常通过构造函数参数或属性访问器方法完成。

例如，假设在一个应用程序的众多组件中，您将处理两个组件：库存服务（用于获取库存水平）和产品服务

（用于提供基本产品信息）。产品服务依赖于库存服务能够提供关于产品的完整信息集。

##### 1.1、应用程序组件由 Spring 应用程序上下文管理并相互注入 {#d5e35}

![](https://drek4537l1klr.cloudfront.net/walls8/v-6/Figures/1-1.png)

Spring Tool Suite的官方下载地址是：

[https://spring.io/tools](https://spring.io/tools)

## 1.2 初始化一个 Spring 应用程序

### 1.2.1 使用 Spring Tool Suite 初始化 Spring 项目

到在 Spring Tool Suite 中开始一个新的 Spring 项目，转到 File 菜单并选择 New，然后选择 Spring Starter Project。图 1.2 显示了要查找的菜单结构。

##### 图 1.2。使用 Spring Tool Suite 中的 Initializr 启动一个新项目![](https://drek4537l1klr.cloudfront.net/walls8/v-6/Figures/1-2.png)

##### 图 1.2.1。使用 Spring Tool Suite 中的 Initializr 启动一个新项目\(for Eclipse in Windows 10\)![](/assets/1-2-1.png)

选择 Spring Starter Project 后，将出现一个新项目向导对话框（图 1.3）。

向导的第一页要求您提供一些常规项目信息，例如项目名称、描述和其他基本信息。

如果您熟悉 Maven pom.xml 文件的内容，您就会将大多数字段识别为最终出现在 Maven 构建规范中的项目。

对于 Taco Cloud 应用程序，填写如图 1.3 所示的对话框，然后单击 Next。

##### 图 1.3。为 Taco Cloud 应用程序指定常规项目信息![](https://drek4537l1klr.cloudfront.net/walls8/v-6/Figures/1-3.png) {#d5e120}

##### 图 1.3.1  为 Taco Cloud 应用程序指定常规项目信息\(for Eclipse in Windows 10\) {#d5e120}

![](/assets/1-3-1.png)

向导的下一页让您选择要添加到项目中的依赖项（见图 1.4）。请注意，在对话框顶部附近，您可以选择要作为项目基础的 Spring Boot 版本。这默认为可用的最新版本。除非您需要针对不同的版本，否则保持原样通常是个好主意。

至于依赖项本身，您可以展开各个部分并手动查找所需的依赖项，也可以在可用列表顶部的搜索框中搜索它们。对于 Taco Cloud 应用程序，您将从图 1.4 中显示的依赖项开始。

##### 图 1.4。选择启动依赖项![](https://drek4537l1klr.cloudfront.net/walls8/v-6/Figures/1-4.png) {#d5e129}

##### 图 1.4.1。选择启动依赖项\(for Eclipse in Windows 10\) {#d5e129}

![](/assets/1-4.-1png.png)

此时，您可以单击完成以生成项目并将其添加到您的工作区。

但是，如果您有点冒险，可以再单击一次 Next 以查看新建启动项目向导的最后一页，如图 1.5 所示。

##### 图 1.5。（可选）指定备用 Initializr 地址![](https://drek4537l1klr.cloudfront.net/walls8/v-6/Figures/1-5.png) {#d5e137}

##### 图 1.5.1。（可选）指定备用 Initializr 地址\(for Eclipse in Windows 10\) {#d5e137}

![](/assets/1-5-1.png)

默认情况下，新建项目向导会调用[start.spring.io 中](http://start.spring.io/)的 Spring Initializr来生成项目。通常，不需要覆盖此默认值，这就是您可以在向导的第二页上单击“完成”的原因。但是，如果由于某种原因您要托管您自己的 Initializr 克隆（可能是您自己机器上的本地副本或在您公司防火墙内运行的自定义克隆），那么您需要更改 Base Url 字段以指向您的 Initializr单击完成之前的实例。

单击完成后，项目将从 Initializr 下载并加载到您的工作区中。等待它加载和构建，然后您就可以开始开发应用程序功能了。但首先，让我们看看 Initializr 给出了什么你。

### 1.2.2 检查 Spring 项目结构 {#sigil_toc_id_2}



##### 图 1.6。初始 Spring 项目结构如 Spring Tool Suite 所示![](https://drek4537l1klr.cloudfront.net/walls8/v-6/Figures/1-6.png)



