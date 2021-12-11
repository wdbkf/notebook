[TOC]

## 第一章 Spring 概念

### 1. **Spring5** **框架概述**

1. Spring 是**轻量级**的**开源**的 JavaEE **框架**

   轻量级：它的体积很小，引用的jar包比较少也比较小，不需要引用其他组件，可以独立使用。

2. Spring 可以解决企业应用开发的复杂性

3. Spring 有两个核心部分：IOC 和 Aop

   1. IOC：控制反转，把创建对象过程交给 Spring 进行管理
   2. Aop：面向切面，不修改源代码进行功能增强

4. Spring 特点

   （1）方便解耦，简化开发

   （2）Aop 编程支持

   （3）方便程序测试

   （4）方便和其他框架进行整合

   （5）方便进行事务操作

   （6）降低 API 开发难度

## 第二章 IOC容器

### 1. **IOC（概念和原理）**

- 什么是 IOC

  （1）控制反转，把对象创建和对象之间的调用过程，交给 Spring 进行管理

  （2）使用 IOC 目的：为了耦合度降低

  （3）做入门案例就是 IOC 实现（见Idea）

- IOC 底层原理

  （1）**xml 解析、工厂模式、反射**

- 画图讲解 IOC 底层原理

  1.原始方式（耦合度太高）![image-20211114143710309](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114143710309.png)

  2.工厂模式（UserService与UserDao间的耦合度降低，但是UserFactory有耦合，并没有将耦合降低到最低限度！！）

  ![image-20211114143917982](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114143917982.png)

  3. **IOC过程**（进一步降低了耦合度！）

     ![image-20211114151252201](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114151252201.png)

     

### 2.**IOC（**BeanFactory **接口）**

- IOC 思想基于 IOC 容器完成，IOC 容器底层就是**对象工厂**

- Spring 提供 IOC 容器实现两种方式：（两个接口）

  （1）**BeanFactory**：IOC 容器基本实现，是 Spring 内部的使用接口，不提供开发人员进行使用

  - 加载配置文件时候不会创建对象，在获取对象（使用）才去创建对象

  （2）**ApplicationContext**：BeanFactory 接口的子接口，提供更多更强大的功能，一般由开发人员进行使用

  - 加载配置文件时候就会把在配置文件对象进行创建（推荐使用这种，把对象创建等耗时耗资源的操作让服务器执行，而不是等到用的时候再创建。）

- ApplicationContext 接口有实现类

  ![image-20211114153026925](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114153026925.png)



### 3.**IOC** **操作** **Bean** **管理**

#### 1.概念

1. **什么是** **Bean** **管理**

     Bean 管理指的是两个操作

   （1）Spring 创建对象

   （2）Spirng 注入属性

2. Bean 管理操作有两种方式

   （1）基于 xml 配置文件方式实现

   （2）基于注解方式实现

#### 2.**基于** **xml** **方式**

##### 1. **基于** **xml** **方式创建对象**

![image-20211114161835994](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114161835994.png)

（1）在 spring 配置文件中，使用 bean 标签，标签里面添加对应属性，就可以实现对象创建

（2）在 bean 标签有很多属性，介绍常用的属性

​	\* id 属性：唯一标识（命个名）

​	\* class 属性：类全路径（包类路径）

（3）创建对象时候，默认也是**执行无参数构造方法**完成对象创建



##### 2. **基于** **xml** **方式注入属性的两种方式**

- **DI**：**依赖注入，就是注入属性**（**DI和IOC的区别（面试）**：DI是IOC中一种具体实现，它就表示依赖注入，就是注入属性，但注入属性要在创建对象基础之上进行完成！）

  1. **第一种注入方式：使用** **set** **方法进行注入**

     ![image-20211114163322288](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114163322288.png)

     （3）测试

     ![image-20211114164857851](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114164857851.png)

  2. **第二种注入方式：使用有参数构造进行注入**

     ![image-20211114165537224](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114165537224.png)

     ![image-20211114165549005](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114165549005.png)

     （3）测试

     ![image-20211114165626432](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114165626432.png)

  3. **p** **名称空间注入（了解）**

     ![image-20211114170224644](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114170224644.png)

     其他操作和第一步相同，底层也是使用 set 方法进行注入。

     

