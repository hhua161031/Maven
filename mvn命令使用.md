mvn命令使用
============
### 开篇
从maven 实战这本书里面将maven 定义为项目构建工具，具体讲是能将项目编译、测试、打包等集成一身，是一个强大工具。
以前用maven只是用到它的对第三方类库的管理功能，对它的认识也不是很全面。通过maven手动对项目进行构建,加强对maven发的认识。
<br>
#### 准备：<br>
apache-maven-3.5.0

#### 命令介绍：

命令            | 解释
--------       | ---
Mvn compile    | 编译
Mvn clean      | 清空target目录
Mvn package    | 打包
Mvn test       | 运行单元测试
Mvn install    | 把当前目录下的程序达成jar包放入本地库供另一个程序调用


*使用上述命令要在项目的根目录下执行。如model ，这样maven会在根目录生成target 目录存放编译好项目以及打好的包。*

Compile<test<package<install  <br>
Install 命令执行会把前面的几条命令都执行，在打印信息也可以看出。依次类推。
<br>
<br>
Mvn 命令可以多条组合执行<br>
Mvn clean compile 先清除后编译
### 测试项目：
\model\src\main\java\com\juvenxu\mvnbook\helloworld\ HelloWord.java<br>
\model\src\test\java\com\juvenxu\mvnbook\helloworld\ HelloWorldTest.java
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令1.png) 


