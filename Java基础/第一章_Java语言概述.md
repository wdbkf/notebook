## 第一章  Java语言概述

### 1. Java历史

 - 现在公司用的最多的是Java 8 和 Java 11版本。

 - Java技术体系平台

   + Java SE 支持面向桌面级应用
   + Java EE 主要针对Web应用程序开发
   + Java ME 支持Java程序运行在移动终端上的平台

### 2. Java特点

1. Java语言是面向对象的（oop）

2. 健壮的。Java的强类型机制、异常处理、垃圾自动收集等是Java程序健壮性的重要保证；

3. 跨平台性的。[即：一个编译好的.class文件可以在多个系统下运行，这种特性称为跨平台， “一次编译，到处运行”]

   ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210910213147717.png)

4. Java语言是解释型的。[解释性语言：javascript,PHP, java	编译性语言: c / c++；区别是：解释性语言编译后的代码，不能直接被机器执行，需要解释器来执行；编译性语言编译后的代码，可以直接被机器执行, c /c++ ]

### 3. Java运行机制及运行过程

- 因为有了JVM（java虚拟机），同一个java程序在三个不同的OS（Win、LInux、Mac）中都可以执行（不同的OS的JVM也不一样）。这样就实现了Java程序的跨平台性。
- Java 核心机制-Java 虚拟机 [JVM java virtual machine]
  1. JVM 是一个虚拟的计算机，具有指令集并使用不同的存储区域。负责执行指令，管理数据、内存、寄存器，包含在JDK 中；
  2. 对于不同的平台，有不同的虚拟机；
  3. Java 虚拟机机制屏蔽了底层运行平台的差别，实现了“一次编译，到处运行”

### 4. Java开发环境搭建

- JDK、JRE 和JVM 的包含关系
  - JDK = JRE + 开发工具集（例如 Javac,java 编译工具等)
  - JRE = JVM + Java SE 标准类库（java 核心类库）
  - 如果只想运行开发好的 .class 文件 只需要 JRE
- 下载安装JDK，配置环境变量path(环境变量的作用是为了在DOS的任意目录，可以使用java和javac命令)  Tips：环境变量中用户变量针对当前用户，系统变量针对全部用户


### 5. 开发入门

- 开发步骤
  - 将 Java 代码编写到扩展名为 Hello.java 的文件中。
  - 通过 javac 命令对该 java 文件进行编译，生成 .class 文件。
    - java文件中有中文时，如何处理：
      1. 在文件->设置文件编码->选择GBK（因为在命令行属性中代码页中文的编码模式是GBK，所以应该一致才能运行）
      2. 需要重新保存即可
  - 通过 java 命令对生成的 class 文件进行运行。（本质是将字节码文件装载到 JVM机执行）

- Java开发注意事项和细节说明
  - 一个源文件中最多只能有一个 public 类，其它类的个数不限。而且，编译后，每一个类，都生成对应一个.class。
  - Java语言严格区分大小写。
  - 如果源文件包含一个public类，则文件名必须按该类名命名。
  - 一个源文件中最多只能有一个 public 类。其它类的个数不限，也可以将 main 方法写在非 public 类中，然后指定运行非 public 类，这样入口方法就是非 public 的 main 方法。

- 转义字符

  ```java
  // \t	:一个制表位，实现对齐的功能
  // \n	:换行符
  // \\	:一个\
  // \"	:一个"
  // \'	:一个'
  // \r	:一个回车	
  public class ChangeChar{
  	public static void main(String[] args){
  		// 解读
  		// 1. 输出	韩顺平教育
  		// 2. \r 表示回车 碰到\r程序会把光标定回“韩”，在输出“北京”
  		System.out.println("韩顺平教育\r北京");
  		// \\:一个\	\\\\:  两个\\ 
  		System.out.println("C:\\Windows\\System32\\cmd.exe");
  		System.out.println("C:\\\\Windows\\\\System32\\\\cmd.exe");
  	}
  }
  ```

- 注释

  ```java
  //	单行注释	//
  //	多行注释  /* */
  //	文档注释  /** */
  ```

  -  被注释的文字，不会被 JVM（java 虚拟机）解释执行

  - 多行注释里面不允许有多行注释嵌套

  - 文档注释的内容（即”@author“和”@version“等javadoc标签）可以被JDK提供的工具javadoc所解析，生成一套以网页文件形式体现的该程序的说明文档，一般写在类

    如何生成（javadoc -d 文件夹名 -xx -yy Demo.java   如：javadoc -d d:\\\temp -author -version ChangeCharTest.java）

    ```java
    /**
    	*@author TT
    	*@version 1.0
    */
    public class ChangeCharTest{
    	public static void main(String[] args){
    		System.out.println("书名\t作者\t价格\t销量\n三国\t罗贯中\t120\t1000");
    	}
    }
    ```

