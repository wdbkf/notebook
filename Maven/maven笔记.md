## Maven基础

### 1. Maven简介

- Maven是什么

  ![image-20211208213625719](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208213625719.png)

- Maven的作用

  ![image-20211208213709645](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208213709645.png)

  

### 2. 下载与安装

### 3. Maven基础概念（重点）

- 仓库

  ![image-20211208223006688](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208223006688.png)

  ![image-20211208223027037](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208223027037.png)

- 坐标

  ![image-20211208223128292](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208223128292.png)

- 本地仓库配置 （setting.xml 文件中配置）

  ![image-20211208223506883](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208223506883.png)

- 远程仓库配置

  ![image-20211208223531976](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208223531976.png)

- 镜像仓库配置

  ![image-20211208223552809](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208223552809.png)

- 全局setting与用户setting的区别

  ![image-20211208223703913](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208223703913.png)

  

### 4. 第一个Maven项目(手工制作)（重点）

#### 1. Maven 工程目录结构

- ![image-20211208224405177](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208224405177.png)

- 在src同层目录下创建pom.xml

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <project 
      xmlns="http://maven.apache.org/POM/4.0.0" 
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
      xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd"> 
      <modelVersion>4.0.0</modelVersion> 
      <groupId>com.itheima</groupId> 
      <artifactId>project-java</artifactId> 
      <version>1.0</version> 
      <packaging>jar</packaging> 
      <dependencies> 
          <dependency> 
              <groupId>junit</groupId> 
              <artifactId>junit</artifactId> 
              <version>4.12</version>
          </dependency>
      </dependencies>
  </project>
  ```

  

#### 2. 构建命令 （重要）

![image-20211208224602536](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208224602536.png)

#### 3. 插件创建工程

- 创建工程

  ```java
  mvn archetype:generate
  	-DgroupId={project-packaging} 
  	-DartifactId={project-name} 
  	-DarchetypeArtifactId=maven-archetype-quickstart
  	-DinteractiveMode=false
  ```

- 创建java工程

  ```java
  mvn archetype:generate -DgroupId=com.itheima -DartifactId=java-project -
  DarchetypeArtifactId=maven-archetype-quickstart -Dversion=0.0.1-snapshot -
  DinteractiveMode=false
  ```

- 创建web工程

  ```java
  mvn archetype:generate -DgroupId=com.itheima -DartifactId=web-project -
  DarchetypeArtifactId=maven-archetype-webapp -Dversion=0.0.1-snapshot -
  DinteractiveMode=false
  ```

  

### 5. 第一个Maven项目(IDEA生成)（重点）

![image-20211208232726800](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208232726800.png)

![image-20211208232735484](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208232735484.png)

- maven_home directory : 选择maven3.6.1 版本
- **User setting file** : 选择 D:\Program Files\apache-maven-3.6.1\conf 下的setting.xml  里面**配置了 自定义本地仓库的位置** ！！！【之前几个maven项目都默认放在c盘中 不太好！】

![image-20211208233236374](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211208233236374.png)

![image-20211210162350692](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210162350692.png)

![image-20211210162407602](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210162407602.png)



### 6. 依赖管理（重点）

#### 1. 依赖配置

![image-20211210170314319](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210170314319.png)

#### 2. 依赖传递

![image-20211210170517701](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210170517701.png)

![image-20211210170755485](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210170755485.png)

#### 3. 可选依赖

![image-20211210170837320](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210170837320.png)

#### 4. 排除依赖

![image-20211210170903043](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210170903043.png)

#### 5. 依赖范围

![image-20211210171737248](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210171737248.png)

![image-20211210171955473](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210171955473.png)

### 7. 生命周期与插件

#### 1. 项目构建生命周期

![image-20211210172728746](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210172728746.png)

![image-20211210172751099](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210172751099.png)

![image-20211210172825010](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210172825010.png)

![image-20211210172838335](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210172838335.png)

![image-20211210172917084](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210172917084.png)

#### 2. 插件

![image-20211210173041673](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210173041673.png)



## Maven高级

### 1. 分模块开发与设计 （重点）

- ![image-20211210221456085](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210221456085.png)

  - ![image-20211210221522863](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210221522863.png)

  - ![image-20211210221559068](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210221559068.png)

  - ![image-20211210221832881](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210221832881.png)

  - ![image-20211210222043006](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210222043006.png)

    

### 2. 聚合（重点）

- ![image-20211210222405459](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210222405459.png)

- ![image-20211210222451054](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210222451054.png)

### 3. 继承（重点）

- ![image-20211210222519963](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210222519963.png)
- ![image-20211210222554909](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210222554909.png)
- ![image-20211210222641372](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210222641372.png)
- ![image-20211210223140207](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223140207.png)
- ![image-20211210223149105](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223149105.png)

### 4. 属性（重点）

- ![image-20211210223324986](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223324986.png)
- ![image-20211210223350095](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223350095.png)
- ![image-20211210223451347](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223451347.png)
- ![image-20211210223504930](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223504930.png)
- ![image-20211210223537695](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223537695.png)
- ![image-20211210223606814](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223606814.png)
- ![image-20211210223624897](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223624897.png)

### 5. 版本管理

- ![image-20211210223644156](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223644156.png)
- ![image-20211210223650503](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223650503.png)
- ![image-20211210223726940](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223726940.png)

### 6. 资源配置

- ![image-20211210223759867](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223759867.png)
- ![image-20211210223828566](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223828566.png)
- ![image-20211210223917796](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223917796.png)

### 7. 多环境开发配置

- ![image-20211210223935212](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210223935212.png)

- 多环境配置

  ![image-20211210224044471](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224044471.png)

- ![image-20211210224125138](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224125138.png)

### 8. 跳过测试 （了解）

- ![image-20211210224307561](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224307561.png)
- ![image-20211210224321174](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224321174.png)
- ![image-20211210224347095](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224347095.png)
- ![image-20211210224354770](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224354770.png)

### 9. 私服（重点）

- ![image-20211210224441851](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224441851.png)

- ![image-20211210224449102](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224449102.png)

- ![image-20211210224518688](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224518688.png)

- ![image-20211210224600514](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224600514.png)

- ![image-20211210224623416](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224623416.png)

- ![image-20211210224755709](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224755709.png)

- ![image-20211210224851970](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224851970.png)

- ![image-20211210224923866](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210224923866.png)

- ![image-20211210225030006](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210225030006.png)

- ![image-20211210225107395](E:\Java_Notes\notebook\Maven\maven笔记.assets\image-20211210225107395.png)

  



