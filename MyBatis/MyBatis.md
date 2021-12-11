## 一、MyBatis 简介

### 1. Hibernate 的缺点 与 MyBatis的优点

![image-20211129161827142](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211129161827142.png)



![image-20211129161802320](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211129161802320.png)

### 2. MyBatis简介

- MyBatis 是支持定制化 SQL、存储过程以及高级映射的优秀的持久层框架
- MyBatis 避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集。
- MyBatis可以使用简单的XML或注解用于配置和原始映射，将接口和Java的POJO（Plain Old Java Objects，普通的Java对象）映射成数据库中的记录.



### 3. 为什么要使用MyBatis？

- MyBatis是一个半自动化的持久化层框架。

- JDBC

  - SQL夹在Java代码块里，耦合度高导致硬编码内伤

  - 维护不易且实际开发需求中sql是有变化，频繁修改的情况多见

- Hibernate和 JPA

  - 长难复杂SQL，对于Hibernate而言处理也不容易

  - 内部自动生产的SQL，不容易做特殊优化。

  - 基于全映射的全自动框架，大量字段的POJO进行部分映射时比较困难。导致数据库性能下降。 

- 对开发人员而言，核心sql还是需要自己优化

- **sql和java编码分开，功能边界清晰，一个专注数据、一个专注业务。**