- Java代码规范
  1. 类、方法的注释，要以javadoc的方式（文档注释）来写；
  2. 小技巧：选中代码，然后键入 tab 整体右移；选中代码，然后健入 shift+tab  整体左移；
  3. 源文件使用utf-8编码；
  4. 代码编写有次行风格和行尾风格。

- 常用DOS命令
  1. 查看当前目录是有什么内容 dir 
  2. 切换到其他盘下：盘符号 cd : change directory
  3. 切换到当前盘的其他目录下 (使用相对路径和绝对路径演示)，..\表示上一级目录   案例演示： cd	d:\abc2\test200	cd ..\\..\abc2\test200
  4. 切换到上一级： 案例演示： cd ..
  5. 切换到根目录：cd \
     案例演示：cd \
  6. 查看指定的目录下所有的子级目录 tree
  7. 清屏 cls [苍老师]
  8. 退出 DOS exit
  9.  md[创建目录],rd[删除目录],copy[拷贝文件],del[删除文件],echo[输入内容到文件],move[剪切]



## 第二章  变量

### 1.变量介绍

- 变量是程序的基本组成单位
- 变量相当于内存中一个数据存储空间的表示（不同的变量，类型不同，占用的空间大小不同），你可以把变量看做是一个房间的门牌号，通过门牌号我们可以找到房间，而通过变量名可以访问到变量(值)。
- 变量三要素：变量=变量名+值+数据类型

### 2. +号的使用

- 当左右两边都是数值型，则做加法运算
- 当左右两边有一方为字符串，则做拼接运算
- 运算顺序从左到右

### 3. 数据类型

- 每一种数据都定义了明确的数据类型，在内存中分配了不同大小的内存空间(字节)
- ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911192044954.png)
- 整型类型![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911193242808.png)
  - 整型的使用细节
    - ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911193815553.png)
    - ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911194725828.png)

-  浮点类型

  - 浮点型的分类![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911195108370.png)

  - 说明

    - 关于浮点数在机器中存放形式的简单说明，浮点数=符号位+指数位+尾数位
    -  尾数部分可能丢失，造成精度损失(小数都是近似值)。

  - 浮点型使用细节

    - ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911202031626.png)

    - ```java
      //浮点数使用陷阱: 2.7  和 8.1 / 3	比较
      //看看一段代码
      double num11 = 2.7;
      double num12 = 8.1 / 3; //2.7 System.out.println(num11);//2.7
      System.out.println(num12);//接近 2.7 的一个小数，而不是 2.7
      //得到一个重要的使用点: 当我们对运算结果是小数的进行相等判断时，要小心
      //应该是以两个数的差值的绝对值，在某个精度范围类判断
      if( num11 == num12) {
      System.out.println("num11 == num12  相等");
      }
      //正确的写法 , ctrl + /  注释快捷键,  再次输入就取消注释
      if(Math.abs(num11 - num12) < 0.000001 ) {
      System.out.println("差值非常小，到我的规定精度，认为相等...");
      }
      System.out.println(Math.abs(num11 - num12));
      //细节:如果是直接查询得到的小数或者直接赋值，是可以判断相等
      ```

- 字符类型

  - 字符类型可以表示单个字符,字符类型是 char，char 是两个字节(可以存放汉字)，多个字符我们用字符串 String(我们后面详细讲解 String)

  - 字符类型可以直接存放一个数字，但输出的是这个数字对应的ASCII码。

  - 字符类型使用细节

    - ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911212911780.png)

      

    - ```java
      public class IntDetail{
      	public static void main(String[] args) {
      		int n1 = 'a' + 'b';
      		char n2 = 'a' + 1;
      		char n3 = 'a';
      		System.out.println(n1); // 195 
      		System.out.println(n2); // b  char本质是一个数字，所以运算后输出ASCII码表中98对应的字符b
          	System.out.println((int)n2); // 98 输出b对应的ASCII码
      		System.out.println('a' + 10); // 107  char类型是可以进行运算的，相当于一个整数，因为它都对应有 Unicode 码
      
      	}
      
      }
      ```

    - ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911215848821.png)

- 布尔类型

  ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911223741525.png)

### 4. 编码

- ASCII 码介绍![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911223025155.png)
- Unicode 编码介绍![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911223216486.png)
- UTF-8 编码介绍![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210911223401977.png)

### 5. 数据类型转换





