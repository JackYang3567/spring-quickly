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

在历史上，引导Spring应用上下文将bean装配在一起的方式是使用一个或多个XML文件（描述各个组件以及它们与其他组件的关联关系）

例如，以下 XML 声明了两个 bean，一个 InventoryServicebean 和一个ProductServicebean，并通过构造函数参数将InventoryServicebean 连接到ProductService其中：

```
<bean id="inventoryService"
      class="com.example.InventoryService" />

<bean id="productService"
      class="com.example.ProductService" />
  <constructor-arg ref="inventoryService" />
</bean>
```

然而，在 Spring 的最新版本中，基于 Java 的配置更为常见。以下基于 Java 的配置类等价于 XML 配置：

```
@Configuration
public class ServiceConfiguration {
  @Bean
  public InventoryService inventoryService() {
    return new InventoryService();
  }

  @Bean
  public ProductService productService() {
    return new ProductService(inventoryService());
  }
}
```

该@Configuration注解向 Spring 表明这是一个配置类，它将向 Spring 应用程序上下文提供 bean。配置的类方法使用@Bean注解进行标注，表示它们返回的对象应该作为 bean 添加到应用程序上下文中（默认情况下，它们各自的 bean ID 将与定义它们的方法的名称相同）。



* ##### Spring Boot 是 Spring框架的扩展，提供了很多增强生产效率的方法。
* ##### Spring Boot 大幅度减少了构建应用程序所需的显式配置的数量
* ##### Spring Boot 极大改善了 Spring 开发



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

### 1.2.2 检查 Spring 项目结构

项目在 IDE 中加载后，展开它以查看它包含的内容。图 1.6 显示了 Spring Tool Suite 中扩展的 Taco Cloud 项目。

##### 图 1.6。初始 Spring 项目结构如 Spring Tool Suite 所示![](https://drek4537l1klr.cloudfront.net/walls8/v-6/Figures/1-6.png)

您可能会认为这是典型的 Maven 或 Gradle 项目结构，其中应用程序源代码放在 src/main/java 下，测试代码放在 src/test/java 下，非 Java 资源放在 src/main/resources 下. 在该项目结构中，您需要注意以下项目：

* `mvnw`和`mvnw.cmd`——这些是 Maven包装脚本。即使您的机器上没有安装 Maven，您也可以使用这些脚本来构建您的项目。
* pom.xml — 这是 Maven 构建规范。我们稍后会更深入地研究这一点。
* `TacoCloudApplication.java`——这是引导项目的 Spring Boot 主类。稍后我们将仔细研究这个类。
* application.properties — 该文件最初是空的，但提供了一个可以指定配置属性的地方。我们将在本章中稍微修改这个文件，但我会将配置属性的详细解释推迟到第 5 章。
* static — 您可以在此文件夹中放置要提供给浏览器的任何静态内容（图像、样式表、JavaScript 等）。它最初是空的。
* 模板 — 您将在此文件夹中放置将用于向浏览器呈现内容的模板文件。它最初是空的，但您很快就会添加一个 Thymeleaf 模板。
* `TacoCloudApplicationTests.java`— 这是一个简单的测试类，可确保 Spring 应用程序上下文加载成功。在开发应用程序时，您将向组合中添加更多测试。

#### 探索构建规范

什么时候您填写了 Initializr 表单，并指定您的项目应使用 Maven 构建。因此，Spring Initializr 为您提供了一个 pom.xml 文件，其中已经填充了您所做的选择。以下清单显示了 Initializr 提供的整个 pom.xml 文件。

##### 清单 1.1。最初的 Maven 构建规范

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
        https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.4.0</version>
    <relativePath />
  </parent>
  <groupId>sia</groupId>
  <artifactId>taco-cloud</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <name>taco-cloud</name>
  <description>Taco Cloud Example</description>

  <properties>
    <java.version>11</java.version>
  </properties>

  <dependencies>
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>

    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-devtools</artifactId>
      <scope>runtime</scope>
      <optional>true</optional>
    </dependency>

    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-test</artifactId>
      <scope>test</scope>
      <exclusions>
        <exclusion>
          <groupId>org.junit.vintage</groupId>
          <artifactId>junit-vintage-engine</artifactId>
        </exclusion>
      </exclusions>
    </dependency>

  </dependencies>

  <build>
    <plugins>
      <plugin>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-maven-plugin</artifactId>
      </plugin>
    </plugins>
  </build>

  <repositories>
    <repository>
      <id>spring-milestones</id>
      <name>Spring Milestones</name>
      <url>https://repo.spring.io/milestone</url>
    </repository>
  </repositories>
  <pluginRepositories>
    <pluginRepository>
      <id>spring-milestones</id>
      <name>Spring Milestones</name>
      <url>https://repo.spring.io/milestone</url>
    </pluginRepository>
  </pluginRepositories>

</project>
```



