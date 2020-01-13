---
layout: post
title:  "Java的包管理与Maven"
date:   2020-01-13 12:43:33
categories: Java Maven
excerpt: Java的包管理与Maven
---

* content
{:toc}

# 什么是包？

JVM的工作被设计的相当简单：
* 执行一个类的字节码
* 假如这个过程中碰到了新类，加载它

那么去哪加载这些类呢？可以通过Classpath来寻找这些类，如果是目录，就直接找，如果是jar文件，就把文件解压缩然后再找。

> 类的全限定类名（目录层级）唯一确定了一个类

那么这些jar包就是一堆类的集合，是把许多类放在一起打的压缩包

# 什么是包管理？

> 你要使用一些第三方类，需要告诉JVM去哪里找

包管理的本质就是告诉JVM如何找到所需的第三方类库，以及成功的解决其中的冲突问题。

# Maven

> 在没有Maven的年代，需要手动写命令编译运行。后来有了Apache Ant。

Maven是一个包管理工具和自动化构建工具，它的一个原则是：Convention over configuration（约定优于配置）。

如果你需要使用一个第三方类库，那么需要在`pom.xml`加入该依赖，这样就能自动从Maven中央仓库下载。

Maven有一套中央仓库，按照一定的约定把这些包存储起来。除了中央仓库，Maven的本地仓库默认位于`~/.m2`，默认从中央仓库下载缓存到这个目录。

Maven对包进行了抽象，对所有的包添加了3个属性：`groupId`、`artifaactId`和`version`，可以根据这个规则去找对应的包。

> 语义化版本 2.0.0：https://semver.org/lang/zh-CN/

# 包冲突

Maven自动解决了传递性依赖。

比如当项目所引用的库的传递性依赖库有相同时，就会发生包冲突。

包冲突的表现有：
* AbstractMethodError
* NotClassDefError
* ClassNotFoundException
* LinkageError

Maven对传递性依赖的自动管理有个原则：
* 绝对不允许最终的classpath出现同名不同版本的jar包

那么对于上面举的例子，就需要删除一个包，

对于包冲突，Maven的解决原则是：
* 离项目最近的包胜出

> 推荐一个IDEA插件：Maven Helper，可以帮助你解决包冲突

# Maven依赖scope

指定依赖只在某个地方有效，比如只在test中。

常见的scope有：
* `<scope>compile</scope>`
* `<scope>test</scope>`

# 2个pom.xml例子

https://github.com/alibaba/fastjson/blob/master/pom.xml

https://github.com/google/guava/blob/master/pom.xml