##### 3. xml**注入其他类型属性**

1. **字面量**

   ![image-20211114171540338](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114171540338.png)

   

2. **注入属性-外部 bean**

   ![image-20211114185554292](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114185554292.png)



3. **注入属性-内部** **bean**

   （1）一对多关系：部门和员工

   一个部门有多个员工，一个员工属于一个部门

   部门是一，员工是多

   （2）在实体类之间表示一对多关系，员工表示所属部门，使用对象类型属性进行表示；

   ![image-20211114192732518](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114192732518.png)

   ![image-20211114192745884](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114192745884.png)

   

4. **注入属性-级联赋值**

   ![image-20211114193033136](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114193033136.png)

   ![image-20211114193320401](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114193320401.png)

   

5. **xml** **注入集合属性**

   ![image-20211114200614510](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114200614510.png)

   ![image-20211114200742544](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114200742544.png)

   - **细节**

     - **在集合里面设置对象类型值**

       ![image-20211114200920908](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114200920908.png)

     - **把集合注入部分提取出来**

       ![image-20211114201011728](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114201011728.png)

       ![image-20211114201022783](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114201022783.png)

   

##### 5. **FactoryBean**

![image-20211114202509082](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114202509082.png)



##### 6.bean作用域

![image-20211114203329939](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114203329939.png)

![image-20211114203401085](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114203401085.png)



##### 7. bean生命周期

![image-20211114211610104](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114211610104.png)

![image-20211114211659211](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114211659211.png)

![image-20211114211832328](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114211832328.png)

![image-20211114211906925](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114211906925.png)



##### 8. **xml** **自动装配**

1. **什么是自动装配**

   （1）根据指定装配规则（属性名称或者属性类型），Spring 自动将匹配的属性值进行注入；

2. **演示自动装配过程**

   （1）根据属性名称自动注入

   ![image-20211114213300301](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114213300301.png)

   ![image-20211114213315915](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114213315915.png)

   （2）根据属性类型自动注入（配置创建对象的bean只能有一个）

   ![image-20211114213416437](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114213416437.png)

   

##### 9.**外部属性文件**

![image-20211114214951572](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114214951572.png)

![image-20211114215020233](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211114215020233.png)



#### 3. 基于注解方式

1. **什么是注解**

（1）注解是代码特殊标记，格式：@注解名称(属性名称=属性值, 属性名称=属性值..)

（2）使用注解，注解作用在类上面，方法上面，属性上面

（3）使用注解目的：简化 xml 配置



2. **Spring** **针对** **Bean** **管理中创建对象提供注解**

（1）@Component

（2）@Service

（3）@Controller

（4）@Repository

\* 上面四个注解功能是一样的，都可以用来创建 bean 实例



3. **基于注解方式实现对象创建**

![image-20211116155930487](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116155930487.png)

![image-20211116160309635](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116160309635.png)

4. **开启组件扫描细节配置**

   ![image-20211116160441961](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116160441961.png)



5. **基于注解方式实现属性注入**

   ![image-20211116161533101](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116161533101.png)

   ![image-20211116161604924](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116161604924.png)

   

6. **完全注解开发** 

   ![image-20211116161710724](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116161710724.png)





## 第三章 Aop

### 1. **什么是** **AOP**

（1）面向切面编程（方面），利用 AOP 可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。

（2）通俗描述：不通过修改源代码方式，在主干功能里面添加新功能

（3）使用登录例子说明 AOP

![image-20211116214615890](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116214615890.png)



### 2. **AOP（底层原理）**

1. **AOP** **底层使用动态代理**

   （1）有两种情况动态代理

   ![image-20211116214750280](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116214750280.png)



- **第一种 ：AOP（JDK动态代理）**

  1、**使用 JDK 动态代理，使用 Proxy 类里面的方法创建代理对象**

  ![image-20211116215157635](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116215157635.png)

  2、**编写** **JDK** **动态代理代码**

  ![image-20211116215407308](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116215407308.png)

  ![image-20211116215529787](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116215529787.png)

  

  

