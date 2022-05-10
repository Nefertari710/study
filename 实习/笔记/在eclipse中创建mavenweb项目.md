1. 创建一个maven工程![](../图片资源/在eclipse中创建mavenweb项目图片资源/P1.png)
2. 直接下一步![](../图片资源/在eclipse中创建mavenweb项目图片资源/P2.png)
3. 类型选择 maven-archetype-webapp![](../图片资源/在eclipse中创建mavenweb项目图片资源/P3.png)
4. 填写好上面的两项，最下面的包名随意![](../图片资源/在eclipse中创建mavenweb项目图片资源/P4.png)
5. 解决默认jdk版本问题--修改配置文件
	- 我们可以把一些没有关的东西删除掉
	- 修改内容
	```xml
	<build>
		<plugins>
			<plugin>
				  <groupId>org.apache.maven.plugins</groupId>
				  <artifactId>maven-compiler-plugin</artifactId>
				  <version>3.8.1</version>
				  <configuration>
					<source>1.8</source>
					<target>1.8</target>
				  </configuration>
			</plugin>
		</plugins>
	</build>
	```
	- 修改后的效果![](../图片资源/在eclipse中创建mavenweb项目图片资源/P5.png)
	- 更新一下项目![](../图片资源/在eclipse中创建mavenweb项目图片资源/P6.png)
	- 更新一下项目![](../图片资源/在eclipse中创建mavenweb项目图片资源/P7.png)
	- 更新后效果![](../图片资源/在eclipse中创建mavenweb项目图片资源/P8.png)
6. 解决看不到src/main/java 和 src/test/java 目录的问题
	- 我们的方式是通过移除jdk的方式
	- 步骤一：![](../图片资源/在eclipse中创建mavenweb项目图片资源/P9.png)
	- 步骤二:选中并移除![](../图片资源/在eclipse中创建mavenweb项目图片资源/P10.png)
	- 步骤三:选择Add Library![](../图片资源/在eclipse中创建mavenweb项目图片资源/P11.png)
	- 步骤四:选择JRE![](../图片资源/在eclipse中创建mavenweb项目图片资源/P12.png)
	- 步骤五:选择版本![](../图片资源/在eclipse中创建mavenweb项目图片资源/P13.png)
	- 最终效果![](../图片资源/在eclipse中创建mavenweb项目图片资源/P14.png)
7. 解决创建maven项目时生成的jsp有红叉问题
	- 问题![](../图片资源/在eclipse中创建mavenweb项目图片资源/P15.png)
	- 原因:因为没有引入javaee相关的依赖
	- 解决方法:手动把相关的依赖引入
	- 引入关于servlet的支持
	```xml
	<dependency>
		<groupId>javax.servlet</groupId>
		<artifactId>javax.servlet-api</artifactId>
		<version>3.1.0</version>
		<scope>provided</scope>
	</dependency>
	```
	- 引入JSP的支持
	```xml
	<dependency>
		<groupId>javax.servlet.jsp</groupId>
		<artifactId>javax.servlet.jsp-api</artifactId>
		<version>2.3.1</version>
	</dependency>
	```
	- 引入JSTL 的支持
	```xml
	<dependency>
		<groupId>javax.servlet</groupId>
		<artifactId>jstl</artifactId>
		<version>1.1.2</version>
	</dependency>
	<dependency>
		<groupId>taglibs</groupId>
		<artifactId>standard</artifactId>
		<version>1.1.2</version>
	</dependency>
	```
	- 全部引入后依赖效果![](../图片资源/在eclipse中创建mavenweb项目图片资源/P16.png)
	- 可以看到依赖已经全部导入了![](../图片资源/在eclipse中创建mavenweb项目图片资源/P17.png)
	- 最终效果--红叉消失![](../图片资源/在eclipse中创建mavenweb项目图片资源/P18.png)
8. 在index.jsp中写入el表达式,发现它不能解析
	- 问题![](../图片资源/在eclipse中创建mavenweb项目图片资源/P19.png)
	- 原因:原有的web.xml内容太古老了
	- 需要替换的代码
	```xml
	<?xml version="1.0" encoding="UTF-8"?>
	<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns="http://xmlns.jcp.org/xml/ns/javaee" 
		xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" id="WebApp_ID" version="3.1">
	</web-app>
	```
	- 替换后效果![](../图片资源/在eclipse中创建mavenweb项目图片资源/P20.png)
	- 最后效果![](../图片资源/在eclipse中创建mavenweb项目图片资源/P21.png)
9. 如果有必要就修改一下
	- 首先我们需要先看到系统隐藏起来的资源文件--对于资源文件前面的那个框取消勾选![](../图片资源/在eclipse中创建mavenweb项目图片资源/P22.png)
	- 执行后资源文件就会出现![](../图片资源/在eclipse中创建mavenweb项目图片资源/P23.png)
	- 对.setting中的这一文件进行修改![](../图片资源/在eclipse中创建mavenweb项目图片资源/P24.png)
	- 修改成和web.xml中版本相同![](../图片资源/在eclipse中创建mavenweb项目图片资源/P25.png)