Maven installs Jar file into dependencies and usit
==================================

[Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

[Using Maven makes Jar file with dependencies](https://github.com/lucasko-tw/maven-jar-with-dependencies)


### 
![arch.png](https://github.com/lucasko-tw/maven-install-jar-into-dependencies/blob/master/arch.png)
The goal is to install jar into dependencies and use it.



### Install jar into dependencies from tutorial-maven-utils/

edit the pom.xml

```XML
<groupId>org.lucasko</groupId>
<artifactId>tutorial-maven-utils</artifactId>
<version>1.0.0</version>
<packaging>jar</packaging>

<properties>
	<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
</properties>

<build>
	<finalName>${project.artifactId}</finalName> 
</build>
```


compile: compile the source code of the project
 
```sh
 mvn compile
```

install: install: install the package into the local repository, for use as a dependency in other projects locally

```sh
 mvn install
```

1. The jar is created in  /home/{username}/Downloads/tutorial-maven-utils/pom.xml to /home/{username}/.m2/repository/org/lucasko/tutorial-maven-utils/1.0.0/tutorial-maven-utils-1.0.0.pom

2. For now, you can use this dependency from local respository.




### Using new dependency from tutorial-maven-jar/

Import dependency into project.

```xml
	<dependencies>

		<dependency>
			<groupId>log4j</groupId>
			<artifactId>log4j</artifactId>
			<version>1.2.17</version>
		</dependency>

		<dependency>
			<groupId>org.lucasko</groupId>
			<artifactId>tutorial-maven-utils</artifactId>
			<version>1.0.0</version>
		</dependency>

	</dependencies>
```


### Create jar file from tutorial-maven-jar/

compile: compile the source code of the project
 
```sh
 mvn compile
```

package: take the compiled code and package it in its distributable format, such as a JAR.

```sh
 mvn package
```
the jar is created in target/tutorial-maven-jar-with-dependencies.jar

### Run jar file

```sh
  java -jar tutorial-maven-jar-with-dependencies.jar
```

the result is:

	I am utils.