### 3. **AOP（术语）**

![image-20211116215653010](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116215653010.png)

![image-20211116215735112](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116215735112.png)



### 4. **AOP** **操作（准备工作）** 

![image-20211116215903597](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116215903597.png)

![image-20211116215944762](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211116215944762.png)

### 5. **AOP** **操作（AspectJ** **注解）**

![image-20211117144831711](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117144831711.png)

![image-20211117145008814](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117145008814.png)

![image-20211117154219803](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117154219803.png)

![image-20211117154232177](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117154232177.png)



### 6. **AOP** **操作（AspectJ** **配置文件）**

![image-20211117154331263](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117154331263.png)





## 第四章 JdbcTemplate

### 1.**JdbcTemplate(概念和准备**) 

**1、什么是 JdbcTemplate**

（1）Spring 框架对 JDBC 进行封装，使用 JdbcTemplate 方便实现对数据库操作

![image-20211117194755093](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117194755093.png)

![image-20211117195802213](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117195802213.png)



### 2.**JdbcTemplate** **操作数据库（添加）**

![image-20211117200042047](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200042047.png)

![image-20211117200055418](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200055418.png)



### 3. **JdbcTemplate** **操作数据库（修改和删除）**

![image-20211117200147253](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200147253.png)



### 4. **JdbcTemplate** **操作数据库（查询返回某个值）**

![image-20211117200213256](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200213256.png)

![image-20211117200220336](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200220336.png)



### 5. **JdbcTemplate** **操作数据库（查询返回对象）**

![image-20211117200301883](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200301883.png)



### 6. **JdbcTemplate** **操作数据库（查询返回集合）**

![image-20211117200359644](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200359644.png)



### 7. **JdbcTemplate** **操作数据库（批量操作）**

![image-20211117200456775](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200456775.png)

![image-20211117200517900](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200517900.png)

![image-20211117200616122](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200616122.png)

![image-20211117200624999](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117200624999.png)





## 第五章 事务管理

### 1. **事务操作（事务概念）**

**1、什么事务**

（1）事务是数据库操作最基本单元，逻辑上一组操作，要么都成功，如果有一个失败所有操作都失败

（2）典型场景：银行转账

   \* lucy 转账 100 元 给 mary

   \* lucy 少 100，mary 多 100

**2、事务四个特性（ACID）** 

（1）原子性  (要么都成功要么都失败)

（2）一致性（操作前后总量不变）

（3）隔离性（多事务操作中不会互相影响）

（4）持久性（事务提交后，表中数据也变化）



### 2. **事务操作（搭建事务操作环境）**

![image-20211117230720736](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117230720736.png)

![image-20211117230801765](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117230801765.png)

![image-20211117230850640](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117230850640.png)



### 3. **事务操作（Spring** **事务管理介绍）**

![image-20211117231141893](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231141893.png)



### 4. **事务操作（注解声明式事务管理）**（重要）

![image-20211117231238519](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231238519.png)

![image-20211117231300293](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231300293.png)



### 5. **事务操作（声明式事务管理参数配置）**

![image-20211117231610631](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231610631.png)

![image-20211117231626847](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231626847.png)

![image-20211117231707430](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231707430.png)



### 6. **事务操作（XML** **声明式事务管理）**

![image-20211117231946272](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231946272.png)

![image-20211117231956916](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117231956916.png)



### 7. **事务操作（完全注解声明式事务管理）**

![image-20211117232117331](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117232117331.png)

![image-20211117232126206](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211117232126206.png)





## 第六章 Spring5 新特性

### 1. 整合日志框架、**@Nullable** **注解**、**函数式风格** **GenericApplicationContext**

![image-20211118160209168](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211118160209168.png)

![image-20211118160534698](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211118160534698.png)



### 2. **Spring5** **支持整合** **JUnit5**

![image-20211118160743766](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211118160743766.png)

![image-20211118160842094](E:\Java_Notes\notebook\Spring 5\Spring5_notes.assets\image-20211118160842094.png)



### 3.**Spring5** **框架新功能（Webflux）** 

前置知识：SpringMVC、SpringBoot、Maven、Java 8新特性 

学完再来看这里！

 