### 4.  mybatis提供了哪些功能

    1. 提供了创建Connection ,Statement, ResultSet的能力 ，不用开发人员创建这些对象了
    2. 提供了执行sql语句的能力， 不用你执行sql
    3. 提供了循环sql， 把sql的结果转为java对象， List集合的能力
       while (rs.next()) {
       	Student stu = new Student();
       	stu.setId(rs.getInt("id"));
       	stu.setName(rs.getString("name"));
       	stu.setAge(rs.getInt("age"));
       	//从数据库取出数据转为 Student 对象，封装到 List 集合
       	stuList.add(stu);
    4. 提供了关闭资源的能力，不用你关闭Connection, Statement, ResultSet

## 二、**MyBatis** **框架快速入门**

### 1. **快速开始一个** **MyBatis**

详见idea的maven项目 或 初始课程笔记 ！

- **搭建** **MyBatis** **开发环境**
  - 创建 mysql 数据库和表
  - 创建 maven 工程
  - 删除默认创建的 App 类文件
  - 加入 maven 坐标(依赖)
  - 加入 maven 插件
  - **编写** **Student** **实体类**
  - **编写** **Dao** **接口** **StudentDao**
  - **编写** **Dao** **接口** **Mapper** **映射文件** **StudentDao.xml**
  - **创建** **MyBatis** **主配置文件**
  - **创建测试类** **MyBatisTest**
  - 配置日志功能

### 2. **基本** **CURD** **的操作**

详见idea的maven项目 或 初始课程笔记 ！

- **eg :   insert**

  - **StudentDao** **接口中增加方法**

    ```java
    int insertStudent(Student student);
    ```

  - **StudentDao.xml** **加入** **sql** **语句**

    ```java
    <insert id="insertStudent">
     	insert into student(id,name,email,age) 
    		values(#{id},#{name},#{email},#{age})
    </insert>
    ```

  - **增加测试方法**

    ```java
    @Test
    public void testInsert() throws IOException {
         //1.mybatis 主配置文件 
         String config = "mybatis.xml";
         //2.读取配置文件 
         InputStream in = Resources.getResourceAsStream(config);
         //3.创建 SqlSessionFactory 对象 
         SqlSessionFactory factory = new SqlSessionFactoryBuilder().build(in);
         //4.获取 SqlSession
         SqlSession session = factory.openSession();
         //5.创建保存数据的对象 
         Student student = new Student();
         student.setId(1005);
         student.setName("张丽");
         student.setEmail("zhangli@163.com");
         student.setAge(20);
         //6.执行插入 insert
         int rows = session.insert(
        "com.bjpowernode.dao.StudentDao.insertStudent",student);
         //7.提交事务 
         session.commit();
         System.out.println("增加记录的行数:"+rows);
         //8.关闭 SqlSession
         session.close();
    }
    ```

    

### 3. **MyBatis** **内部对象分析**

- **对象使用**

  SqlSession , SqlSessionFactory 等

  - **Resources** **类**

    Resources 类，顾名思义就是资源，用于读取资源文件。其有很多方法通过加载并解析资源文件，返回不同类型的 IO 流对象。

  - **SqlSessionFactoryBuilder** **类**

    SqlSessionFactory 的创 建 ， 需 要 使 用 SqlSessionFactoryBuilder 对 象 的 build() 方 法 。 由于SqlSessionFactoryBuilder 对象在创建完工厂对象后，就完成了其历史使命，即可被销毁。所以，一般会将该 SqlSessionFactoryBuilder 对象创建为一个方法内的局部对象，方法结束，对象销毁。

  - **SqlSessionFactory** **接口**

    SqlSessionFactory 接口对象是一个重量级对象（系统开销大的对象），**是线程安全**的，所以一个应用只需要一个该对象即可。创建 SqlSession 需要使用 SqlSessionFactory 接口的的 openSession()方法。

    - openSession(true)：创建一个有自动提交功能的 SqlSession 

    - openSession(false)：创建一个非自动提交功能的 SqlSession，需手动提交

    - openSession()：同 openSession(false)

  - **SqlSession** **接口**

    SqlSession 接口对象用于执行持久化操作。一个 SqlSession 对应着一次数据库会话，一次会话以SqlSession 对象的创建开始，以 SqlSession 对象的关闭结束。

    **SqlSession 接口对象是线程不安全的**，所以每次数据库会话结束前，需要马上调用其 close()方法，将其关闭。再次需要会话，再次创建。 SqlSession 在方法内部创建，使用完毕后关闭。

- **创建工具类**

  - **创建** **MyBatisUtil** **类**

    ```java
    public class MyBatisUtil {
         //定义 SqlSessionFactory
         private static SqlSessionFactory factory = null;
         static {
             //使用 静态块 创建一次 SqlSessionFactory
             try{
                 String config = "mybatis-config.xml";
                 //读取配置文件 
                 InputStream in = Resources.getResourceAsStream(config);
                 //创建 SqlSessionFactory 对象 
                 factory = new SqlSessionFactoryBuilder().build(in);
             }catch (Exception e){
             	factory = null;
             	e.printStackTrace();
             }
         }
         /* 获取 SqlSession 对象 */
         public static SqlSession getSqlSession(){
             SqlSession session = null;
             if( factory != null){
             	session = factory.openSession();
             }
             return session;
     	 } 
    }
    ```

- **使用** **MyBatisUtil** **类**

  ```java
  @Test
  public void testUtils() throws IOException {
       SqlSession session = MyBatisUtil.getSqlSession();
       List<Student> studentList = session.selectList(
      "com.bjpowernode.dao.StudentDao.selectStudents");
       studentList.forEach( student -> System.out.println(student));
       session.close();
  }
  ```

  

### 4. **MyBatis** **使用传统** **Dao** **开发方式**

使用 Dao 的实现类,操作数据库, **详见 Idea的maven项目**！！

- **Dao** **开发**

  - **创建** **Dao** **接口实现类**

    ```java
    public class StudentDaoImpl implements StudentDao
    ```

  - **实现接口中** **select** **方法**

    ```java
    public List<Student> selectStudents() {
         SqlSession session = MyBatisUtil.getSqlSession();
         List<Student> studentList = session.selectList(
        "com.bjpowernode.dao.StudentDao.selectStudents");
         session.close();
         return studentList;
    }
    ```

  - **测试查询操作:**

    ```java
    public class MyBatisTest {
     	StudentDao studentDao = new StudentDaoImpl();
    }
        @Test
        public void testSelect() throws IOException {
             final List<Student> studentList = studentDao.selectStudents();
             studentList.forEach( stu -> System.out.println(stu));
    }
    ```

    

- **传统** **Dao** **开发方式的分析**

  在前面例子中自定义 Dao 接口实现类时发现一个问题：Dao 的实现类其实并没有干什么实质性的工作，它仅仅就是通过 SqlSession 的相关 API 定位到映射文件 mapper 中相应 id 的 SQL 语句，真正对 DB 进行操作的工作其实是由框架通过 mapper 中的 SQL 完成的。

  所以，**MyBatis 框架就抛开了 Dao 的实现类**，**直接定位到映射文件 mapper 中的相应 SQL 语句，对DB 进行操作**。**这种对 Dao 的实现方式称为 Mapper 的动态代理方式**。

  Mapper 动态代理方式无需程序员实现 Dao 接口。接口是由 MyBatis 结合映射文件自动生成的动态代理实现的。



## 三、 **MyBatis** **框架** **Dao** **代理**

### 1. **Dao** **接口动态代理**

- **Dao** **代理实现** **CURD**

  - **步骤**

    - 去掉 Dao 接口实现类

    - **getMapper** **获取代理对象**

      只需**调用 SqlSession 的 getMapper()方法**，即可获取指定接口的实现类对象。该方法的参数为指定 Dao接口类的 class 值。

      ```java
      StudentDao studentDao = 
      	MyBatisUtil.getSqlSession().getMapper(StudentDao.class);
      ```

    - **使用** **Dao** **代理对象方法执行** **sql** **语句**

      ```java
      // select 方法:
      @Test
      public void testSelect() throws IOException {
           final List<Student> studentList = studentDao.selectStudents();
           studentList.forEach( stu -> System.out.println(stu));
      }
      ```

  - **原理**

    - 动态代理

      ![image-20211202192802142](E:\Java_Notes\notebook\MyBatis\image-20211202192802142.png)

    - MapperProxy 类定义:

      ![image-20211202192831369](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202192831369.png)

    - invoke()方法:

       ![image-20211202192853051](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202192853051.png)

    - 重点方法:

      ![image-20211202192910926](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202192910926.png)

      

### 2. ****深入理解参数****

- **parameterType（一般不写）**

  parameterType: 接口中方法参数的类型， 类型的完全限定名或别名。**这个属性是可选的**，因为 MyBatis可以推断出具体传入语句的参数，默认值为未设置（unset）。接口中方法的参数从 java 代码传入到mapper 文件的 sql 语句。

  ​	int 或 java.lang.Integer

  ​	hashmap 或 java.util.HashMap

  ​	list 或 java.util.ArrayList

  ​	student 或 com.bjpowernode.domain.Student

  更多看课件资源中的有关别名的文件或者 mybatis-3.5.1.pdf 的 15 页。

  <select>,<insert>,<update>,<delete>都可以使用 parameterType 指定类型。

  eg:

  ```java
  <delete id="deleteStudent" parameterType="int">
   	delete from student where id=#{studentId}
  </delete>
  等同于
  <delete id="deleteStudent" parameterType="java.lang.Integer">
   	delete from student where id=#{studentId}
  </delete>
  ```

- **MyBatis** **传递参数**

  从 java 代码中把参数传递到 mapper.xml 文件。

  - **一个简单参数**

    Dao 接口中方法的参数只有一个简单类型（java 基本类型和String），占位符 **#{** **任意字符** **}**，和方法的参数名无关。

    ![image-20211202193606338](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202193606338.png)

    ![image-20211202193622378](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202193622378.png)

  - **多个参数-使用@Param  (常用！)**

    当 Dao 接口方法多个参数，需要通过名称使用参数。在方法形参前面加入@Param(“自定义参数名”)，mapper 文件使用#{自定义参数名}。

    ![image-20211202193819754](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202193819754.png)

  - **多个参数使用对象 （常用！）**

    使用 java 对象传递参数， java 的属性值就是 sql 需要的参数值。 每一个属性就是一个参数。

    语法格式： #{property,javaType=java 中数据类型名,jdbcType=数据类型名称 }

    javaType, jdbcType 的类型 MyBatis 可以检测出来，一般不需要设置。**常用格式 #{ property }**

    ![image-20211202194051442](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202194051442.png)

  - **多个参数-按位置**

    参数位置从 0 开始， 引用参数语法 **#{ arg** **位置** **}** ， 第一个参数是#{arg0}, 第二个是#{arg1}

    注意：mybatis-3.3 版本和之前的版本使用#{0},#{1}方式， 从 mybatis3.4 开始使用#{arg0}方式。

    ![image-20211202194137454](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202194137454.png)

  - **多个参数-使用Map**

    Map 集合可以存储多个值，使用Map向 mapper 文件一次传入多个参数。Map 集合使用 String的 key，Object 类型的值存储参数。 mapper 文件使用 # { key } 引用参数值。

    ![image-20211202194347704](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202194347704.png)

    ![image-20211202194357829](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202194357829.png)

  - **#和$   （面试！！！）** 

    - **#：占位符**，告诉 mybatis 使用实际的参数值代替。并使用 **PrepareStatement 对象执行 sql 语句**, #{…}代替sql 语句的“?”。这样做更安全，更迅速，通常也是首选做法。

      ![image-20211202194546824](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202194546824.png)

      ![image-20211202194612364](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202194612364.png)

    - **$**: **字符串替换，**告诉 mybatis 使用\$包含的“字符串”替换所在位置。使用 **Statement 把 sql 语句和${}的内容连接起来**。**主要用在替换表名，列名，不同列排序等操作。**

      ![image-20211202195049474](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202195049474.png)

    -  **\# 和 $区别**

          1. #使用 ？在sql语句中做占位的， 使用PreparedStatement执行sql，效率高
        2. #能够避免sql注入，更安全。
          3. $不使用占位符，是字符串连接方式，使用Statement对象执行sql，效率低
          4. $有sql注入的风险，缺乏安全性。
          5. $:可以替换表名或者列名

### 3. **处理查询结果**

- **resultType**

  resultType: 执行 sql 得到 ResultSet 转换的类型，使用类型的完全限定名或 别名 (在mybatis主配置文件中定义，使用\<typeAlias>定义别名)。 注意如果返回的是集合，那应该设置为集合包含的类型，而不是集合本身。resultType 和 resultMap，不能同时使用。

  ![image-20211202221401691](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202221401691.png)

  - **简单类型**

    ![image-20211202221501404](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202221501404.png)

  - **对象类型**

    ![image-20211202221647748](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202221647748.png)

    ![image-20211202221657671](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202221657671.png)

  - **Map**

    ![image-20211202221950966](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202221950966.png)

- **resultMap  (重要！！)** 

  **resultMap 可以自定义 sql 的结果和 java 对象属性的映射关系**。更灵活的把列值赋值给指定属性。常用在列名和 java 对象属性名不一样的情况。

  使用方式：

  1. 先定义 resultMap,指定列名和属性的对应关系。

  2. 在\<select>中把 resultType 替换为 resultMap。

  ![image-20211202222328576](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202222328576.png)

- **实体类属性名和列名不同的处理方式**

  - **使用列别名和\<resultType>**

    ![image-20211202223013874](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202223013874.png)

  - **使用\<resultMap>**

### 4. **模糊like** 

模糊查询的实现有两种方式， 一是 java 代码中给查询数据加上“%” ; 二是在 mapper 文件 sql 语句的条件位置加上“%”

![image-20211202223238641](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202223238641.png)

![image-20211202223246591](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202223246591.png)



## 四、**MyBatis** **框架动态** **SQL**

动态 SQL，通过 MyBatis 提供的各种标签对条件作出判断以**实现动态拼接 SQL 语句**。这里的条件判断使用的表达式为 OGNL 表达式。常用的动态 SQL 标签有<if>、<where>、<choose/>、<foreach>等。

MyBatis 的动态 SQL 语句，与 JSTL 中的语句非常相似。

**动态 SQL，主要用于解决查询条件不确定的情况**：在程序运行期间，根据用户提交的查询条件进行查询。提交的查询条件不同，执行的 SQL 语句不同。若将每种可能的情况均逐一列出，对所有条件进行排列组合，将会出现大量的 SQL 语句。此时，可使用动态 SQL 来解决这样的问题。

![image-20211202223735686](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202223735686.png)

### 1. **动态** **SQL-if**

对于该标签的执行，当 test 的值为 true 时，会将其包含的 SQL 片断拼接到其所在的 SQL 语句中。语法：<if test="条件"> sql 语句的部分 </if>

![image-20211202223859444](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202223859444.png)

![image-20211202224019215](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202224019215.png)



### 2.**动态** **SQL-where**

<if/>标签的中存在一个比较麻烦的地方：需要在 where 后手工添加 1=1 的子句。因为，若 where 后的所有<if/>条件均为 false，而 where 后若又没有 1=1 子句，则 SQL 中就会只剩下一个空的 where，SQL出错。所以，在 where 后，需要添加永为真子句 1=1，以防止这种情况的发生。但当数据量很大时，会严重影响查询效率。

使用<where/>标签，在有查询条件时，可以自动添加上 where 子句；没有查询条件时，不会添加where 子句。需要注意的是，第一个<if/>标签中的 SQL 片断，可以不包含 and。不过，写上 and 也不错，系统会将多出的 and 去掉。但其它<if/>中 SQL 片断的 and，必须要求写上。否则 SQL 语句将拼接出错。

语法：<where> 其他动态 sql </where>

![image-20211202224232179](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202224232179.png)

![image-20211202224254488](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202224254488.png)



### 3. **动态** **SQL-foreach**

<foreach/>标签用于实现对于数组与集合的遍历。对其使用，需要注意：

1. collection 表示要遍历的集合类型, list ，array 等。

2. open、close、separator 为对遍历内容的 SQL 拼接。

   ```java
   语法：
   <foreach collection="集合类型" open="开始的字符" close="结束的字符" 
   	item="自定义的,表示数组和集合成员的变量,集合中的成员" separator="集合成员之间的分隔符">
    		#{item 的值}
   </foreach>
   ```

   - **遍历** **List<简单类型>**

     ![image-20211202224741800](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202224741800.png)

     ![image-20211202224748916](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202224748916.png)

   - **遍历** **List<对象类型>**

     ![image-20211202224825854](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202224825854.png)

     ![image-20211202224833144](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202224833144.png)

     

### 4. **动态** **SQL-**代码**片段**

<sql/>标签用于定义 SQL 片断，**以便其它 SQL 标签复用**。而其它标签使用该 SQL 片断，需要使用<include/>子标签。该<sql/>标签可以定义 SQL 语句中的任何部分，所以<include/>子标签可以放在动态 SQL的任何位置。

![image-20211202225020957](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225020957.png)



## 五、**MyBatis** **配置文件**

### 1. **主配置文件**

![image-20211202225221388](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225221388.png)

### 2. **dataSource** **标签**

Mybatis 中访问数据库，可以连接池技术，但它采用的是自己的连接池技术。在 Mybatis 的 mybatis.xml配置文件中，通过<dataSource type="pooled">来实现 Mybatis 中连接池的配置。

- **dataSource** **类型**

  ![image-20211202225405221](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225405221.png)

- **dataSource** **配置**

  ![image-20211202225441720](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225441720.png)

  ![image-20211202225449511](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225449511.png)

- **数据库的属性配置文件 （重要！）**

  把数据库连接信息放到一个单独的文件中。 和mybatis主配置文件分开。
  目的是便于修改，保存，处理多个数据库的信息。

    1）在resources目录中定义一个属性配置文件， xxxx.properties ,例如 jdbc.properties
          在属性配置文件中， 定义数据，格式是 key=value 
  		  **key： 一般使用 . 做多级目录的**。
  		  例如 jdbc.mysql.driver    , jdbc.driver, mydriver
  		  jdbc.driver=com.mysql.jdbc.Driver
  		  jdbc.url=jdbc:mysql//.....
  		  jdbc.username=root
  		  jdbc.password=123456
  	     ![image-20211202225944884](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225944884.png)

  
  
    2）在mybatis的主配置文件，使用<property> 指定文件的位置
  	     在需要使用值的地方， ${key}
  
  ![image-20211202225958630](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225958630.png)
  
  

### 3. **事务**

- **默认需要手动提交事务**

  Mybatis 框架是对 JDBC 的封装，所以 Mybatis 框架的事务控制方式，本身也是用 JDBC 的 Connection对象的 commit(), rollback() .

  Connection 对象的 setAutoCommit()方法来设置事务提交方式的。自动提交和手工提交。

  ![image-20211202225813454](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225813454.png)

- **自动提交事务**

  ![image-20211202225901353](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202225901353.png)

### 4. **别名**

![image-20211202230204969](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202230204969.png)

![image-20211202230217582](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202230217582.png)



### 5. **mapper** **文件**（重要！）

![image-20211202230307324](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202230307324.png)



## 六、拓展

### 1.**PageHelper**

- **Mybatis** **通用分页插件**

  [](https://github.com/pagehelper/Mybatis-PageHelper)

- **基于** **PageHelper** **分页：**

  - **maven** **坐标**

  ```java
  <dependency>
   	 <groupId>com.github.pagehelper</groupId>
   	 <artifactId>pagehelper</artifactId>
       <version>5.1.10</version>
  </dependency>
  ```

  - **加入** **plugin** **配置**

  ```java
  // 在<environments>之前加入
  <plugins>
   <plugin interceptor="com.github.pagehelper.PageInterceptor" />
  </plugins>
  ```

  - **PageHelper** **对象**

    查询语句之前调用 PageHelper.startPage 静态方法。除了 PageHelper.startPage 方法外，还提供了类似用法的 PageHelper.offsetPage 方法。在你需要进行分页的 MyBatis 查询方法前调用 PageHelper.startPage 静态方法即可，紧跟在这个方法后的第一个 **MyBatis 查询方法**会被进行分页。

    ![image-20211202230829750](E:\Java_Notes\notebook\MyBatis\MyBatis.assets\image-20211202230829750.png)

    
