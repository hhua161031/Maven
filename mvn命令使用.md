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
\model\src\test\java\com\juvenxu\mvnbook\helloworld\ HelloWorldTest.java<br>

`注：src\main\java 和\src\test\java是maven项目约定的格式。`<br>
<br><br>

![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令1.png) 
<br>
**HelloWord.java**
```
package com.juvenxu.mvnbook.helloworld;

public class HelloWord {
	public String  sayHello(){
		return "Hello Maven";
	}
	public static void main(String[] args) {
		System.out.println(new HelloWord().sayHello());
	}

}

```
**HelloWorldTest.java**

```
package com.juvenxu.mvnbook.helloworld;

import org.junit.Test;

public class HelloWorldTest {
	@ Test
	public void testSayHello(){
		System.out.println("test hello world");
	}
	@ Test
	public void testSayHello2(){
		System.out.println("test hello world2");
	}
}

```
**Pom.xml**
```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.juvenxu.mvnbook</groupId>
	<artifactId>HelloWord</artifactId>
	<version>1.0-SNAPSHOT</version>
Mvn test:
用mvn进行单元测试
另外在pom文件中scope为test表示依赖项目仅仅参与测试相关的工作，包括测试代码的编译，执行。
	<name>Maven Hello World Project</name>

	<dependencies>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.10</version>
			<scope>test</scope>
		</dependency>
	</dependencies>
   <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-shade-plugin</artifactId>
                <version>1.2.1</version>
                <executions>
                    <execution>
                        <phase>package</phase>
                        <goals>
                            <goal>shade</goal>
                        </goals>
                        <configuration>
                            <transformers>
                                <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
                                    <mainClass>com.juvenxu.mvnbook.helloworld.HelloWord</mainClass>
                                </transformer>
                            </transformers>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>


</project>

```

`注：测试用的项目中的文件以及文件夹包括pom文件是需要按规定目录格式存放的。以便mvn命令能正确读到。即便用eclipse 创建的maven项目也是这样格式`<br>
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令2.png) 
<br>
#### Mvn Compile
类似使用ide对java项目进行编译成class文件<br>
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令3.png)
<br>
生成target目录
<br>
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令4.png) 
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令5.png) 

#### Mvn test
用mvn进行单元测试<br>
另外在pom文件中scope为test表示依赖项目仅仅参与测试相关的工作，包括测试代码的编译，执行。<br>
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令6.png)

#### Mvn package
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令7.png)
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令8.png)<br>
这里有两个包是因为在pom文件中加maven-shade-plugin ，其中一个jar包在MET INF中记录了可提供执行的main 方法路径。两个包的差别也仅此而已	
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令9.png)<br>
`注：maven-shade-plugin在pom中也有严格的位置规范，一般是project ->build ->plugins`
#### Mvn install
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令10.png)
![github](https://github.com/hhua161031/Maven/blob/master/img/mvn命令11.png)

