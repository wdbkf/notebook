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

### 1. 变量介绍

- 变量是程序的基本组成单位
- 变量相当于内存中一个数据存储空间的表示（不同的变量，类型不同，占用的空间大小不同），你可以把变量看做是一个房间的门牌号，通过门牌号我们可以找到房间，而通过变量名可以访问到变量(值)。
- 变量三要素：变量=变量名+值+数据类型

### 2. +号的使用

- 当左右两边都是数值型，则做加法运算
- 当左右两边有一方为字符串，则做拼接运算
- 运算顺序从左到右

### 3. 数据类型（笔试）

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

  - 字符类型可以直接存放一个数字，但输出的是ASCII码表中这个数字对应的字符。

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

### 5. 数据类型转换（笔试）

- 自动类型转换

  - ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912133918830.png)

  - 自动类型转换注意和细节

    - ![image-20210912135612148](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912135612148.png)

    - ```java
      //自动类型转换细节
      public class AutoConvertDetail {
          //编写一个 main 方法
          public static void main(String[] args) {
          //细节 1： 有多种类型的数据混合运算时，
          //系统首先自动将所有数据转换成容量最大的那种数据类型，然后再进行计算int n1 = 10; //ok
          //float d1 = n1 + 1.1;//错误 n1 + 1.1 => 结果类型是 double
          //double d1 = n1 + 1.1;//对 n1 + 1.1 => 结果类型是 double float d1 = n1 + 1.1F;//对 n1 + 1.1 => 结果类型是 float
      
          //细节 2:  当我们把精度(容量)大 的数据类型赋值给精度(容量)小 的数据类型时，
          //就会报错，反之就会进行自动类型转换。
          //
          //int n2 = 1.1;//错误 double -> int
      
          //细节 3: (byte, short) 和 char 之间不会相互自动转换
          //当把具体数赋给 byte 时，(1)先判断该数是否在 byte 范围内，如果是就可以
          byte b1 = 10; //对	, -128-127
          // int n2 = 1; //n2 是 int
          // byte b2 = n2; //错误，原因： 如果是变量赋值,判断类型。n2在内存中有四个字节的存储空间（int），赋给两个字节的b2会精度损失的
          //
          // char c1 = b1; //错误， 原因 byte 不能自动转成 char
      
      
          //细节 4: byte，short，char	他们三者可以计算，在计算时首先转换为 int 类型
          byte b2 = 1; byte b3 = 2; short s1 = 1;
          //short s2 = b2 + s1;//错, b2 + s1 => int
          int s2 = b2 + s1;//对, b2 + s1 => int
          //byte b4 = b2 + b3; //错误: b2 + b3 => int
          //
      
          //细节 5: boolean 不参与转换
          boolean pass = true;
          //int num100 = pass;// boolean  不参与类型的自动转换
      
          //细节 6: 自动提升原则： 表达式结果的类型自动提升为 操作数中最大的类型
          //看一道题
      
          byte b4 = 1; short s3 = 100; int num200 = 1;
          float num300 = 1.1F;
      
          double num500 = b4 + s3 + num200 + num300; //对 float -> double
          }
      }
      ```



- 强制类型转换
  - 自动类型转换的逆过程，将容量大的数据类型转换为容量小的数据类型。使用时要加上强制转换符 ( )，但可能造成精度降低或溢出,格外要注意。
  - 强制类型转换细节说明
    - ![image-20210912142539871](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912142539871.png)



- 基本数据类型和String 类型的转换

  - ![image-20210912144931435](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912144931435.png)

  - ```java
    //怎么把字符串转成字符 char -> 含义是指 把字符串的第一个字符得到
    //解读	s5.charAt(0) 得到 s5 字符串的第一个字符 '1' System.out.println(s5.charAt(0));
    ```

  - 在将 String  类型转成基本数据类型时，要确保String类型能够转换成有效的数据，比如 我们可以把 "123" , 转成一个整数，但是不能把 "hello" 转成一个整数。如果格式不正确，就会抛出异常，程序就会终止， 这个问题在异常处理章节中，会处理。

### 6. 标识符的命名规则和规范

- ![image-20210912185530900](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912185530900.png)
- 标识符命名规范[更加专业]
  - 包名：多单词组成时所有字母都小写：aaa.bbb.ccc //比如 com.hsp.crm
  - 类名、接口名：多单词组成时，所有单词的首字母大写：XxxYyyZzz [大驼峰]
    比如： TankShotGame
  - 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz	[小驼峰， 简称 驼峰法]
    比如： tankShotGame
  - 常量名：所有字母都大写。多单词时每个单词用下划线连接：XXX_YYY_ZZZ 比如 ：定义一个所得税率 TAX_RATE
  - 后面我们学习到 类，包，接口，等时，我们的命名规范要这样遵守,更加详细的看文档.

## 第三章 运算符

### 1.运算符介绍

- 运算符是一种特殊的符号，用以表示数据的运算、赋值和比较等。

### 2. 算术运算符（笔试）

- ![image-20210912161349729](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912161349729.png)
- 取模 % 的本质 ：看一个公式!!!! a % b = a - a / b * b
- ![image-20210912204954290](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912204954290.png)
- 面试题![image-20210912163441761](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912163441761.png)

### 3. 关系运算符

- 关系运算符的结果都是 boolean 型，也就是要么是 true，要么是 false；
- 关系表达式 经常用在 if 结构的条件中或循环结构的条件中。

### 4. 逻辑运算符

- 用于连接多个条件（多个关系表达式），最终的结果也是一个 boolean 值。
- ![image-20210912165620826](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912165620826.png)
- 说明逻辑运算规则：
  - a&b : &  叫逻辑与：规则：当 a 和 b  同时为 true ,则结果为 true, 否则为 false （对于&逻辑与而言，如果第一个条件为 false ,后面的条件仍然会判断）
  - a&&b : && 叫短路与：规则：当 a 和 b 同时为 true ,则结果为 true,否则为 false （对于&&短路与而言，如果第一个条件为 false ,后面的条件不再判断）
    - && 和 & 使用区别
      - &&短路与：如果第一个条件为 false，则第二个条件不会判断，最终结果为 false，效率高；
      - & 逻辑与：不管第一个条件是否为 false，第二个条件都要判断，效率低；
      - 开发中， 我们使用的基本是使用短路与&&,  效率高
  - a|b : | 叫逻辑或，规则：当 a 和 b  ，有一个为 true ,则结果为 true,否则为 false
  - a||b : || 叫短路或，规则：当 a 和 b  ，有一个为 true ,则结果为 true,否则为 false
    - || 和 | 使用区别
      - ||短路或：如果第一个条件为 true，则第二个条件不会判断，最终结果为 true，效率高
      - | 逻辑或：不管第一个条件是否为 true，第二个条件都要判断，效率低
      - 开发中，我们基本使用 ||
  - !a :  叫取反，或者非运算。当 a 为 true, 则结果为 false, 当 a 为 false 是，结果为 true
  - a^b: 叫逻辑异或，当 a 和 b  不同时，则结果为 true, 否则为 false

- 经典题（注意“y=true“中的“=”）

  ![image-20210912173414826](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912173414826.png)

### 5. 赋值运算符

- 赋值运算符特点

  - 运算顺序从右往左	int	num =	a + b + c;

  - 赋值运算符的左边 只能是变量,右边 可以是变量、表达式、常量值
    int num = 20; int num2= 78 * 34 - 10; int num3 = a;

  - 复合赋值运算符等价于下面的效果比如：a+=3;等价于 a=a+3;  其他类推

  - 复合赋值运算符会进行类型转换。（重点细节）

    ```java
    byte b = 3;
    b += 2; // 等价 b = (byte)(b + 2); 这里如果写成 b = b + 2 则会报错，因为 b + 2 是int类型的了
    b++; // b = (byte)(b+1);
    ```

### 6. 三元运算符

- 基本语法

  条件表达式 ? 表达式 1: 表达式 2；

- ```java
  //三元运算符使用
  
  public class TernaryOperator {
      //编写一个 main 方法
      public static void main(String[] args) {
  
          int a = 10; int b = 99;
          // 解读
          // 1. a > b 为 false
          // 2.  返回 b--, 先返回 b 的值,然后在 b-1
          // 3. 返回的结果是 99
          int result = a > b ? a++ : b--; 
          System.out.println("result=" + result); // 99
          System.out.println("a=" + a); //要注意这里不会执行（可以理解成if-else），所以还是10
          System.out.println("b=" + b); // 98
  	}
  }
  ```

- 使用细节

  - 表达式 1 和表达式 2 要为可以赋给接收变量的类型(或可以自动转换/强转)
  - 三元运算符可以转成 if--else 语句

### 7. 运算符优先级

- 运算符有不同的优先级，所谓优先级就是表达式运算中的运算顺序。如下图，上一行运算符总优先于下一行。

- 只有单目运算符、赋值运算符是从右向左运算的。

  ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912184501081.png)

### 8. 进制

- 进制介绍

  对于整数，有四种表示方式：

  - 二进制：0,1 ，满 2 进 1.以 0b 或 0B 开头。

  - 十进制：0-9 ，满 10 进 1。
  - 八进制：0-7 ，满 8 进 1.  以数字 0 开头表示。
  - 十六进制：0-9 及 A(10)-F(15)，满 16 进 1.  以 0x 或 0X 开头表示。此处的 A-F 不区分大小写。

- 进制转换

  - 二进制转换成十进制示例

    ![image-20210912193405412](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912193405412.png)

  -  八进制转换成十进制示例

    ![image-20210912193448596](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912193448596.png)

  - 十六进制转换成十进制示例

    规则：从最低位(右边)开始，将每个位上的数提取出来，乘以 16 的(位数-1)次方，然后求和。案例：请将 0x23A 转成十进制的数
    0x23A = 10 * 16^0 + 3 * 16 ^ 1 + 2 * 16^2 = 10 + 48 + 512 = 570

  - 十进制转换成二进制

    规则：将该数不断除以 2，直到商为 0 为止，然后将每步得到的余数倒过来，就是对应的二进制。

    案例：请将 34  转成二进制	= 0B00100010

    ![image-20210912193933857](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912193933857.png)

  - 十进制转换成八进制

    规则：将该数不断除以 8，直到商为 0 为止，然后将每步得到的余数倒过来，就是对应的八进制。

    案例：请将 131  转成八进制 => 0203

    ![image-20210912194122952](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912194122952.png)

  - 十进制转换成十六进制

    规则：将该数不断除以 16，直到商为 0 为止，然后将每步得到的余数倒过来，就是对应的十六进制。

    案例：请将 237  转成十六进制 => 0xED

    ![image-20210912194223548](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912194223548.png)

  - 二进制转换成八进制

    规则：从低位开始,将二进制数每三位一组，转成对应的八进制数即可。

    案例：请将 ob11010101 转成八进制

    ob11(3)010(2)101(5)	=> 0325

  - 二进制转换成十六进制

    规则：从低位开始，将二进制数每四位一组，转成对应的十六进制数即可。

    案例：请将 ob11010101 转成十六进制

    ob1101(D)0101(5) =	0xD5

  - 八进制转换成二进制

    规则：将八进制数每 1 位，转成对应的一个 3 位的二进制数即可。
    案例：请将 0237 转成二进制
    02(010)3(011)7(111) =	0b10011111

  - 十六进制转换成二进制

    规则：将十六进制数每 1 位，转成对应的 4 位的一个二进制数即可。

    案例：请将 0x23B 转成二进制

    0x2(0010)3(0011)B(1011) =	0b001000111011

### 9. 位运算

- 二进制在运算中的说明

  ![image-20210912200940500](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912200940500.png)

- 原码、反码、补码 (重点 难点)

  ![image-20210912200956908](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912200956908.png)

  - 为什么计算机都是以补码的方式来运算的？
    - 因为补码把正数和负数统一起来了。

- 位运算符

  - java 中有 7 个位运算(&、|、^、~、>>、<<和 >>>)

    - ![image-20210912201146614](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210912201146614.png)

    - 算术右移 >>：低位溢出(就是不要),符号位不变,并用符号位补溢出的高位

    - 算术左移 <<:  符号位不变,低位补 0

      - int a=1>>2; //1 => 00000001 => 00000000 

        本质 1 /2 / 2 =0，即1/2^2^=0

      - int c=1<<2; //1 => 00000001 => 00000100 本质 1 * 2 * 2 = 4 ,即1*2^2^=4

    - \>>>逻辑右移也叫无符号右移,运算规则是: 低位溢出，高位补 0

    - 特别说明：没有 <<< 符号



## 第四章 程序控制结构

### 1. 顺序控制

![image-20210913142857587](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210913142857587.png)

### 2. 分支控制（if，else，switch）

- 嵌套分支

  在一个分支结构中又完整的嵌套了另一个完整的分支结构，里面的分支的结构称为内层分支外面的分支结构称为外层分支。老师建议: 不要超过 3 层 （可读性不好）

  ```java
  /**
   * 参加歌手比赛，如果初赛成绩大于 8.0 进入决赛，否则提示淘汰。
   * 并且根据性别提示进入男子组或女子组。 输入成绩和性别，
   * 进行判断和输出信息
   */
  import java.util.Scanner; //表示把 java.util 下的 Scanner 类导入
  public class NestedIf{
  	public static void main(String[] args) {
  		
  		System.out.println("请输入初赛成绩：");
  		Scanner myScanner = new Scanner(System.in);
  		double score = myScanner.nextDouble();
  		if(score > 8.0){
  			System.out.println("进决赛！请输入性别：");
  			char gender = myScanner.next().charAt(0); //先接收字符串，再接受字符串的第一个字符
  			if(gender == '男'){ 
  				System.out.println("进入男子组！");
  			}else{
  				System.out.println("进入女子组!");
  			}
  		}else{
  			System.out.println("淘汰!");
  		}
  		
  	}
  
  }
  ```



- switch 分支结构

  - ![image-20210913154955887](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210913154955887.png)

  - 流程图（注意如果语句块没写break，那么就会直接执行下一个语句块，不会判断条件）

    ![image-20210913155302763](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210913155302763.png)

    

  - switch 注意事项和细节讨论

    ![image-20210913160603359](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210913160603359.png)

  - 练习

    ```java
    import java.util.Scanner; //表示把 java.util 下的 Scanner 类导入
    /**
     * 1.对学生成绩大于等于 60 分的，输出"合格"。低于 60 分的，输出"不合格"。(注：输入的成绩不能大于 100),  提示 成绩/60
     * 2.根据用于指定月份，打印该月份所属的季节。3,4,5  春季 6,7,8  夏季	9,10,11 秋季 12, 1, 2 冬季 [课堂练习,  提示 使用穿透 ]
     */
    
    public class SwitchExercise{
    	public static void main(String[] args) {
            // 第1题
    		// System.out.println("Input score:");
    		// Scanner myScanner = new Scanner(System.in);
    		// double score = myScanner.nextDouble();
    		// if(score >= 0.0 && score <= 100){
    		// 	switch((int)(score/60)){
    		// 		case 0:
    		// 			System.out.println("不合格");
    		// 		case 1:
    		// 			System.out.println("合格");
    		//     }
    		// }else{
    		// 	System.out.println("输入的成绩在0-100");
    		// }
    		
            //第2题
    		System.out.println("Input month:");
    		Scanner myScanner = new Scanner(System.in);
    		int month = myScanner.nextInt();
    		switch(month){
    			case 3:
    			case 4:
    			case 5:
    				System.out.println("春季");
    				break;
    			case 6:
    			case 7:
    			case 8:
    				System.out.println("夏季");
    				break;
    			case 9:
    			case 10:
    			case 11:
    				System.out.println("秋季");
    				break;
    			case 12:
    			case 1:
    			case 2:
    				System.out.println("冬季");
    				break;
    			default:
    				System.out.println("您输入的月份不对（1-12）");
    		}
    	}
    }
    ```

    

  - switch 和 if 的比较
    - 如果判断的具体数值不多，而且符合 byte、 short 、int、 char, enum[枚举], String 这 6 种类型。虽然两个语句都可以使用，建议使用 swtich 语句；
    - 其他情况：对区间判断，对结果为 boolean 类型判断，使用 if，if 的使用范围更广。

### 3. 循环控制（for，while，dowhile，多重循环）

- for循环![image-20210913171341746](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210913171341746.png)
  - 注意事项和细节说明
    - 循环条件是返回一个布尔值的表达式
    - for(;循环判断条件;) 中的初始化和变量迭代可以写到其它地方，但是两边的分号不能省略。
      - for(;;){}   //表示一个无限循环，死循环
    - 循环初始值可以有多条初始化语句，但要求类型一样，并且中间用逗号隔开，循环变量迭代也可以有多条变量迭代语句，中间用逗号隔开。

- 两个编程思想(技巧)
  1. 化繁为简 : 即将复杂的需求，拆解成简单的需求，逐步完成	编程 = 思想 -----练习---->  代码
  2. 先死后活 : 先考虑固定的值（常量），然后转成可以灵活变化的值（用变量代替，这样即使以后常量一直变，只需改下变量就行，更加灵活，利于思考）

- while 循环控制

  ![image-20210913184003742](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210913184003742.png)

  - 注意事项和细节说明
    1. 循环条件是返回一个布尔值的表达式
    2. while 循环是先判断再执行语句

- do..while 循环控制

  - 基本语法
    循环变量初始化; 

    do{
    				循环体(语句); 

    ​				循环变量迭代;

    }while(循环条件);

  - 说明
    1. do while 是关键字
    2. 也有循环四要素, 只是位置不一样
    3. 先执行，再判断，也就是说，一定会至少执行一次
    4. 循环条件是返回一个布尔值的表达式
    5. 最后 有一个 分号 ;
    6. while 和 do..while 区别举例:  要账

  - ```java
    /**
     	*如果李三不还钱，则老韩将一直使出五连鞭，直到李三说还钱为止
     	*[System.out.println("老韩问：还钱吗？y/n")]	do...while .. 
     */
    import java.util.Scanner;
    public class DoWhileExercise{
    	public static void main(String[] args) {
    		Scanner myScanner = new Scanner(System.in);
    		char result = ' ';
    		do{
    			System.out.println("老韩问：还钱吗？y/n");
    			result = myScanner.next().charAt(0);
    		}while(result != 'y');
    		System.out.println("已还！");
    
    	}
    
    }
    ```

    

- 多重循环控制(难点! 重点!)

  1. 将一个循环放在另一个循环体内，就形成了嵌套循环。其中，for ,while ,do…while 均可以作为外层循环和内层循环。【建议一般使用两层，最多不要超过 3 层, 否则，代码的可读性很差】

  2. 实质上，嵌套循环就是把内层循环当成外层循环的循环体。当只有内层循环的循环条件为 false 时，才会完全跳出内层循环，才可结束外层的当次循环，开始下一次的循环[听不懂，走案例]。

  3. 设外层循环次数为 m 次，内层为 n 次，则内层循环体实际上需要执行 m*n 次。
  
  ```java
  /**
   * 1)统计 3 个班成绩情况，每个班有 5 名同学，
   * 求出各个班的平均分和所有班级的平均分[学生的成绩从键盘输入]。
   * 2)统计三个班及格人数，每个班有 5 名同学。
   */
  import java.util.Scanner;
  public class MulForExercise01{
  	public static void main(String[] args) {
  		Scanner myScanner = new Scanner(System.in);
  		double sum = 0.0; //一个班总分
  		double sum2 = 0.0; //三个班总分
  		double score = 0.0; // 分数
  		int eligibility = 0; //及格人数
          int classNum = 3; //班级数
          int stuNum = 5;//学生数
  		for(int j = 1;j <= classNum;j++){ //班级
  			for(int i = 1;i <= stuNUm;i++){ //学生
  				System.out.println("请输入"+j+"班第"+i+"位同学成绩：");
  				score = myScanner.nextDouble();
  				if(score >= 60){
  					eligibility++;
  				}
  				sum += score;
  			}
  			System.out.println(j+"班的平均分为" + sum/stuNum);
  			sum2 += sum;
  			sum = 0.0;
  		}
  		System.out.println("所有班级的平均分为" + sum2/(classNum * stuNum));	
  		System.out.println("三个班及格人数为" + eligibility);	
  
  	}
  }
  
  ```
  
  (一定记住要写完后，应用”先死后活“，将一些常量变量化，更灵活)

     ```java
     /**
      * 请编写一个程序，
      * 可以接收一个整数,表示层数（totalLevel），
      * 打印出金字塔。(Stars.java) [化繁为简, 先死后活]
      */
     public class Stars{
     	public static void main(String[] args) {
     		//打印金字塔一边
     		// int totalLevel = 7;//层数
     		// for(int i = 1;i <= totalLevel;i++){
     		// 	for(int j = 1;j <= i;j++){
     		// 		System.out.print("*");
     		// 	}
     		// 	System.out.println();
     		// }
     		
     		//打印实金字塔
     		// int totalLevel = 4;//层数
     		// for(int i = 1;i <= totalLevel;i++){
     		// 	for(int j = i + 1;j <= totalLevel;j++){
     		// 		System.out.print(" ");
     		// 	}
     		// 	for(int k = 1 ; k <= (2*i - 1) ; k++){
     		// 		System.out.print("*");				
     		// 	}		
     		// 	System.out.println();
     		// }
     
     		//打印空三角
     		int totalLevel = 4;//层数
     		for(int i = 1;i <= totalLevel;i++){   //控制层数
     			for(int j = i + 1;j <= totalLevel;j++){ //打印空格
     				System.out.print(" ");
     			}
     			for(int k = 1 ; k <= (2*i - 1) ; k++){ 
     				if(i == 1 || i == totalLevel){  //首行和末行打印全部星星
     					System.out.print("*");
     				}else{ //中间行打印一头一尾星星，其中打印空格
     					System.out.print("*");
     					for(int m = 1;m <= (2*i - 3);m++){
     						System.out.print(" ");
     					}
     					System.out.print("*");	
     					//k = 2*i - 1;
     					break;
     				}
     				//对于空心处理，老师的方法更好
     				// if(k == 1 || k == 2*i - 1 || i == totalLevel){
     				// 	System.out.print("*");
     				// }else{
     				// 	System.out.print(" ");
     				// }
     				
     			}		
     			System.out.println();
     		}
     
     
     	}
     
     }
     ```
  
  - 打印空心菱形
  
    ```java
    public class Stars02{
    	public static void main(String[] args) {
    		//打印空心菱形     [将菱形分上下部分]
    		int totalLevel = 12;//菱形上部分层数
    		for(int i = 1;i <= totalLevel;i++){   //控制上部分层数
    			for(int j = 1;j <= totalLevel - i;j++){ //打印前面的空格
    				System.out.print(" ");
    			}
    			for(int k = 1 ; k <= (2*i - 1) ; k++){ //打印菱形中的星星和空格
    				//对于空心处理，老师的方法更好
    				if(k == 1 || k == 2*i - 1){
    					System.out.print("*");
    				}else{
    					System.out.print(" ");
    				}
    				if(i == totalLevel && k == 2*i - 1){ //菱形下部分就打印个倒三角就行，代码和上部分差不多，只要控制循环变量初始化值或循环条件等就可以实现；
    					System.out.println();
    					for(int m = 1;m <= totalLevel - 1;m++){ //控制下部分层数
    						for(int n = 1;n <= m;n++){ //打印前面的空格
    							System.out.print(" ");
    						}
    						// 1 7  ((totalLevel-1)-m)*2+1 
    						// 2 5    （动手写下来更容易找到规律，要动手分析）
    						// 3 3
    						// 4 1
    						for(int l = 1 ; l <= (((totalLevel-1)-m)*2+1) ; l++){ //打印菱形中的星星和空格
    							if(l == 1 || l == ((totalLevel-1)-m)*2+1){
    								System.out.print("*");
    							}else{
    								System.out.print(" ");
    							}
    						}
    						System.out.println();
    					}
    				}			
    			}		
    			System.out.println();
    		}
    
    	}
    
    }
    
    ```
  
    

### 4. break

- break 语句用于终止某个语句块的执行，一般使用在 switch 或者循环[for , while , do-while]中

- 注意事项和细节说明

  ![image-20210914003320941](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210914003320941.png)

### 5. continue

- continue 语句用于结束本次循环，继续执行下一次循环。
- continue 语句出现在多层嵌套的循环语句体中时，可以通过标签指明要跳过的是哪一层循环 , 这个和前面的标签的使用的规则一样.

### 6. return

- return 使用在方法，表示跳出所在的方法，在讲解方法的时候，会详细的介绍，这里我们简单的提一下。

- 注意：如果 return 写在 main 方法，退出程序

  

## 第五章 数组、排序和查找

### 1. 数组

- 数组可以存放多个同一类型的数据。数组也是一种数据类型，是引用类型；

- 数组的使用

  - ![image-20210914182037355](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210914182037355.png)
  - - 先声明数组
      语法:数据类型 数组名[];	也可以  数据类型[] 数组名; int a[];  或者 int[] a;
    - 创建数组
      语法: 数组名=new 数据类型[大小]; 
  - 静态初始化![image-20210914184203005](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210914184203005.png)
  - 或  数据类型 数组名[] = new 数据类型[]{值1,值2,....}



- 数组使用注意事项和细节
  1. 数组是多个相同类型数据的组合，实现对这些数据的统一管理
  2. 数组中的元素可以是任何数据类型，包括基本类型和引用类型，但是不能混用。
  3. 数组创建后，如果没有赋值，有默认值
     int 0，short 0, byte 0, long 0, float 0.0,double 0.0，char \u0000，boolean false，String null
  4. 使用数组的步骤 1. 声明数组并开辟空间 2 给数组各个元素赋值 3 使用数组
  5. 数组的下标是从 0 开始的。
  6. 数组下标必须在指定范围内使用，否则报：下标越界异常，比如int [] arr=new int[5];  则有效下标为 0-4
  7. 数组属引用类型，数组型数据是对象(object) 

- 数组赋值机制 (重要)

  1. 基本数据类型赋值，这个值就是具体的数据，而且相互不影响。（值拷贝）
     int n1 = 2; int n2 = n1;

  2. 数组在默认情况下是引用传递，赋的值是地址。（地址拷贝/引用传递）

     看一个案例，并分析数组赋值的内存图(重点, 难点. )。

     //代码  int[] arr1 = {1,2,3};   int[] arr2 = arr1;（在栈中把地址复制一份，所以指向堆的数据空间是同一个）

     ![image-20210914193405097](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210914193405097.png)

- 数组添加/扩容

  ```java
  import java.util.Scanner;
  public class ArrayAdd02 {
  
      //编写一个 main 方法
      public static void main(String[] args) {
          /*
          要求：实现动态的给数组添加元素效果，实现对数组扩容。ArrayAdd.java
          1.原始数组使用静态分配 int[] arr = {1,2,3}
          2.增加的元素 4，直接放在数组的最后 arr = {1,2,3,4}
          3.用户可以通过如下方法来决定是否继续添加，添加成功，是否继续？y/n
  
          思路分析
          1. 定义初始数组 int[] arr = {1,2,3}//下标 0-2
          2.定义一个新的数组 int[] arrNew = new int[arr.length+1];
          3.遍历 arr 数组，依次将 arr 的元素拷贝到 arrNew 数组
          4.将 4 赋给 arrNew[arrNew.length - 1] = 4;把 4 赋给 arrNew 最后一个元素
          5.让 arr  指向 arrNew ;	arr = arrNew;  那么 原来 arr 数组就被销毁；（指向arrNew后，原来arr 数组指向的空间因为没有被地址引用了，就会被JVM当作垃圾销毁）
          6.创建一个 Scanner 可以接受用户输入
          7.因为用户什么时候退出，不确定，老师使用 do-while + break 来控制
          */
  
          Scanner myScanner = new Scanner(System.in);
          //初始化数组 
          int[] arr = {1,2,3};
  
          do {
              int[] arrNew = new int[arr.length + 1];
              //遍历 arr 数组，依次将 arr 的元素拷贝到 arrNew 数组
              for(int i = 0; i < arr.length; i++) { 
                  arrNew[i] = arr[i];
              }
              System.out.println("请输入你要添加的元素"); 
              int addNum = myScanner.nextInt();
              //把 addNum 赋给 arrNew 最后一个元素
              arrNew[arrNew.length - 1] = addNum;
              //让 arr 指向 arrNew, 
              arr = arrNew;
              //输出 arr 看看效果
              System.out.println("====arr 扩容后元素情况===="); 
              for(int i = 0; i < arr.length; i++) {
                  System.out.print(arr[i] + "\t");
              }
              //问用户是否继续
              System.out.println("是否继续添加 y/n"); 
              char key = myScanner.next().charAt(0); 
              if( key == 'n') { //如果输入 n ,就结束
                  break;
              }
          }while(true);
  
  
          System.out.println("你退出了添加...");
      }
  }
  ```
  
  

- 数组缩减

  ```java
  import java.util.Scanner;
  public class ArrayReduce{
  	public static void main(String[] args) {
  		Scanner myScanner = new Scanner(System.in);
  		int arr[] = {1,2,3,4,5};
  
  		do{
  			int[] arrNew = new int[arr.length - 1];
  			for(int i = 0; i < arrNew.length; i++){
  				arrNew[i] = arr[i];
  			}
  			arr = arrNew;
  			System.out.println("缩减后的数组为：");
  			for(int j = 0; j < arr.length; j++){			
  				System.out.print(arr[j] + "\t");
  			}
  			System.out.println("是否继续缩减? y/n");
  			char answer = myScanner.next().charAt(0);
  			if(answer == 'y'){
  				if(arr.length == 1){
  					System.out.println("最后一个元素,不能再缩减");
  					break;
  				}
  			}else if(answer == 'n'){
  					break;
  			}
  
  		}while(true);
  	}
  
  }
  ```

  

### 2. 排序

- 内部排序:

  指将需要处理的所有数据都加载到内部存储器中进行排序。包括(交换式排序法、选择式排序法和插入式排序法)；

- 外部排序法:

  数据量过大，无法全部加载到内存中，需要借助外部存储进行排序。包括(合并排序法和直接合并排序法)。

### 3. 查找

- 在 java 中，我们常用的查找有两种:
  1. 顺序查找 
  2. 二分查找【二分法，我们放在算法讲解】

### 4. 多维数组

- 二维数组的使用
  ```java
  public class TwoDimensionalArray01 {
  
  //编写一个 main 方法
  public static void main(String[] args) {
  
      /*
      请用二维数组输出如下图形
      0 0 0 0 0 0
      0 0 1 0 0 0
      0 2 0 3 0 0
      0 0 0 0 0 0
      */
      
      //什么是二维数组：
      //老韩解读
      //1. 从定义形式上看 int[][]
      //2. 可以这样理解，原来的一维数组的每个元素是一维数组, 就构成二维数组
      int[][] arr = { {0, 0, 0, 0, 0, 0},
                      {0, 0, 1, 0, 0, 0},
                      {0, 2, 0, 3, 0, 0},
                      {0, 0, 0, 0, 0, 0} };
  
  
      //关于二维数组的关键概念
      //(1)
      System.out.println("二维数组的元素个数=" + arr.length);
      //(2) 二维数组的每个元素是一维数组,  所以如果需要得到每个一维数组的值
      //	还需要再次遍历
      //(3) 如果我们要访问第 (i+1)个一维数组的第 j+1 个值 arr[i][j];
      //	举例 访问 3, =》 他是第 3 个一维数组的第 4 个值 arr[2][3]
      System.out.println("第 3 个一维数组的第 4 个值=" + arr[2][3]); //3
  
  
      //输出二维图形
      for(int i = 0; i < arr.length; i++) {//遍历二维数组的每个元素
          //遍历二维数组的每个元素(数组)
          //老韩解读
          //1. arr[i] 表示 二维数组的第 i+1 个元素 比如 arr[0]：二维数组的第一个元素
          //2. arr[i].length 得到 对应的 每个一维数组的长度
          for(int j = 0; j < arr[i].length; j++) {
              System.out.print(arr[i][j] + " "); //输出了一维数组
          }
          System.out.println();//换行
          }
      }
  }
  
  ```
  
- 使用方式 1: 动态初始化

  1. 语法: 类型[][] 数组名=new 类型[大小]\[大小]
  2. 比如: int a[]\[]=new int[2]\[3]

  - 二维数组在内存的存在形式  (重点！！！)

    ![image-20210914224117402](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210914224117402.png)

- 使用方式 2: 动态初始化

  先声明：类型 数组名[]\[];	

  再定义(开辟空间)  数组名 = new 类型[大小]\[大小] 

  赋值(有默认值，比如 int	类型的就是 0)

- 使用方式 3: 动态初始化-列数不确定(二维数组中每个一维数组的个数不确定)
  - 语法: 类型[][] 数组名=new 类型[大小]\[]
  - 比如: int[]\[] arr = new int[3]\[]  
    - 创建 二维数组，一共有 3 个一维数组，但是每个一维数组还没有开数据空间，需要遍历 arr 每个一维数组，给每个一维数组开空间 new，如果没有给一维数组 new ,那么 arr[i]就是 null 。

- 使用方式 4: 静态初始化

  定义 类型 数组名[][]	= {{值 1,值 2..},{值 1,值 2..},{值 1,值 2..}}

- 杨辉三角应用

  ```java
  /**
   * 使用二维数组打印一个 10 行杨辉三角
   */
  
  public class YangHui{
  	public static void main(String[] args) {
  		int[][] arr = new int[10][];  //初始化，不确定列数
  
  		for(int i = 0; i < arr.length; i++){ 
  			arr[i] = new int[i+1]; //给二维数组的元素一维数组分配空间 
  			for(int j = 0; j < arr[i].length; j++){ //赋值
  				if(j == 0 || j == arr[i].length - 1){  //找到杨辉三角规律
  					arr[i][j] = 1;
  				}else{
  					arr[i][j] = arr[i-1][j-1] + arr[i-1][j];
  				}		
  			}
  		}
  
  		for(int m = 0; m < arr.length; m++){ //输出
  			for(int n = 0; n < arr[m].length; n++){
  				System.out.print(arr[m][n] + " ");
  			}
  			System.out.println();
  		}
  	}
  }
  ```

  

- 二维数组使用细节和注意事项
  1. 一维数组的声明方式有: int[] x	或者 int x[]
  
  2. 二维数组的声明方式有:
     int[]\[] y 或者	int[] y[]	或者 int	y[]\[]
     
  3. 二维数组实际上是由多个一维数组组成的，它的各个一维数组的长度可以相同，也可以不相同。比如： map[][] 是一个二维数组
     int map[]\[] = {{1,2},{3,4,5}}
     由 map[0] 是一个含有两个元素的一维数组 ，map[1] 是一个含有三个元素的一维数组构成，我们也称为列数不等的二维数组。
     
     

## 第六章  面向对象编程(基础部分)

### 1.类与对象

- java 设计者 引入 类与对象(OOP) ，根本原因 就是现有的技术，不能完美的解决新的需求。

  ![](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915121706563.png)

- 1. 类是抽象的，概念的，代表一类事物，比如人类,猫类.., 即它是数据类型.
  2. 对象是具体的，实际的，代表一个具体事物, 即 是实例.
  3. 类是对象的模板，对象是类的一个个体，对应一个实例

- 对象在内存中存在形式    (重要的!!)

![image-20210915133647044](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915133647044.png)

- 属性/成员变量/字段
  - 从概念或叫法上看： 成员变量 = 属性 = field(字段) （即 成员变量是用来表示属性的) ;
  - 属性是类的一个组成部分，一般是基本数据类型，也可是引用类型(对象，数组)；
  - 注意事项和细节说明:
    1. 属性的定义语法同变量，示例：访问修饰符 属性类型 属性名；这里老师简单的介绍访问修饰符： 控制属性的访问范围
       有四种访问修饰符 public, proctected, 默认, private ,后面我会详细介绍
    2. 属性的定义类型可以为任意类型，包含基本类型或引用类型
    3. 属性如果不赋值，有默认值，规则和数组一致。具体说: int   0，short 0, byte 0, long 0, float 0.0, double 0.0，char  \u0000， boolean  false，String  null

- 如何创建对象

  1. 先声明再创建
     Cat cat ; //声明对象 cat cat = new Cat(); //创建

  2. 直接创建
     Cat cat = new Cat();

- 类和对象的内存分配机制  (重要)

![image-20210915141206682](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915141206682.png)

![image-20210915141215462](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915141215462.png)

Java 内存的结构分析

1. 栈： 一般存放基本数据类型(局部变量)
2. 堆： 存放对象(Cat cat ,  数组等)
3. 方法区：常量池(常量，比如字符串)， 类加载信息

Java 创建对象的流程简单分析  （重要！！！）

1. 先加载 Person 类信息 (属性和方法信息,  只会加载一次)
2. 在堆中分配空间, 进行默认初始化(看规则)
3. 把地址赋给 p , p 就指向对象
4. 进行指定初始化， 比如 p.name =”小明”	p.age = 80

### 2. 成员方法

- 基本介绍

  在某些情况下，我们要需要定义成员方法(简称方法)。比如人类:除了有一些属性外( 年龄，姓名..),我们人类还有一些行为比如:可以说话、跑步..,通过学习，还可以做算术题

- 方法的调用机制原理：(重要!-示意图!!!)

  ![image-20210915152723116](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915152723116.png)

- 成员方法的好处
  1. 提高代码的复用性
  2. 可以将实现的细节封装起来，然后供其他用户来调用即可

- 成员方法的定义

  访问修饰符 返回数据类型 方法名（形参列表..） {//方法体

  ​				语句；
  ​				return 返回值;（不是必须的）
  }

- 注意事项和使用细节
  1. 一个方法最多有一个返回值	[思考，如何返回多个结果 返回数组 ]
  2. 返回类型可以为任意类型，包含基本类型或引用类型(数组，对象)
  3. 如果方法要求有返回数据类型，则方法体中最后的执行语句必须为 return 值; 而且要求返回值类型必须和 return 的值类型一致或兼容
  4. 如果方法是 void，则方法体中可以没有 return 语句，或者 只写  return ;
  5. ![image-20210915160810954](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915160810954.png)
  6. ![image-20210915161011330](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915161011330.png)

- 练习中确实发现自己的一些错误

  - 调用方法时直接用类调用。。。。。 要注意啊 实例化对象

  - 把类写在了public类里边。。。。 定义类要写外边啊

  - ```java
    public class ClassTest{
    	public static void main(String[] args) {
    		printChar pc = new printChar();
    		pc.printCharSquare(4,4,'#');		
    	}
    }
    
    class printChar{
    
    	public void printCharSquare(int lines,int cols,char c){
    		for(int i = 0; i < lines; i++){
    			for(int j = 0; j < cols; j++){
    				System.out.print(c);
    			}
    			System.out.println();
    		}
    	}
    
    }
    
    ```

### 3. 成员方法传参机制

- 案例1：基本数据类型，传递的是值（值拷贝），形参的任何改变不影响实参！

  ![image-20210915201202963](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915201202963.png)

  

- 案例2：引用类型传递的是地址（传递也是值，但是值是地址），可以通过形参影响实参

  ![image-20210915202350415](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915202350415.png)

  ![image-20210915203028597](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915203028597.png)

### 4.方法递归调用(重难点)

- 案例（程序执行到一个方法时就会开辟一个独立的栈空间）

  ![image-20210915210508677](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915210508677.png)

- 案例2：阶乘

  ![image-20210915212740051](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915212740051.png)

- 递归重要规则

  ![image-20210915213016048](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210915213016048.png)

- 练习（斐波那契数）(猴子吃桃问题)

  ```java
  public class RecursionExercise01{
  	public static void main(String[] args) {
  			GetFib f = new GetFib();
  			int n = 2;
  			int val = f.getFib(n);
  			if(val != -1){
  				System.out.println(val);
  			}			
  	}
  }
  
  class GetFib{
  /*
  请使用递归的方式求出斐波那契数 1,1,2,3,5,8,13...给你一个整数 n，求出它的值是多思路分析
  1.当 n = 1  斐波那契数 是 1
  2.当 n = 2  斐波那契数 是 1
  3.当 n >= 3	斐波那契数 是前两个数的和
  4.这里就是一个递归的思路
  */
  	public int getFib(int n){
  		if(n >= 1){
  			if(n == 1 || n == 2){
  				return 1;
  			}else{
  				return getFib(n-1) + getFib(n-2);
  			}
  
  		}else{
  			System.out.println("请输入大于等于1的整数！！");
  			return -1;
  		}
  		
  	}
  }
  
  ```

  ```java
  public class RecursionExercise02{
  	public static void main(String[] args) {
  		Monkey m = new Monkey();
  		int days = 1;
  		int totalPeach = m.eatPeach(days);
  		if(totalPeach != -1){
  			System.out.println("第" + days + "天有" + totalPeach + "桃子");
  		}	
  	}
  }
  /*
  猴子吃桃子问题：有一堆桃子，猴子第一天吃了其中的一半，并再多吃了一个！
  以后每天猴子都吃其中的一半，然后再多吃一个。当到第 10 天时，
  想再吃时（即还没吃），发现只有 1 个桃子了。问题：最初共多少个桃子？
  10 1    要找规则、规律！！！
  9  4
  8  10
  7  22
  .  .
  .  .
   */
  class Monkey{
  	public int eatPeach(int days){  //返回每天剩余多少桃子，那第一天剩余就是总的
  		if(days == 10){
  			return 1;
  		}else if(days >= 1 && days <= 9){
  			return (eatPeach(days + 1) + 1) * 2;
  		}else{
  			System.out.println("days在1-10");
  			return -1;
  		}
  	}
  }
  ```
  
  

- 迷宫问题 （难点！！！！！！！！！）

  ```java
  public class MiGong{
  	public static void main(String[] args) {
  		int[][] map	= new int[8][7];
  		for(int i = 0; i < 7; i++){
  			map[0][i] = 1;
  			map[7][i] = 1;		
  		}	
  		for(int i = 1; i < 7; i++){
  			map[i][0] = 1;
  			map[i][6] = 1;		
  		}
  		map[3][1] = 1;
  		map[3][2] = 1;	
  		System.out.println("===初始地图===");
  		for(int i = 0; i < map.length; i++){
  			for(int j = 0; j < map[i].length; j++){
  				System.out.print(map[i][j] + " ");
  			}
  			System.out.println();
  		}
  		System.out.println("===行走路线图===");
  		Mouse m = new Mouse();
  		m.outOfMigong(map,1,1);
  		for(int i = 0; i < map.length; i++){
  			for(int j = 0; j < map[i].length; j++){
  				System.out.print(map[i][j] + " ");
  			}
  			System.out.println();
  		}
  	}
  }
  
  class Mouse{
  //使用  递归回溯  的思想来解决老鼠出迷宫
  
  //老师的解读
  //1. outOfMigong 方法就是专门来找出迷宫的路径
  //2. 如果找到，就返回 true ,否则返回 false
  //3. map 就是二维数组，即表示迷宫
  //4. i,j 就是老鼠的位置，初始化的位置为(1,1)
  //5. 因为我们是递归的找路，所以我先规定 map 数组的各个值的含义
  //	 0 表示可以走 1 表示障碍物 2 表示已走且可以走 3 表示走过，但是走不通是死路
  //6. 当 map[6][5] =2 就说明找到通路,就可以结束，否则就继续找.
  //7. 先确定老鼠找路策略 下->右->上->左
  //
  	public boolean outOfMigong(int[][] map,int i,int j){
  		if(map[6][5] == 2){
  			return true;
  		}else{
  			if(map[i][j] == 0){//当前这个位置 0,说明表示可以走
  				map[i][j] = 2;//我们假定可以走通
  				//使用找路策略，来确定该位置是否真的可以走通
  			 	if(outOfMigong(map,i+1,j)){//先走下
  			 		return  true;
  			 	}else if(outOfMigong(map,i,j+1)){//右
  			 		return  true;
  			 	}else if(outOfMigong(map,i-1,j)){
  			 		return  true;
  			 	}else if(outOfMigong(map,i,j-1)){
  			 		return  true;
  			 	}else{
  			 		map[i][j] = 3;
  					return false;	
  			 	}
  			}else{//map[i][j] = 1 , 2, 3 
  				return false;
  			}
  		}
  		
  	}
  }
  
  ```

  

### 5. 重载

- java 中允许同一个类中，多个同名方法的存在，但要求 形参列表不一致！
- 重载的好处
  1. 减轻了起名的麻烦
  2. 减轻了记名的麻烦

- 注意事项和使用细节

  ![image-20210916144558541](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916144558541.png)

  - 说明：如果 方法名和形参列表相同，单纯改变返回类型不构成重载； 如果方法名相同， 且形参列表只是改变参数名也不构成重载。

### 6. 可变参数

-  基本概念

  java 允许将同一个类中多个同名同功能但参数个数不同的方法，封装成一个方法。就可以通过可变参数实现。

- 基本语法

  访问修饰符 返回类型 方法名(数据类型...  形参名) {
  }

- 案例

  ```java
  public class VarParameter01 {
      //编写一个 main 方法
      public static void main(String[] args) {
  
  
          HspMethod m = new HspMethod(); 
          System.out.println(m.sum(1, 5, 100)); //106 
          System.out.println(m.sum(1,19)); //20
      }
  }
  class HspMethod {
      //可以计算 2 个数的和，3 个数的和 ， 4. 5， 。。
      //可以使用方法重载
      // public int sum(int n1, int n2) {//2 个数的和
      //	return n1 + n2;
      // }
      // public int sum(int n1, int n2, int n3) {//3 个数的和
      //	return n1 + n2 + n3;
      // }
      // public int sum(int n1, int n2, int n3, int n4) {//4 个数的和
      //	return n1 + n2 + n3 + n4;
      // }
      //.....
      //上面的三个方法名称相同，功能相同, 参数个数不同-> 使用可变参数优化
      //老韩解读
      //1. int... 表示接受的是可变参数，类型是 int ,即可以接收多个 int(0-多)
      //2. 使用可变参数时，可以当做数组来使用 即 nums 可以当做数组
      //3. 遍历 nums 求和即可
      public int sum(int... nums) {
      //System.out.println("接收的参数个数=" + nums.length); 
          int res = 0;
      	for(int i = 0; i < nums.length; i++) { 
              res += nums[i];
      	}
      	return res;
      }
  }
  ```

- 注意事项和使用细节

  ![image-20210916160521798](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916160521798.png)

### 7. 作用域

- 基本使用

  ![image-20210916162204255](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916162204255.png)

  (局部变量必须赋值后才能使用，因为没有默认值！)

- 注意事项和细节使用

  ![image-20210916163009673](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916163009673.png)

  ![image-20210916163015545](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916163015545.png)

  (属性生命周期较长，伴随着对象的创建而创建，伴随着对象的销毁而销毁。局部变量，生命周期较短，伴随着它的代码块的执行而创建，伴随着代码块的结束而销毁。即在一次方法调用过程中!！)

### 8. 构造器(构造方法)

- 基本介绍

  构造方法又叫构造器(constructor)，是类的一种特殊的方法，它的主要作用是 完成对新对象的初始化；

- 基本语法

  [修饰符] 方法名(形参列表){ 

  ​		方法体;
  }

- 说明
  1. 构造器的修饰符可以默认，也可以是 public protected private
  2. 构造器没有返回值
  3. 方法名 和类名字必须一样
  4. 参数列表 和 成员方法一样的规则
  5. 构造器的调用, 由系统完成
  6. 在创建对象时，系统会自动的调用该类的构造器完成对象的初始化。

- 注意事项和细节使用

  ![image-20210916170041090](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916170041090.png)

  ![image-20210916170045881](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916170045881.png)

  （javap指令能对给定的class文件提供的字节代码进行反编译！！）

- 对象创建的流程分析 （面试题）

  ![image-20210916174004418](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916174004418.png)

  ![image-20210916174039961](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916174039961.png)

### 9. this

- 什么是this

  java虚拟机会给每个对象分配 this，代表当前对象。

- 深入理解this

  案例![image-20210916180724461](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916180724461.png)

  ![image-20210916180735591](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210916180735591.png)

- this 的注意事项和使用细节

  1. this 关键字可以用来访问本类的属性、方法、构造器
  2. this 用于区分当前类的属性和局部变量
  3. 访问成员方法的语法：this.方法名(参数列表);
  4. 访问构造器语法： this(参数列表);     注意只能在构造器中使用  (即只能在构造器中访问另外一个构造器, 必须放在第一条语句)      [重要]
  5. this 不能在类定义的外部使用，只能在类定义的方法中使用。

- 练习

  ```java
  public class TestPerson{
  	public static void main(String[] args) {
  		Person p1 = new Person("jack",22);
  		Person p2 = new Person("jck",22);
  		System.out.println(p1.compareTo(p2)); 
  
  	}
  }
  
  /**
   * 定义Person 类，里面有 name、age 属性，并提供 compareTo 比较方法，用于判断是否和另一个人相等，提供测试类 TestPerson
   * 用于测试, 名字和年龄完全一样，就返回 true,  否则返回 false
   */
  class Person{
  
  	String name;
  	int age;
  
  	public Person(String name, int age){
  		this.name = name;
  		this.age = age;
  	}
  
  	public boolean compareTo(Person p){
  		// if(this.name.equals(p.name) && this.age == p.age){
  		// 	return true;
  		// }else{
  		// 	return false;
  		// }
  		return this.name.equals(p.name) && this.age == p.age;
  	}
  }
  ```

  

## 第七章 面向对象编程(中级部分)

### 1. IDEA

- ![image-20210917145013681](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917145013681.png)
- IDEA 常用快捷键
  - 删除当前行, 默认是 ctrl + Y 
  - 复制当前行,  ctrl + d
  - 补全代码	alt + /
  - 添加注释和取消注释 ctrl + /  【第一次是添加注释，第二次是取消注释】
  - 导入该行需要的类 先配置 auto import ,  然后使用 alt+enter 即可
  - 快速格式化代码 ctrl + alt + L
  - 快速运行程序 自己定义 alt + R
  - 生成构造器等 alt + insert	[提高开发效率]
  - 查看一个类的层级关系 ctrl + H	[学习继承后，非常有用]
  - 将光标放在一个方法上，输入 ctrl + B ,  可以定位到方法 [学继承后，非常有用]
  - 自动的分配变量名 ,  通过 在后面加 .var	（或alt+enter）

- 模板/自定义模板

  ![image-20210917151558001](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917151558001.png)

### 2. 包

- 包的三大作用

  ![image-20210917152200066](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917152200066.png)

- 包基本语法

  ![image-20210917152321298](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917152321298.png)

- 包的本质分析(原理)

  ![image-20210917152652998](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917152652998.png)

- 包的命名

  ![image-20210917153919005](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917153919005.png)

-  常用的包

  一个包下,包含很多的类,java 中常用的包有:

  - java.lang.*	//lang 包是基本包，默认引入，不需要再引入.
  - java.util.*	//util 包，系统提供的工具包,  工具类，使用 Scanner
  - java.net.*	//网络包，网络开发
  - java.awt.*	//是做 java 的界面开发，GUI

- 如何引入包

  老师建议：我们需要使用到哪个类，就导入哪个类即可，不建议使用 *导入

  ![image-20210917154528427](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917154528427.png)

- 注意事项和使用细节

  ![image-20210917155049634](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917155049634.png)

### 3. 访问修饰符

- 基本介绍

  java 提供四种访问控制修饰符号，用于控制方法和属性(成员变量)的访问权限（范围）:

  - 公开级别:用 public 修饰,对外公开
  - 受保护级别:用 protected 修饰,对子类和同一个包中的类公开
  - 默认级别:没有修饰符号,向同一个包的类公开.
  - 私有级别:用 private 修饰,只有类本身可以访问,不对外公开

-  4种访问修饰符的访问范围

  ![image-20210917155336039](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917155336039.png)

- 使用的注意事项

  ![image-20210917155408244](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917155408244.png)

### 4. 封装

- 封装介绍

  ![image-20210917163505692](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917163505692.png)

- 封装的理解和好处

  ![image-20210917163657194](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917163657194.png)

- 封装的实现步骤 (三步)

  ![image-20210917163807008](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917163807008.png)

- 将构造器和setXxx 结合

  - 案例

    ```java
    //有三个属性的构造器
    public Person(String name, int age, double salary) {
        //	this.name = name;
        //	this.age = age;
        //	this.salary = salary;
    	//我们可以将 set 方法写在构造器中，这样仍然可以验证
        setName(name); 
        setAge(age); 
        setSalary(salary);
    }
    ```

    

### 5. 继承

- 为什么需要继承

  ![image-20210917185503418](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917185503418.png)

- 继承基本介绍和示意图

  继承可以解决代码复用,让我们的编程更加靠近人类思维.当多个类存在相同的属性(变量)和方法时,可以从这些类中抽象出父类,在父类中定义这些相同的属性和方法，所有的子类不需要重新定义这些属性和方法，只需要通过 extends 来声明继承父类即可。画出继承的示意图:

  ![image-20210917185918303](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917185918303.png)

- 继承的基本语法

  ![image-20210917190441137](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917190441137.png)

- 继承给编程带来的便利
  - 代码的复用性提高了
  - 代码的扩展性和维护性提高了

- 继承的深入讨论/细节问题  (重要！！)
  1. 子类继承了所有的属性和方法，非私有的属性和方法可以在子类直接访问, 但是私有属性和方法不能在子类直接访问，要通过父类提供公共的方法去访问;
  2. 子类必须调用父类的构造器， 完成父类的初始化
  3. 当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用 super 去指定使用父类的哪个构造器完成对父类的初始化工作，否则，编译不会通过
  4. 如果希望指定去调用父类的某个构造器，则显式的调用一下 : super(参数列表)
  5. super 在使用时，必须放在构造器第一行 (super 只能在构造器中使用)
  6. super() 和 this() 都只能放在构造器第一行，因此这两个方法不能共存在一个构造器
  7. java 所有类都是 Object 类的子类, Object  是所有类的基类.
  8. 父类构造器的调用不限于直接父类！将一直往上追溯直到 Object 类(顶级父类)
  9. 子类最多只能继承一个父类(指直接继承)，即 java 中是单继承机制。思考：如何让 A 类继承 B 类和 C 类？ 【A 继承 B， B 继承 C】
  10. 不能滥用继承，子类和父类之间必须满足 “is-a” 的逻辑关系

- 子类创建的内存布局 （重要！！）

  ![image-20210917203907199](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917203907199.png)



### 6. Super

- 基本介绍

  super 代表父类的引用，用于访问父类的属性、方法、构造器；

- 基本语法

  ![image-20210917212219787](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917212219787.png)

- super 给编程带来的便利/细节

  ![image-20210917214258638](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917214258638.png)

  ![image-20210917214302997](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917214302997.png)

  案例：

  ```java
  package com.hspedu.super_;
  
  public class Base { //父类是 Object
  
  	public int n1 = 999; 
      public int age = 111; 
      public void cal() {
  		System.out.println("Base 类的 cal() 方法...");
  	}
  	public void eat() {
  		System.out.println("Base 类的 eat()	");
  	}
  }
  
  package com.hspedu.super_;
  
  public class A extends Base{
  	//4 个属性
  	public int n1 = 100;
      protected int n2 = 200;
      int n3 = 300;
  	private int n4 = 400;
  
      public A() {}
      public A(String name) {}
      public A(String name, int age) {}
  
      //	public void cal() {
      //	System.out.println("A 类的 cal() 方法...");
      //	}
  
      public void test100() {
      }
  
      protected void test200() {
      }
  
      void test300() {
      }
  
      private void test400() {
      }
  }
  
  
  package com.hspedu.super_;
  
  public class B extends A {
  
  
  	public int n1 = 888;
  
  
      //编写测试方法
      public void test() {
      //super 的访问不限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用 super 去访问爷爷类的成员；
      // 如果多个基类(上级类)中都有同名的成员，使用 super 访问遵循就近原则。A->B->C
  
          System.out.println("super.n1=" + super.n1); 
          super.cal();
  	}
      
      //访问父类的属性 , 但不能访问父类的 private 属性 [案例]super.属性名
      public void hi() {
      	System.out.println(super.n1 + " " + super.n2 + " " + super.n3 );
      }
      public void cal() {
      	System.out.println("B 类的 cal() 方法...");
      }
      public void sum() {
      	System.out.println("B 类的 sum()");
          //希望调用父类-A 的 cal 方法
          //这时，因为子类 B 没有 cal 方法，因此我可以使用下面三种方式
          //找 cal 方法时(cal() 和 this.cal())，顺序是:
          // (1)先找本类，如果有，则调用
          // (2)如果没有，则找父类(如果有，并可以调用，则调用)
          // (3)如果父类没有，则继续找父类的父类,整个规则，就是一样的,直到 Object 类
          // 提示：如果查找方法的过程中，找到了，但是不能访问， 则报错, cannot access
          //	如果查找方法的过程中，没有找到，则提示方法不存在
          //cal();
          this.cal(); //等价 cal
          //找 cal 方法(super.call()) 的顺序是直接查找父类（不会回子类找），其他的规则一样
          //super.cal();
  
          //演示访问属性的规则
          //n1 和 this.n1 查找的规则是
          //(1) 先找本类，如果有，则调用
          //(2) 如果没有，则找父类(如果有，并可以调用，则调用)
          //(3) 如果父类没有，则继续找父类的父类,整个规则，就是一样的,直到 Object 类
          // 提示：如果查找属性的过程中，找到了，但是不能访问， 则报错, cannot access
          //	如果查找属性的过程中，没有找到，则提示属性不存在
          System.out.println(n1); 
          System.out.println(this.n1);
          //找 n1 (super.n1) 的顺序是直接查找父类属性，其他的规则一样
          System.out.println(super.n1);
      }
      
      //访问父类的方法，不能访问父类的 private 方法 super.方法名(参数列表); 
      public void ok() {
          super.test100(); 
          super.test200(); 
          super.test300();
          //super.test400();//不能访问父类 private 方法
      }
      //访问父类的构造器(这点前面用过)：super(参数列表);只能放在构造器的第一句，只能出现一句！ 
      public	B() {
          //super();
          //super("jack", 10);
          super("jack");
      }
  }
  
  //测试类
  package com.hspedu.super_;
  
  public class Super01 {
      public static void main(String[] args) { 
          B b = new B();//子类对象
          //b.sum();
          b.test();
      }
  }
  ```

- super 和 this 的比较

  ![image-20210917215050035](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917215050035.png)

### 7. overwrite

- 基本介绍

  ![image-20210918132937111](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918132937111.png)

- 注意事项和使用细节

  ![image-20210918134827446](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918134827446.png)

- 重写和重载比较

  ![image-20210918135051164](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918135051164.png)

### 8. 多态 （重要）

- 多[多种]态[状态]基本介绍

  方法或对象具有多种形态。是面向对象的第三大特征，多态是建立在封装和继承基础之上的。

- 多态的具体体现

  - 方法的多态

    重写和重载就体现多态。

  - 对象的多态 (核心，困难，重点)

    ![image-20210918142730008](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918142730008.png)

    (3)说明：可以通过object类的getClass()来查看运行类型！
    
    ![image-20210918142737174](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918142737174.png)

- 多态注意事项和细节讨论

  - 多态的前提是：两个对象(类)存在继承关系

  - 多态的向上转型

    ![image-20210918145145996](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918145145996.png)

    向上转型调用方法的规则如下:

    - 可以调用父类中的所有成员(需遵守访问权限)
    - 但是不能调用子类的特有的成员（因为在编译阶段，能调用哪些成员,是由编译类型来决定的！！）
    - 最终运行效果看子类(运行类型)的具体实现, 即调用方法时，按照从子类(运行类型)开始查找方法，然后调用，规则和前面我们讲的方法调用规则一致。

  - 多态向下转型 (把指向子类对象的父类引用，转成指向子类对象的子类引用)

    ![image-20210918150625377](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918150625377.png)

    

  - 属性没有重写之说！属性的值看编译类型；（重要）
  - instanceOf 比较操作符，用于判断对象的运行类型是否为 XX 类型或XX 类型的子类型；（重要，==经常和向下转型一起用==）

- java 的动态绑定机制   (非常重要！！)

  ![image-20210918162301868](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918162301868.png)

- 多态的应用

  1. 多态数组

     数组的定义类型为父类类型，里面保存的实际元素类型为子类类型；

  2. 多态参数

     ![image-20210918173450561](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918173450561.png)

  

### 9. Object类详解 （面试）

1. equals 方法

   - ==和 equals 的对比    [面试题]

     ![image-20210918174038691](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918174038691.png)

     ![image-20210918175238891](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918175238891.png)
     
     ![image-20210919192412064](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210919192412064.png)

2. hashCode 方法

   ![image-20210918190739507](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918190739507.png)

   - 6 个小结：
     - 提高具有哈希结构的容器的效率！
     - 两个引用，如果指向的是同一个对象，则哈希值肯定是一样的！
     - 两个引用，如果指向的是不同对象，则哈希值是不一样的
     - 哈希值主要根据地址号来的！ 不能完全将哈希值等价于地址

3. toString 方法

   - 基本介绍
     默认返回：全类名+@+哈希值的十六进制，【查看 Object  的 toString 方法】

     ```java
     /*
     Object 的 toString() 源码
     (1)getClass().getName() 类的全类名(包名+类名 )
     (2)Integer.toHexString(hashCode()) 将对象的 hashCode 值转成 16 进制字符串
     */
     public String toString() {
     	return getClass().getName() + "@" + Integer.toHexString(hashCode());
     }
     
     ```

   - 子类往往重写 toString 方法，用于返回对象的属性信息。重写 toString 方法，打印对象或拼接对象时，都会自动调用该对象的 toString 形式.

   - 当直接输出一个对象时， toString 方法会被默认的调用, 比如 System.out.println(monster) ； 就会默认调用
     monster.toString()

4. finalize 方法 （面试！！）

   - 当对象被回收时，系统自动调用该对象的 finalize 方法（JVM只提供垃圾回收机制，具体一些释放资源的操作需要程序员对finaize方法重写来实现垃圾回收，资源释放）。子类可以重写该方法，做一些释放资源的操作；

   - 什么时候被回收：当某个对象没有任何引用时，则 jvm 就认为这个对象是一个垃圾对象，就会使用垃圾回收机制来销毁该对象，在销毁该对象前，会先调用 finalize 方法。

   - 垃圾回收机制的调用，是由系统来决定(即有自己的 GC 算法), 也可以通过 System.gc() 主动触发垃圾回收机制；
     老韩提示： 我们在实际开发中，几乎不会运用 finalize ,  所以更多就是为了应付面试. 

     ```java
     package com.hspedu.object_;
     
     //演示 Finalize 的用法
     public class Finalize_ {
     	public static void main(String[] args) {
     
     
             Car bmw = new Car("宝马");
             //这时 car 对象就是一个垃圾,垃圾回收器就会回收(销毁)对象,  在销毁对象前，会调用该对象的 finalize 方法
             //,程序员就可以在 finalize 中，写自己的业务逻辑代码(比如释放资源：数据库连接,或者打开文件..)
             //,如果程序员不重写 finalize,那么就会调用 Object 类的 finalize, 即默认处理
             //,如果程序员重写了 finalize,  就可以实现自己的逻辑
             bmw = null;
             System.gc();//主动调用垃圾回收器
     
     
             System.out.println("程序退出了	");
         }
     }
     class Car {
     	private String name;
     	//属性, 资源。。
     	public Car(String name) { 
             this.name = name;
         }
         //重写 finalize @Override
         protected void finalize() throws Throwable {
         System.out.println("我们销毁 汽车" + name );
         System.out.println("释放了某些资源	");
     
     }
     }
     ```

     

### 10. 断点调试

- ![image-20210918195248901](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918195248901.png)
- ![image-20210918195303184](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210918195303184.png)
- 小技巧
  - 将光标放在某个变量上，可以看到最新的数据。
  - 断点可以在 debug 过程中，动态的下断点

- 快捷键

  F7(跳入)	F8(跳过)	shift+F8(跳出) F9(resume,执行到下一个断点)
  F7：跳入方法内
  F8:	逐行执行代码.
  shift+F8:	跳出方法



## 第八章 房屋出租系统项目

## 第九章 面向对象编程(高级部分)

### 1. 类变量(静态变量)和类方法

- 什么是类变量

  ![image-20210920152205482](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920152205482.png)

- 如何定义类变量

  ![image-20210920152355891](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920152355891.png)

- 如何访问类变量

  ![image-20210920152432666](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920152432666.png)

  说明：类变量是随着类的加载而创建，所以即使没有创建对象实例也可以访问

- 该类变量最大的特点就是会被类的所有的对象实例共享

- 类变量内存布局

  ![img](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\wps2.png)

- 类变量使用注意事项和细节讨论

  ![image-20210920153236508](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920153236508.png)

  ![image-20210920153248228](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920153248228.png)



- 类方法基本介绍

  ![image-20210920153730271](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920153730271.png)

- 类方法的调用

  ![image-20210920153759812](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920153759812.png)

- 类方法经典的使用场景

  ![image-20210920154702825](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920154702825.png)

  如果我们希望不创建实例，也可以调用某个方法(即当做工具来使用)，这时，把方法做成静态方法时非常合适。

- 类方法使用注意事项和细节讨论

  ![image-20210920155004503](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920155004503.png)

  ![image-20210920155011048](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920155011048.png)

### 2. 理解main方法语法

- 深入理解main 方法

  ![image-20210920162320847](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920162320847.png)

- 特别提示：
  - 在 main()方法中，我们可以直接调用 main 方法所在类的静态方法或静态属性。
  - 但是，不能直接访问该类中的非静态成员，必须创建该类的一个实例对象后，才能通过这个对象去访问类中的非静态成员

- main动态传值

  ![img](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\wps8.png)

### 3. 代码块 (面试)

- 基本介绍

  ![image-20210920163347408](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920163347408.png)

- 基本语法

  ![image-20210920163446475](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920163446475.png)

- 代码块的好处

  ![image-20210920163558588](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920163558588.png)

  重要：代码块调用的顺序优先于构造器。

- 代码块使用注意事项和细节讨论 （面试）

  ![image-20210920164334269](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920164334269.png)

  ![image-20210920170632572](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920170632572.png)

  ![image-20210920171847891](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920171847891.png)

  ![image-20210920172858008](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920172858008.png)



### 4. 单例设计模式

- 什么是设计模式

  ![image-20210920184051682](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920184051682.png)

- 什么是单例模式

  ![image-20210920184140903](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920184140903.png)

- 单例模式应用实例

  ![image-20210920185429818](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920185429818.png)

```java
package com.hspedu.single_;

/**
*  演示饿漢式的單例模式
*/
public class SingleTon01 {
    public static void main(String[] args) {
    //	GirlFriend xh = new GirlFriend("小红");
    //	GirlFriend xb = new GirlFriend("小白");

    //通过方法可以获取对象
    GirlFriend instance = GirlFriend.getInstance();
    System.out.println(instance);

    GirlFriend instance2 = GirlFriend.getInstance(); 
    System.out.println(instance2);

    System.out.println(instance == instance2);//T
    //System.out.println(GirlFriend.n1);
    }
}

//有一个类， GirlFriend
//只能有一个女朋友
class GirlFriend {

    private String name;

    //public static	int n1 = 100;
    //为了能够在静态方法中，返回 gf 对象，需要将其修饰为 static
    //對象，通常是重量級的對象, 餓漢式可能造成創建了對象，但是沒有使用. 
    private static GirlFriend gf = new GirlFriend("小红红");

    //如何保障我们只能创建一个 GirlFriend  对象
    
    //步骤[单例模式-饿汉式]
    
    //1. 将构造器私有化
    //2. 在类的内部直接创建对象(该对象是 static)
    //3. 提供一个公共的 static 方法，返回 gf 对象
    private GirlFriend(String name) {
    	System.out.println("構造器被調用."); 
        this.name = name;
    }

    public static GirlFriend getInstance() { 
        return gf;
    }

    @Override
    public String toString() { 
        return "GirlFriend{" +
    		"name='" + name + '\'' + '}';
    }

}

package com.hspedu.single_;

    /**
    * 演示懶漢式的單例模式
    */
public class SingleTon02 {
    public static void main(String[] args) {
        //new Cat("大黃");
        //System.out.println(Cat.n1); 
        Cat instance = Cat.getInstance(); 
        System.out.println(instance);

        //再次調用 getInstance
        Cat instance2 = Cat.getInstance(); 
        System.out.println(instance2);

        System.out.println(instance == instance2);//T
    }
}

    //希望在程序運行過程中，只能創建一個 Cat 對象


    //使用單例模式
class Cat {
    private String name;
    public static int n1 = 999;
    private static Cat cat ; //默認是 null


    //步驟
    //1.仍然構造器私有化
    //2.定義一個 static 靜態屬性對象
    //3.提供一個 public 的 static 方法，可以返回一個 Cat 對象
    //4.懶漢式，只有當用戶使用 getInstance 時，才返回 cat 對象, 後面再次調用時，會返回上次創建的 cat 對象
    //	從而保證了單例
    private Cat(String name) {
    	System.out.println("構造器調用..."); 
        this.name = name;
    }
    public static Cat getInstance() {
    	if(cat == null) {//如果還沒有創建 cat 對象
    		cat = new Cat("小可愛");
    	}
    return cat;
    }

    @Override
    public String toString() {
    	return "Cat{" +
    		"name='" + name + '\'' + '}';
    }
}
```

- 饿汉式VS 懒汉式

  ![image-20210920192142541](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920192142541.png)



### 5. final 关键字

- 基本介绍

  ![image-20210920192804595](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920192804595.png)

- final 使用注意事项和细节讨论

  ![image-20210920194310973](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920194310973.png)

  ![image-20210920195251614](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920195251614.png)
  
  说明：第七点很细节！！ 注意！！！

### 6. 抽象类

- 抽象类快速入门

  即： 父类方法不确定性的问题
  考虑将该方法设计为抽象(abstract)方法
  所谓抽象方法就是没有实现的方法
  所谓没有实现就是指，没有方法体
  当一个类中存在抽象方法时，需要将该类声明为 abstract 类
  一般来说，抽象类会被继承，有其子类来实现抽象方法.

- 抽象类的介绍

  ![image-20210920200824090](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920200824090.png)

- 细节

  ![image-20210920200926449](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920200926449.png)

  ![image-20210920201210869](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920201210869.png)

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920201822038.png" alt="image-20210920201822038" style="zoom:150%;" />

- 抽象类最佳实践-模板设计模式

  - 基本介绍

    ![image-20210920210600676](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920210600676.png)

  - 模板设计模式能解决的问题

    ![image-20210920210629061](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920210629061.png)

### 7. 接口

- 基本介绍

  ![image-20210920212834130](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210920212834130.png)

- 注意事项和细节

  ![image-20210921150912373](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921150912373.png)

  说明：第3）点可以快捷键  alt+enter

  ![image-20210921152450589](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921152450589.png)

  - 练习

    ![image-20210921154050916](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921154050916.png)



- 实现接口 vs 继承类

  ==小结==:	当子类继承了父类，就自动的拥有父类的功能，
  如果子类需要扩展功能，可以通过实现接口的方式扩展.
  可以理解 实现接口 是 对 java  单继承机制的一种补充.

  ![image-20210921154316087](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921154316087.png)

- 接口的多态特性

  ![image-20210921155043731](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921155043731.png)

  ```java
  package com.hspedu.interface_;
  /**
  * 演示多态传递现象
  */
  public class InterfacePolyPass {
      public static void main(String[] args) {
      //接口类型的变量可以指向，实现了该接口的类的对象实例
      IG ig = new Teacher();
      //如果 IG 继承了 IH 接口，而 Teacher 类实现了 IG 接口
      //那么，实际上就相当于 Teacher 类也实现了 IH 接口.
      //这就是所谓的 接口多态传递现象. 
      IH ih = new Teacher();
      }
  }
  
  
  interface IH {
  	void hi();
  }
  interface IG extends IH{ } 
  class Teacher implements IG {
  	@Override 
      public void hi() {
  	}
  }
  ```

  

### 8. 内部类

- 基本介绍

  ![image-20210921162015111](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921162015111.png)

- 基本语法

  ![image-20210921162034387](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921162034387.png)

- 内部类的分类

  - 如果定义类在局部位置(方法中/代码块) :(1) 局部内部类(通常再方法中) (2) 匿名内部类

  - 定义在成员位置 (1) 成员内部类 (2) 静态内部类

    ![image-20210921162320260](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921162320260.png)

- 局部内部类的使用

  ![image-20210921163456233](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921163456233.png)

  ![image-20210921164059923](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921164059923.png)

  

- 匿名内部类的使用(重要!!!!!!!)

  ![image-20210921165304696](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921165304696.png)

  ```java
  package com.hspedu.innerclass;
  
  /**
  * 演示匿名内部类的使用
  */
  public class AnonymousInnerClass {
  	public static void main(String[] args) { 
          Outer04 outer04 = new Outer04(); 
          outer04.method();
  	}
  }
  
  class Outer04 { //外部类
      private int n1 = 10;//属性
      public void method() {//方法
          
          //基于接口的匿名内部类
          
          //老韩解读
          //1.需求： 想使用 IA 接口,并创建对象
          //2.传统方式，是写一个类，实现该接口，并创建对象
          //3.老韩需求是 Tiger/Dog  类只是使用一次，后面再不使用
          //4. 可以使用匿名内部类来简化开发
          //5. tiger 的编译类型 ? IA
          //6. tiger 的运行类型 ? 就是匿名内部类	Outer04$1
          /*
          我们看底层 会分配 类名 Outer04$1
          class Outer04$1 implements IA {
              @Override
              public void cry() {
                  System.out.println("老虎叫唤...");
              }
          }
          */
          //7. jdk 底层在创建匿名内部类 Outer04$1,立即马上就创建了 Outer04$1 实例，并且把地址
          //	返回给 tiger
          //8. 匿名内部类使用一次，就不能再使用
          IA tiger = new IA() { //如果用原始方法就要去建一个类去实现该接口，然后调用方法这种 硬编码 的方式；如果用匿名内部类就更加简洁灵活！！！
              @Override
              public void cry() {
              	System.out.println("老虎叫唤...");
              }
          };
          
          System.out.println("tiger 的运行类型=" + tiger.getClass()); 
          tiger.cry();
          tiger.cry();
          tiger.cry();
  
          //	IA tiger = new Tiger();
          //	tiger.cry();
  
  
      //演示基于类的匿名内部类
      //分析
      //1. father 编译类型 Father
      //2. father 运行类型 Outer04$2
      //3. 底层会创建匿名内部类
      /*
      class Outer04$2 extends Father{//所以本质上看，可以用继承思想与多态的向上转型和动态绑定理解！
          @Override
          public void test() {
         		System.out.println("匿名内部类重写了 test 方法");
          }
      }
      */
      //4. 同时也直接返回了 匿名内部类 Outer04$2 的对象
      //5. 注意("jack") 参数列表会传递给 构造器
  	Father father = new Father("jack"){
          @Override
          public void test() {
              System.out.println("匿名内部类重写了 test 方法");
          }
      };
          
      System.out.println("father 对象的运行类型=" + father.getClass());//Outer04$2 
      father.test();
  
      //基于抽象类的匿名内部类
      Animal animal = new Animal(){
          @Override
          void eat() {
          	System.out.println("小狗吃骨头...");
          }
      };
      animal.eat();
          
      }
  }
  
  
  interface IA {//接口
      public void cry();
  }
  //class Tiger implements IA {
  //
  //	@Override
  //	public void cry() {
  //	System.out.println("老虎叫唤...");
  //	}
  //}
  //class Dog implements	IA{
  //	@Override
  //	public void cry() {
  //	System.out.println("小狗汪汪...");
  //	}
  //}
  
  class Father {//类
      public Father(String name) {//构造器
      	System.out.println("接收到 name=" + name);
      }
      public void test() {//方法
      }
  }
  
  abstract class Animal { //抽象类
      abstract void eat();
  }
  
  ```

- 匿名内部类细节

  ![image-20210921232020093](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921232020093.png)

  ![image-20210921232827539](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921232827539.png)

  ![image-20210921232934926](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210921232934926.png)

- 练习

  ```java
  /*
  1.有一个铃声接口 Bell，里面有个 ring 方法。(右图)
  2.有一个手机类 Cellphone，具有闹钟功能 alarmClock，参数是 Bell 类型(右图)
  3.测试手机类的闹钟功能，通过匿名内部类(对象)作为参数，打印：懒猪起床了
  4.再传入另一个匿名内部类(对象)，打印：小伙伴上课了
  */
  
  //如果用老办法，就要建一个类去实现Bell接口，再重写方法，创对象，再cellPhone.alarmClock(该对象)；动态绑定；
  //而使用匿名内部类 直接可以作为一个对象 alarmClock(匿名内部类), 简洁灵活，太香了！
  
  package com.yt.innerclass;
  
  public class InnerClassExercise {
      public static void main(String[] args){
          CellPhone cellPhone = new CellPhone();
          cellPhone.alarmClock(new Bell() { //匿名内部类是个对象，
              // 传递的是实现了 Bell 接口的匿名内部类 InnerClassExercise$1
              @Override
              public void ring() {
                  System.out.println("懒猪起床了");
              }
          });
          cellPhone.alarmClock(new Bell() {
              @Override
              public void ring() {
                  System.out.println("小伙伴上课了");
              }
          });
      }
  }
  
  interface Bell{
      void ring();
  }
  
  class CellPhone{
      public void alarmClock(Bell bell){
          bell.ring();
      }
  }
  ```

  

- 成员内部类的使用

  ![image-20210922001400044](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922001400044.png)

  ![image-20210922001455135](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922001455135.png)

  ```java
  //外部其他类，使用成员内部类的2种方式
  // 第一种方式
  // outer08.new Inner08(); 相当于把 new Inner08()当做是 outer08 成员
  // 这就是一个语法，不要特别的纠结. 
  Outer08 outer08 = new Outer08(); 
  Outer08.Inner08 inner08 = outer08.new Inner08(); inner08.say();
  // 第二方式 在外部类中，编写一个方法getInner08Instance()，可以返回 Inner08 对象
  Outer08.Inner08 inner08Instance = outer08.getInner08Instance(); inner08Instance.say();
  ```

  

  ![image-20210922001507391](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922001507391.png)

- 静态内部类的使用

  ![image-20210922003556789](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922003556789.png)

  ![image-20210922003629470](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922003629470.png)

  ![image-20210922003659557](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922003659557.png)

  ```java
  //外部其他类 使用静态内部类
  //方式 1
  //因为静态内部类，是可以通过类名直接访问(前提是满足访问权限) 
  Outer10.Inner10 inner10 = new Outer10.Inner10();
  inner10.say();
  //方式 2
  //编写一个方法getInner10()，可以返回静态内部类的对象实例.
  Outer10 outer10 = new Outer10();
  Outer10.Inner10 inner101 = outer10.getInner10(); System.out.println("============"); inner101.say();
  //编写一个静态方法getInner10_()，可以返回静态内部类的对象实例.
  Outer10.Inner10 inner10_ = Outer10.getInner10_(); System.out.println("************"); inner10_.say();
  ```

  ![image-20210922003706240](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922003706240.png)



## 第十章 枚举与注解

### 1.枚举介绍

- 枚举对应英文(enumeration, 简写 enum)
- 枚举是一组常量的集合。
- 可以这里理解：枚举属于一种特殊的类，里面只包含一组有限的特定的对象。
- 枚举的二种实现方式
  1. 自定义类实现枚举
  2. 使用 enum 关键字实现枚举

### 2. 自定义类实现枚举

![image-20210922111728040](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922111728040.png)

- 自定义类实现枚举-小结
  - 构造器私有化
  - 本类内部创建一组对象[四个 春夏秋冬]
  - 对外暴露对象（通过为对象添加 public final static 修饰符）
  - 可以提供 get 方法，但是不要提供 set

### 3. enum关键字实现枚举

- 使用 enum 来实现枚举类
  1. 使用关键字 enum 替代 class
  2. public static final Season SPRING = new Season("春天", "温暖")   直接使用 SPRING("春天", "温暖")代替    解读： 常量名(实参列表)
  3. 如果有多个常量(对象)， 使用  ,  号间隔即可
  4. 如果使用 enum  来实现枚举，要求将定义常量对象，写在前面
  5. 如果我们使用的是无参构造器，创建常量对象，则可以省略 ()

- enum 关键字实现枚举注意事项
  1.  当我们使用enum 关键字开发一个枚举类时，默认会继承 Enum 类, 而且是一个final 类[如何证明],老师使用javap(反编译)  工具来演示.
  2. 传统的 public static final Season2 SPRING = new Season2("春天", "温暖"); 简化成 SPRING("春天", "温暖")， 这里必须知道，它调用的是哪个构造器.
  3. 如果使用无参构造器 创建 枚举对象，则实参列表和小括号都可以省略.
  4. 当有多个枚举对象时，使用 , 间隔，最后有一个分号结尾.
  5. 枚举对象必须放在枚举类的行首.
  6. 使用 enum 关键字后，就不能再继承其它类了，因为 enum 会隐式继承 Enum，而 Java 是单继承机制。 
  7. 枚举类和普通类一样，可以实现接口，如下形式。
     enum 类名 implements  接口 1，接口 2{}

- 练习 （注意返回的对象是静态的  所示是true）

  ![image-20210922134916059](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922134916059.png)

- enum 常用方法说明

  说明：使用关键字 enum 时，会隐式继承 Enum 类,  这样我们就可以使用 Enum 类相关的方法。[看下源码定义.]

  public abstract class Enum<E extends Enum<E>> implements 				Comparable<E>, Serializable {
  }

  ![image-20210922140902676](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922140902676.png)

  1. toString: Enum 类已经重写过了，返回的是当前对象名,子类可以重写该方法，用于返回对象的属性信息
  2. name：返回当前对象名（常量名），子类中不能重写
  3. ordinal：返回当前对象的位置号，默认从 0 开始
  4. values：返回当前枚举类中所有的常量(对象)
  5. valueOf：将字符串转换成枚举对象，要求字符串必须为已有的常量名，否则报异常！
  6. compareTo：比较两个枚举常量，比较的就是编号！

- 练习

  ```java
  package com.yt.enum_;
  
  /**
   * @author Yt
   * @version 1.0
   */
  public class EnumExercise {
      public static void main(String[] args){
          Week[] weeks = Week.values();
          for(Week w:weeks){  //可以用weeks.for 直接写出for循环！！
              System.out.println(w.getName());
          }
  
      }
  }
  
  enum Week{
  
      MONDAY("星期一"),TUESDAY("星期二"), WEDNESDAY("星期三"), THURSDAY("星期四"), FRIDAY("星期五"), SATURDAY("星期六"), SUNDAY("星期日");
      private String name;
  
      Week(String name) {
          this.name = name;
      }
  
      public String getName() {
          return name;
      }
  
      @Override
      public String toString() {
          return "Week{" +
                  "name='" + name + '\'' +
                  '}';
      }
  }
  ```

  

### 4. JDK内置的基本注解类型

- 注解的理解
  1. 注解(Annotation)也被称为元数据(Metadata)，用于修饰解释 包、类、方法、属性、构造器、局部变量等数据信息。
  2. 和注释一样，注解不影响程序逻辑，但注解可以被编译或运行，相当于嵌入在代码中的补充信息。
  3. 在 JavaSE 中，注解的使用目的比较简单，例如标记过时的功能，忽略警告等。在 JavaEE 中注解占据了更重要的角色，例如用来配置应用程序的任何切面，代替 java EE 旧版中所遗留的繁冗代码和 XML 配置等

- 基本的 Annotation 介绍

  使用 Annotation 时要在其前面增加 @ 符号, 并把该 Annotation 当成一个修饰符使用。用于修饰它支持的程序元素
  三个基本的 Annotation:

  1) @Override: 限定某个方法，是重写父类方法,  该注解只能用于方法（如果你写了@Override 注解，编译器就会去检查该方法是否真的重写了父类的方法，如果的确重写了，则编译通过，如果没有构成重写，则编译错误）

     看看 @Override 的定义
     //	解读： 如果发现 @interface 表示一个 注解类
     /*
     @Target(ElementType.METHOD) @Retention(RetentionPolicy.SOURCE) 

     public @interface Override {
     }
     */

     ![image-20210922145412158](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922145412158.png)

  2) @Deprecated: 用于表示某个程序元素(类,  方法等)已过时

     1. @Deprecated  修饰某个元素,  表示该元素已经过时

     2. 即不在推荐使用，但是仍然可以使用

     3. 查看 @Deprecated  注解类的源码

        /* @Documented
        @Retention(RetentionPolicy.RUNTIME)
        @Target(value={CONSTRUCTOR, FIELD, LOCAL_VARIABLE, METHOD, PACKAGE, PARAMETER, TYPE})
        public @interface Deprecated {
        }
        */ 

     4. 可以修饰方法，类，字段,  包,  参数	等等

     5. @Deprecated  可以做版本升级过渡使用

  3) @SuppressWarnings: 抑制编译器警告

     1. 当我们不希望看到这些警告的时候，可以使用 SuppressWarnings 注解来抑制警告信息

     2. 在{" "} 中，可以写入你希望抑制(不显示)警告信息

     3. 可以指定的警告类型有
        //	all，抑制所有警告
        //	boxing，抑制与封装/拆装作业相关的警告
        //	//cast，抑制与强制转型作业相关的警告
        //	//dep-ann，抑制与淘汰注释相关的警告
        //	//deprecation，抑制与淘汰的相关警告
        //	//fallthrough，抑制与 switch 陈述式中遗漏 break 相关的警告
        //	//finally，抑制与未传回 finally 区块相关的警告
        //	//hiding，抑制与隐藏变数的区域变数相关的警告
        //	//incomplete-switch，抑制与 switch 陈述式(enum case)中遗漏项目相关的警告
        //	//javadoc，抑制与 javadoc 相关的警告

        //	//nls，抑制与非 nls 字串文字相关的警告
        //	//null，抑制与空值分析相关的警告
        //	//rawtypes，抑制与使用 raw 类型相关的警告
        //	//resource，抑制与使用 Closeable 类型的资源相关的警告
        //	//restriction，抑制与使用不建议或禁止参照相关的警告
        //	//serial，抑制与可序列化的类别遗漏 serialVersionUID 栏位相关的警告
        //	//static-access，抑制与静态存取不正确相关的警告
        //	//static-method，抑制与可能宣告为 static 的方法相关的警告
        //	//super，抑制与置换方法相关但不含 super 呼叫的警告
        //	//synthetic-access，抑制与内部类别的存取未最佳化相关的警告
        //	//sync-override，抑制因为置换同步方法而遗漏同步化的警告
        //	//unchecked，抑制与未检查的作业相关的警告
        //	//unqualified-field-access，抑制与栏位存取不合格相关的警告
        //	//unused，抑制与未用的程式码及停用的程式码相关的警告

     4. 关于 SuppressWarnings 作用范围是和你放置的位置相关，比如 @SuppressWarnings 放置在 main 方法，那么抑制警告的范围就是 main，通常我们可以放置具体的语句, 方法, 类.

     5. 看看 @SuppressWarnings  源码
        (1) 放置的位置就是 TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE
        (2) 该注解类有数组 String[] values() ，设置一个数组比如 {"rawtypes", "unchecked", "unused"}
        /*
        @Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
                 @Retention(RetentionPolicy.SOURCE)

        ​          public @interface SuppressWarnings {

        ​				String[] value();

        ​	  	}
        */

        ![image-20210922151032533](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922151032533.png)

### 5. 元注解进行注释

- 元注解的基本介绍

  JDK 的元 Annotation  用于修饰其他 Annotation
  元注解： 本身作用不大，讲这个原因希望同学们，看源码时，可以知道他是干什么

- 元注解的种类 (使用不多，了解, 不用深入研究)

  1) Retention	//指定注解的作用范围，三种 SOURCE,CLASS,RUNTIME

     - 说明
       只能用于修饰一个 Annotation 定义, 用于指定该 Annotation 可以保留多长时间, @Rentention 包含一个 RetentionPolicy
       类型的成员变量, 使用 @Rentention  时必须为该 value 成员变量指定值:
       @Retention 的三种值

       1) RetentionPolicy.SOURCE: 编译器使用后，直接丢弃这种策略的注释

       2) RetentionPolicy.CLASS: 编译器将把注解记录在 class 文件中. 当运行 Java 程序时, JVM 不会保留注解。 这是默认值

       3) RetentionPolicy.RUNTIME:编译器将把注解记录在 class 文件中. 当运行 Java 程序时, JVM  会保留注解.  程序可以通过反射获取该注解

          ![image-20210922151924636](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922151924636.png)

  2) Target // 指定注解可以在哪些地方使用

     ![image-20210922152519049](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922152519049.png)

  3) Documented //指定该注解是否会在 javadoc 体现

     ![image-20210922152537115](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922152537115.png)

  4) Inherited //子类会继承父类注解



## 第十一章 异常

### 1. 异常的概念

![image-20210922190502852](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922190502852.png)

### 2. 异常体系图

- 异常体系图

  ![image-20210922192224896](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922192224896.png)

  ![image-20210922192834883](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922192834883.png)

### 3. 常见的异常

- NullPointerException 空指针异常
- ArithmeticException 数学运算异常
- ArrayIndexOutOfBoundsException 数组下标越界异常
- ClassCastException 类型转换异常
- NumberFormatException 数字格式不正确异常[]

### 4. 异常处理概念

- 异常处理的方式

  ![image-20210922195006657](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922195006657.png)

  ![image-20210922195032750](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922195032750.png)

  ![image-20210922195224706](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922195224706.png)

### 5. 异常处理分类

- try-catch 方式（ctrl + atl + t）处理异常说明

  ![image-20210922200038132](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922200038132.png)

- try-catch 方式处理异常-注意事项

  ![image-20210922200116670](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922200116670.png)

  ![image-20210922200809866](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922200809866.png)

  ![image-20210922201640222](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922201640222.png)

-  练习（注意！！）

  ![image-20210922202644386](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922202644386.png)



- throws 异常处理

  - 基本介绍

    ![image-20210922203659425](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922203659425.png)

  - 注意事项和使用细节

    ![image-20210922203748148](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922203748148.png)

### 6. 自定义异常

- 基本概念

  ![image-20210922205503482](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922205503482.png)

- 自定义异常的步骤

  ![image-20210922205929083](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922205929083.png)

  1. 一般情况下，我们自定义异常是继承 RuntimeException
  2. 即把自定义异常做成 运行时异常，好处是，我们可以使用默认的处理机制，即比较方便。

### 7. throw和throws的对比

![image-20210922210154790](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922210154790.png)



## 第十二章 常用类

### 1. 包装类（Wrapper）

- 针对八种基本数据类型相应的引用类型—包装类
  有了类的特点，就可以调用类中的方法。

  ![image-20210922214141377](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922214141377.png)

  ![image-20210922214351014](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922214351014.png)

  ![](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922214530483.png)

  ![image-20210922214545829](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210922214545829.png)

  

- 包装类和基本数据的转换 (装箱和拆箱)  (面试)

  ```java
  package com.hspedu.wrapper;
  
  /**
  *@author 韩顺平
  *@version 1.0
  */
  public class Integer01 {
      public static void main(String[] args) {
          //演示 int <--> Integer 的装箱和拆箱
          //jdk5 前是手动装箱和拆箱
          //手动装箱 int->Integer 
          int n1 = 100;
          Integer integer = new Integer(n1); 
          Integer integer1 = Integer.valueOf(n1);
  
          //手动拆箱
          //Integer -> int
          int i = integer.intValue();
  
  
          //jdk5 后，就可以自动装箱和自动拆箱
          int n2 = 200;
          //自动装箱 int->Integer
          Integer integer2 = n2; //底层使用的是 Integer.valueOf(n2)
          //自动拆箱 Integer->int
          int n3 = integer2; //底层仍然使用的是 intValue()方法
      }
  }
  ```

  

- 练习 （面试）

  ![image-20210923095831278](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923095831278.png)

  解释：第二题注意，三元运算符是一个整体，所以在运算时会提升精度，统一为Double，所以输出1.0！！

- 包装类型和String 类型的相互转换

  ```java
  public class WrapperVSString {
  public static void main(String[] args) {
      //包装类(Integer)->String 
      Integer i = 100;//自动装箱
      //方式 1
      String str1 = i + "";
      //方式 2
      String str2 = i.toString();
      //方式 3
      String str3 = String.valueOf(i);
  
  
      //String -> 包装类(Integer) 
      String str4 = "12345";
      Integer i2 = Integer.parseInt(str4);//使用到自动装箱
      Integer i3 = new Integer(str4);//构造器
  
      System.out.println("ok~~");
      }
  }
  ```

  

- Integer 类和Character 类的常用方法

  ```java
  public class WrapperMethod {
      public static void main(String[] args) { 
          System.out.println(Integer.MIN_VALUE); //返回最小值
          System.out.println(Integer.MAX_VALUE);//返回最大值
  
  
          System.out.println(Character.isDigit('a'));//判断是不是数字
          System.out.println(Character.isLetter('a'));//判断是不是字母
          System.out.println(Character.isUpperCase('a'));//判断是不是大写
          System.out.println(Character.isLowerCase('a'));//判断是不是小写
  
  
          System.out.println(Character.isWhitespace('a'));//判断是不是空格
          System.out.println(Character.toUpperCase('a'));//转成大写
          System.out.println(Character.toLowerCase('A'));//转成小写
  	}
  }
  ```

  

- Integer 类面试题

  ```java
  public class WrapperExercise02 {
      public static void main(String[] args) { 
          Integer i = new Integer(1); 
          Integer j = new Integer(1);
          System.out.println(i == j);	//False
  
          //所以，这里主要是看范围 -128 ~ 127  就是直接返回
          /*
          老韩解读
          //1. 如果 i 在 IntegerCache.low(-128)~IntegerCache.high(127),就直接从数组cache[i + (-IntegerCache.low)]返回,这个数组存放着-128~127的数。
          //2. 如果不在 -128~127,就直接 new Integer(i) 
          public static Integer valueOf(int i) {
          if (i >= IntegerCache.low && i <= IntegerCache.high) 
              return IntegerCache.cache[i + (-IntegerCache.low)];
          return new Integer(i);
          }
          */
          Integer m = 1; //底层 Integer.valueOf(1); -> 阅读源码
          Integer n = 1;// 底 层 Integer.valueOf(1); 
          System.out.println(m == n); //T
  
          //所以，这里主要是看范围 -128 ~ 127  就是直接返回
          //，否则，就 new Integer(xx);
          Integer x = 128;//底层 Integer.valueOf(128); 
          Integer y = 128;//底层 Integer.valueOf(128); 
          System.out.println(x == y);//False
     
      
          Integer i11=127; 
          int i12=127;
          //只要有基本数据类型，判断的是值是否相同   
          System.out.println(i11==i12); //T
          //只要有基本数据类型，判断的是值是否相同 
          Integer i13=128; 
          int i14=128;
          System.out.println(i13==i14);//T
  	}
  }
  ```

  

### 2. String类 （面试）

- String 类的理解和创建对象

  ![image-20210923110933700](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923110933700.png)

  ![image-20210923110950881](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923110950881.png)

  ```java
  public class String01 {
      public static void main(String[] args) {
          //1.String 对象用于保存字符串，也就是一组字符序列
          //2. "jack" 字符串常量,  双引号括起的字符序列
          //3. 字符串的字符使用 Unicode 字符编码，一个字符(不区分字母还是汉字)占两个字节
          //4. String 类有很多构造器，构造器的重载
          //	常用的有 String	s1 = new String(); 
          //String	s2 = new String(String original);
          //String	s3 = new String(char[] a);
          //String	s4 = new String(char[] a,int startIndex,int count)
          //String    s5 = new String(byte[] b)
          //5. String  类实现了接口 Serializable【String  可以串行化:可以在网络传输】
          //	          实现了接口 Comparable [String 对象可以比较大小]
          //6. String  是 final  类，不能被其他的类继承
          
          //7. String  有属性 private final char value[];  用于存放字符串内容     
          //8. 一定要注意：value 是一个 final 类型， 不可以修改(需要功力)：即 value 不能指向
          //	新的地址，但是单个字符内容是可以变化
  
          String name = "jack"; 
          name = "tom";
          
          final char[] value = {'a','b','c'};
          char[] v2 = {'t','o','m'};
          value[0] = 'H';
          //value = v2;  不可以修改 value 地址
      }
  }
  ```

  

- 创建String 对象的两种方式

  ![image-20210923124118704](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923124118704.png)

  - 两种创建String 对象的区别

    ![image-20210923124244779](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923124244779.png)

    ![image-20210923124356190](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923124356190.png)

  - 练习

    ![image-20210923130340397](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923130340397.png)

    ![image-20210923132403229](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923132403229.png)



- 字符串的特性

  ![image-20210923134434106](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923134434106.png)

  ![image-20210923134456893](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923134456893.png)

  - 面试题

    1.![image-20210923134514105](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923134514105.png)

    2.![image-20210923134529811](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923134529811.png)

    <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923134728086.png" alt="image-20210923134728086" style="zoom: 50%;" />

    3.![img](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\wps5.png)



- String 类的常见方法

  - 说明

    ![image-20210923143238811](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923143238811.png)

  - String 类的常见方法一览

    ![image-20210923143250970](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923143250970.png)

    ![image-20210923150125536](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923150125536.png)

    ```java
    // 7.compareTo 比较两个字符串的大小，如果前者大，
    // 则返回正数，后者大，则返回负数，如果相等，返回 0
    // 老韩解读
    // (1) 如果长度相同，并且每个字符也相同，就返回 0
    // (2) 如果长度相同或者不相同，但是在进行比较时，可以区分大小
    //	就返回 if (c1 != c2) {
    //			return c1 - c2;
    //		  }
    // (3) 如果前面的部分都相同，就返回 str1.len - str2.len 
    String a = "jcck";// len = 4
    String b = "jack";// len = 4
    System.out.println(a.compareTo(b)); //  返回值是 'c' - 'a' = 2 的值
    
    // 8.format 格式字符串
    /* 占位符有:
    * %s  字符串 %c 字符 %d 整型 %.2f 浮点型
    *
    */
    String name = "john"; 
    int age = 10;
    double score = 56.857;
    char gender = '男';
    //将所有的信息都拼接在一个字符串. 
    String info = "我的姓名是" + name + "年龄是" + age + ",成绩是" + score + "性别是" + gender + "。希望大家喜欢我！";
    System.out.println(info);
    
    //老韩解读
    //1. %s , %d , %.2f %c 称为占位符
    //2. 这些占位符由后面变量来替换
    //3. %s  表示后面由 字符串来替换
    //4. %d 是整数来替换
    //5. %.2f 表示使用小数来替换，替换后，只会保留小数点两位,  并且进行四舍五入的处理
    //6. %c 使用 char 类型来替换
    String formatStr = "我的姓名是%s 年龄是%d，成绩是%.2f 性别是%c.希望大家喜欢我！";
    String info2 = String.format(formatStr, name, age, score, gender);
    System.out.println("info2=" + info2);
    ```

    

### 3. StringBuffer和StringBuilder类 (面试)

- 基本介绍

  ![image-20210923151459717](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923151459717.png)

  ```java
  public class StringBuffer01 {
      public static void main(String[] args) {
      //老韩解读
      //1. StringBuffer 的直接父类 是 AbstractStringBuilder
      //2. StringBuffer 实现了 Serializable,  即 StringBuffer 的对象可以串行化
      //3. 在父类中	AbstractStringBuilder 有属性 char[] value, 不是 final
      //	该 value 数组存放 字符串内容，存放在 堆中的!!! 
      //4. StringBuffer 是一个 final 类，不能被继承
      //5. 因为 StringBuffer 字符内容是存在 char[] value, 所以在变化(增加/删除)
      //	不用每次都更换地址(即不是每次创建新对象)， 所以效率高于 String
      StringBuffer stringBuffer = new StringBuffer("hello");	
      }
  }
  ```

- String VS StringBuffer

  ![image-20210923151851429](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923151851429.png)

- StringBuffer的构造器

  ![image-20210923153018339](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923153018339.png)

- String 和 StringBuffer 相互转换

  ![image-20210923153149791](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923153149791.png)

- StringBuffer 类常见方法

  ![image-20210923154145444](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923154145444.png)

  

- 练习

  ![image-20210923160505691](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923160505691.png)



- StringBuilder 类

  - 基本介绍

    ![image-20210923163036394](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923163036394.png)

    ```java
    public class StringBuilder01 {
    	public static void main(String[] args) {
            //老韩解读
            //1. StringBuilder 继承 AbstractStringBuilder 类
            //2. 实现了 Serializable ,说明 StringBuilder 对象是可以串行化(对象可以网络传输,可以保存到文件)
            //3. StringBuilder 是 final 类,  不能被继承
            //4. StringBuilder 对象字符序列仍然是存放在其父类 AbstractStringBuilder 的 char[] value;
            //	因此，字符序列是堆中
            //5. StringBuilder 的方法，没有做互斥的处理,即没有 synchronized 关键字,因此在单线程的情况下使用
            //	StringBuilder
            StringBuilder stringBuilder = new StringBuilder();
        }
    }
    ```

    

- String、StringBuffer 和 StringBuilder 的比较

  ![image-20210923164346885](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923164346885.png)

- String、StringBuffer 和 StringBuilder 的选择

  ![image-20210923164435324](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923164435324.png)

### 4. Math类

 	Math 类包含用于执行基本数学运算的方法，如初等指数、对数、平方根和三角函数。

![image-20210923170427391](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923170427391.png)

### 5. Date日期类、Calender日历类以及新的日期

- 第一代日期类

  ![image-20210923205218898](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923205218898.png)

  ```java
  package com.hspedu.date_;
  
  import java.text.ParseException; 
  import java.text.SimpleDateFormat; 
  import java.util.Date;
  
  public class Date01 {
      public static void main(String[] args) throws ParseException {
          //老韩解读
          //1. 获取当前系统时间
          //2. 这里的 Date 类是在 java.util 包
          //3. 默认输出的日期格式是国外的方式, 因此通常需要对格式进行转换
          Date d1 = new Date(); //获取当前系统时间
          System.out.println("当前日期=" + d1);
          
          Date d2 = new Date(9234567); //通过指定毫秒数得到时间
          System.out.println("d2=" + d2); //获取某个时间对应的毫秒数
       
          //老韩解读
          //1. 创建 SimpleDateFormat 对象，可以指定相应的格式
          //2. 这里的格式使用的字母是规定好，不能乱写
  
          SimpleDateFormat sdf = new SimpleDateFormat("yyyy 年 MM 月 dd 日 hh:mm:ss E");
          String format = sdf.format(d1); // format:将日期转换成指定格式的字符串
          System.out.println("当前日期=" + format);
  
          //老韩解读
          //1. 可以把一个格式化的 String  转成对应的 Date
          //2. 得到 Date 仍然在输出时，还是按照国外的形式，如果希望指定格式输出，需要转换
          //3. 在把 String -> Date ， 使用的 sdf 格式需要和你给的 String 的格式一样，否则会抛出 转换异常
          String s = "1996 年 01 月 01 日 10:20:30  星期一"; 
          Date parse = sdf.parse(s); 
          System.out.println("parse=" + sdf.format(parse));
  	}
  }
  ```

- 第二代日期类

  ![image-20210923210959503](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923210959503.png)

  ```java
  package com.hspedu.date_;
  import java.util.Calendar;
  
  public class Calendar_ {
      public static void main(String[] args) {
          //老韩解读
          //1. Calendar 是一个抽象类， 并且构造器是 private
          //2. 可以通过 getInstance() 来获取实例
          //3. 提供大量的 方法 和 字段 提供给程序员
          //4. Calendar 没有提供对应的格式化的类，因此需要程序员自己组合来输出 (灵活)
          //5. 如果我们需要按照 24 小时进制来获取时间， Calendar.HOUR ==改成=> Calendar.HOUR_OF_DAY 
          Calendar c = Calendar.getInstance(); //创建日历类对象//比较简单，自由
          System.out.println("c=" + c);
          //获取日历对象的某个日历字段
          System.out.println("年：" + c.get(Calendar.YEAR));
          // 这里为什么要 + 1,  因为 Calendar 返回月时候，是按照 0  开始编号
          System.out.println("月：" + (c.get(Calendar.MONTH) + 1));
          System.out.println("日：" + c.get(Calendar.DAY_OF_MONTH));
          System.out.println("小时：" + c.get(Calendar.HOUR));
          System.out.println("分钟：" + c.get(Calendar.MINUTE));
          System.out.println("秒：" + c.get(Calendar.SECOND));
          //Calender 没有专门的格式化方法，所以需要程序员自己来组合显示
          System.out.println(c.get(Calendar.YEAR)	+	"-"	+	(c.get(Calendar.MONTH)	+	1)	+	"-"	+ c.get(Calendar.DAY_OF_MONTH) + " " + c.get(Calendar.HOUR_OF_DAY) + ":" + c.get(Calendar.MINUTE) + ":" + c.get(Calendar.SECOND) );
  
      }
  }
  ```
  
  

- 第三代日期类

  ![image-20210923212716736](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923212716736.png)

  ![image-20210923212724968](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923212724968.png)

  - DateTimeFormatter 格式日期类

    ![image-20210923214451430](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923214451430.png)

  ```java
  package com.hspedu.date_;
  
  import java.time.Instant; 
  import java.time.LocalDate;
  import java.time.LocalDateTime; 
  import java.time.LocalTime;
  import java.time.format.DateTimeFormatter;
  import java.util.ArrayList;
  import java.util.Collection;
  
  public class LocalDate_ {
      public static void main(String[] args) {
          //第三代日期
          //老韩解读
          //1. 使用 now() 返回表示当前日期时间的 对象
          LocalDateTime ldt = LocalDateTime.now(); 
          //LocalDate.now();
          //LocalTime.now(); 		
          System.out.println(ldt);
  
          //2. 使用 DateTimeFormatter 对象来进行格式化
          // 创建 DateTimeFormatter 对象
          DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss"); 	
          String format = dateTimeFormatter.format(ldt);
          System.out.println("格式化的日期=" + format);
  
          System.out.println("年=" + ldt.getYear());
          System.out.println("月=" + ldt.getMonth());
          System.out.println("月=" + ldt.getMonthValue());
          System.out.println("日=" + ldt.getDayOfMonth());
          System.out.println("时=" + ldt.getHour());
          System.out.println("分=" + ldt.getMinute());
          System.out.println("秒=" + ldt.getSecond());
  
          LocalDate now = LocalDate.now(); //可以获取年月日
          LocalTime now2 = LocalTime.now();//获取到时分秒
  
          //提供 plus  和 minus 方法可以对当前时间进行加或者减
          //看看 890 天后，是什么时候 把 年月日-时分秒
          LocalDateTime localDateTime = ldt.plusDays(890);
          System.out.println("890 天后=" + dateTimeFormatter.format(localDateTime));
  
          //看看在 3456 分钟前是什么时候，把 年月日-时分秒输出
          LocalDateTime localDateTime2 = ldt.minusMinutes(3456);
          System.out.println("3456 分钟前 日期=" + dateTimeFormatter.format(localDateTime2));
      }
  } 
  ```

  

- Instant 时间戳

  ![image-20210923214546140](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923214546140.png)

  ```java
  package com.hspedu.date_;
  
  import java.time.Instant;
  import java.util.Date;
  
  public class Instant_ {
      public static void main(String[] args) {
  
          //1.通过 静态方法 now() 获取表示当前时间戳的对象
          Instant now = Instant.now(); 
          System.out.println(now);
          //2. 通过 from  可以把 Instant 转成 Date
          Date date = Date.from(now);
          //3. 通过 date 的 toInstant() 可以把 date 转成 Instant 对象
          Instant instant = date.toInstant();
      }
  }
  ```

  



### 6. System类

- System 类常见方法和案例

  ![image-20210923202338611](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923202338611.png)

  ```java
  (2)arraycopy
  //1. 主要是搞清楚这五个参数的含义
  //2.
  //	源数组
  //	* @param	src	the source array.
  //	srcPos： 从源数组的哪个索引位置开始拷贝
  //	* @param	srcPos	starting position in the source array.
  //	dest :  目标数组，即把源数组的数据拷贝到哪个数组
  //	* @param	dest	the destination array.
  //	destPos: 把源数组的数据拷贝到 目标数组的哪个索引
  //	* @param	destPos	starting position in the destination data.
  //	length: 从源数组拷贝多少个数据到目标数组
  //	* @param	length	the number of array elements to be copied.
  ```

  

### 7. Arrays类

- Arrays 类常见方法应用案例

  ![image-20210923182144590](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923182144590.png)

  ![image-20210923182201843](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923182201843.png)

  ```java
  package com.hspedu.arrays_;
  
  import java.util.Arrays; 
  import java.util.Comparator;
  
  public class ArraysMethod01 {
      public static void main(String[] args) {
  
          Integer[] integers = {1, 20, 90};
          //遍历数组
          //	for(int i = 0; i < integers.length; i++) {
          //		System.out.println(integers[i]);
          //	}
          
          //(一)直接使用 Arrays.toString 方法，显示数组
          
          System.out.println(Arrays.toString(integers));
  
          
          
          //(二)演示 sort 方法的使用
          
          Integer arr[] = {1, -1, 7, 0, 89};
          //进行排序
          //老韩解读
          //1. 可以直接使用冒泡排序 ,  也可以直接使用 Arrays 提供的 sort 方法排序
          //2. 因为数组是引用类型，所以通过 sort 排序后，会直接影响到 实参 arr
          //3. sort 重载的，也可以通过传入一个接口 Comparator 实现定制排序
          //4. 调用 定制排序 时，传入两个参数 (1) 排序的数组 arr
          //	(2)  实现了 Comparator 接口的匿名内部类 ,  要求实现	compare 方法
          //5. 先演示效果，再解释
          //6. 这里体现了接口编程的方式 , 看看源码，就明白
          //	源码分析
          //(1) Arrays.sort(arr, new Comparator()
          //(2) 最终到 TimSort 类的 private static <T> void binarySort(T[] a, int lo, int hi, int start,
          //	Comparator<? super T> c)()
          //(3) 执行到 binarySort 方法的代码,  会根据动态绑定机制 c.compare()执行我们传入的
          //	匿名内部类的 compare ()
          //	while (left < right) {
          //		int mid = (left + right) >>> 1;
          //		if (c.compare(pivot, a[mid]) < 0)
          //			right = mid;
          //		else
          //			left = mid + 1;
          //	}
          //(4) new Comparator() {
          //		@Override
          //		public int compare(Object o1, Object o2) {
          //			Integer i1 = (Integer) o1;
          //			Integer i2 = (Integer) o2;
          //			return i2 - i1;
          //		}
          //	}
          //(5) public int compare(Object o1, Object o2) 返回的值>0 还是 <0
          //	会影响整个排序结果, 这就充分体现了 接口编程+动态绑定+匿名内部类的综合使用
          //	将来的底层框架和源码的使用方式，会非常常见
          
          //Arrays.sort(arr); // 默认排序方法
          
          //定制排序
          Arrays.sort(arr, new Comparator() {
              @Override
          	public int compare(Object o1, Object o2) { 
                  Integer i1 = (Integer) o1;
          		Integer i2 = (Integer) o2; 
                  return i2 - i1;
         		}
          });
          System.out.println("===排序后==="); 
          System.out.println(Arrays.toString(arr));
      }
  }
  
  ==================================================================================================
  
  package com.hspedu.arrays_;
  
  import java.util.Arrays; 
  import java.util.Comparator;
  
  public class ArraysSortCustom {
  	public static void main(String[] args) {
  
          int[] arr = {1, -1, 8, 0, 20};
          //bubble01(arr);
  
          bubble02(arr, new Comparator() { 
              @Override
          	public int compare(Object o1, Object o2) {
                  int i1 = (Integer) o1;
          		int i2 = (Integer) o2;
          		return i2 - i1;// return i2 - i1;
  			}
  		});
  
  
  		System.out.println("==定制排序后的情况=="); 
          System.out.println(Arrays.toString(arr));
  	}
  
      //使用冒泡完成排序
      public static void bubble01(int[] arr) { 
          int temp = 0;
          for (int i = 0; i < arr.length - 1; i++) {
              for (int j = 0; j < arr.length - 1 - i; j++) {
                  //从小到大
                  if (arr[j] > arr[j + 1]) {
                      temp = arr[j]; 
                      arr[j] = arr[j + 1]; 
                      arr[j + 1] = temp;
                  }
              }
          }
      }
  
  
  	//结合冒泡 + 定制
  	public static void bubble02(int[] arr, Comparator c) { 
          int temp = 0;
  		for (int i = 0; i < arr.length - 1; i++) {
  			for (int j = 0; j < arr.length - 1 - i; j++) {
  			//数组排序由 c.compare(arr[j], arr[j + 1])返回的值决定
                  if (c.compare(arr[j], arr[j + 1]) > 0) {
  					temp = arr[j]; 
                      arr[j] = arr[j + 1]; 
                      arr[j + 1] = temp;
  				}
  			}
  		}
  	}
      
  }
  
  ===============================================================================================
  
  package com.hspedu.arrays_;
  import java.util.Arrays; 
  import java.util.List;
  
  public class ArraysMethod02 {
  	public static void main(String[] args) { 
          Integer[] arr = {1, 2, 90, 123, 567};
  		// (三)binarySearch 通过二分搜索法进行查找，要求必须排好
          // 老韩解读
          //1. 使用 binarySearch 二叉查找
          //2. 要求该数组是有序的.  如果该数组是无序的，不能使用 binarySearch
          //3. 如果数组中不存在该元素，就返回 return -(low + 1);	// key not found. 
          int index = Arrays.binarySearch(arr, 567);
          System.out.println("index=" + index);
  
  
          //(四)copyOf 数组元素的复制
          // 老韩解读
          //1. 从 arr 数组中，拷贝 arr.length 个元素到 newArr 数组中
          //2. 如果拷贝的长度 > arr.length 就在新数组的后面 增加 null
          //3. 如果拷贝长度 < 0 就抛出异常 NegativeArraySizeException
          //4. 该方法的底层使用的是 System.arraycopy() 
          Integer[] newArr = Arrays.copyOf(arr, arr.length);
          System.out.println("==拷贝执行完毕后==");
          System.out.println(Arrays.toString(newArr));
  
  
          //()fill 数组元素的填充
          Integer[] num = new Integer[]{9,3,2};
          //老韩解读
          //1. 使用 99 去填充 num 数组，可以理解成是 替换 原来的元素
          Arrays.fill(num, 99);
          System.out.println("==num 数组填充后=="); 
          System.out.println(Arrays.toString(num));
  
          //(六)equals 比较两个数组元素内容是否完全一致
          Integer[] arr2 = {1, 2, 90, 123};
          //老韩解读
          //1. 如果 arr 和 arr2 数组的元素一样，则方法 true;
          //2. 如果不是完全一样，就返回 false 
          boolean equals = Arrays.equals(arr, arr2); 
          System.out.println("equals=" + equals);
  
          //(七)asList 将一组值，转换成 list
          //老韩解读
          //1. asList 方法，会将 (2,3,4,5,6,1)数据转成一个 List 集合
          //2. 返回的 asList  编译类型 List(接口)
          //3. asList  运行类型 java.util.Arrays$ArrayList, 是 Arrays 类的
          //	静态内部类 private static class ArrayList<E> extends AbstractList<E>
          //	implements RandomAccess, java.io.Serializable 
          List asList = Arrays.asList(2,3,4,5,6,1);
          System.out.println("asList=" + asList);
          System.out.println("asList 的运行类型" + asList.getClass());
  
      }
  }
  ```

  

### 8. BigInteger类和BIgDecimal类

- ![image-20210923203055822](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923203055822.png)

- BigInteger 和BigDecimal 常见方法

  ![image-20210923203647461](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210923203647461.png)

  - BigInteger 
    1. 在对 BigInteger 进行加减乘除的时候，需要使用对应的方法，不能直接进行 + - * /
    2. 可以创建一个 要操作的 BigInteger 然后进行相应操作
    3. BigInteger 底层是将数据当成字符串，再将其转成BigInteger 

  - BigDecimal 

    1. 如果对 BigDecimal 进行运算，比如加减乘除，需要使用对应的方法

    2. 创建一个需要操作的 BigDecimal 然后调用相应的方法即可

    3. 除法注意，可能抛出异常 ArithmeticException

       ```java
       //System.out.println(bigDecimal.divide(bigDecimal2));//可能抛出异常 ArithmeticException
       //在调用 divide 方法时，指定精度即可. BigDecimal.ROUND_CEILING
       //如果有无限循环小数，就会保留 分子 的精度
       System.out.println(bigDecimal.divide(bigDecimal2, BigDecimal.ROUND_CEILING));
       ```

       

## 第十三章 集合(面试)

### 1. 集合框架体系

- 集合

  ![image-20210924165512532](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924165512532.png)

- 集合的框架体系

  Java 的集合类很多，主要分为两大类：

  - ![image-20210924170417392](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924170417392.png)
  - ![image-20210924170434797](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924170434797.png)

  ```java
  package com.hspedu.collection_;
  
  import java.util.ArrayList; 
  import java.util.Collection; 
  import java.util.HashMap; 
  import java.util.Map;
  
  public class Collection_ { @SuppressWarnings({"all"})
      public static void main(String[] args) {
          //老韩解读
          //1. 集合主要是两组(单列集合 , 双列集合)
          //2. Collection  接口有两个重要的子接口 List Set ,  他们的实现子类都是单列集合
          //3. Map 接口的实现子类 是双列集合，存放的 Key-Value
          //4. 把老师梳理的两张图记住
          //Collection
          //Map
          ArrayList arrayList = new ArrayList(); 
          arrayList.add("jack"); 
          arrayList.add("tom");
  
          HashMap hashMap = new HashMap(); 
          hashMap.put("NO1", "北京");
          hashMap.put("NO2", "上海");
      }
  }
  ```

  



### 2. Collection

#### 1. Collection 接口和常用方法

- Collection 接口实现类的特点

  ![image-20210924183136848](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924183136848.png)

- Collection 接口常用方法,以实现子类 ArrayList 来演示

  ![image-20210924183454050](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924183454050.png)

- Collection 接口遍历元素方式 1-使用Iterator(迭代器)

  ![image-20210924190241109](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924190241109.png)

  ![image-20210924190604159](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924190604159.png)

  ![image-20210924190650649](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924190650649.png)

  ```java
  package com.hspedu.collection_;
  
  import java.util.ArrayList;
  import java.util.Collection;
  import java.util.Iterator;
  
  public class CollectionIterator {
      @SuppressWarnings({"all"})
      public static void main(String[] args) {
  
          Collection col = new ArrayList();
  
          col.add(new Book("三国演义", "罗贯中", 10.1));
          col.add(new Book("小李飞刀", "古龙", 5.1));
          col.add(new Book("红楼梦", "曹雪芹", 34.6));
  
          //System.out.println("col=" + col);
          //现在老师希望能够遍历 col 集合
          //1. 先得到 col  对应的 迭代器
          Iterator iterator = col.iterator();
          //2. 使用 while 循环遍历
          //	while (iterator.hasNext()) {//判断是否还有数据
          //	//返回下一个元素，类型是 Object
          //	Object obj = iterator.next();
          //	System.out.println("obj=" + obj);
          //	}
          //老师教大家一个快捷键，快速生成 while =>  itit
          //显示所有的快捷键的的快捷键   ctrl + j 
          while (iterator.hasNext()) {
              Object obj = iterator.next();
              System.out.println("obj=" + obj);
          }
          //3. 当退出 while 循环后 ,  这时 iterator 迭代器，指向最后的元素
          //	iterator.next(); //NoSuchElementException
          //4. 如果希望再次遍历，需要重置我们的迭代器
          iterator = col.iterator();
          System.out.println("===第二次遍历==="); 
          while (iterator.hasNext()) {
              Object obj = iterator.next(); 
              System.out.println("obj=" + obj);
          }
      }
  }
  
  class Book {
  	private String name; 
      private String author; 
      private double price;
  
      public Book(String name, String author, double price) {
          this.name = name;
      	this.author = author; 
          this.price = price;
      }
      public String getName() { 
          return name;
      }
  
  
      public void setName(String name) {
          this.name = name;
      }
  
  
      public String getAuthor() { 
          return author;
      }
  
  
      public void setAuthor(String author) {
          this.author = author;
      }
  
  
      public double getPrice() { 
          return price;
      }
  
  
      public void setPrice(double price) { 
          this.price = price;
      }
  
  
      @Override
      public String toString() {
          return "Book{" +
          "name='" + name + '\'' +
          ", author='" + author + '\'' + ", price=" + price +
          '}';
      }
  }
  ```

  

- Collection 接口遍历对象方式 2-for 循环增强

  ![image-20210924191209483](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924191209483.png)

  ```java
  package com.yt.collection_;
  
  import java.util.ArrayList;
  import java.util.Collection;
  
  public class CollectionFor {
      @SuppressWarnings({"all"})
      public static void main(String[] args) {
  
          Collection col = new ArrayList();
  
          col.add(new Book("三国演义", "罗贯中", 10.1));
          col.add(new Book("小李飞刀", "古龙", 5.1));
          col.add(new Book("红楼梦", "曹雪芹", 34.6));
  
  
          //1.使用增强for，在Collection集合
          //2.增强for底层仍然是迭代器
          //3.可以理解成就是简化版本的 迭代器遍历
          //4.快捷方式 I 或 col.for
  
          for (Object book :col) {
              System.out.println(book);
          }
  
          //增强for，也可以直接在数组使用
  
      }
  }
  calss Book{}...
  ```

  

#### 2. List 接口和常用方法

- ![image-20210924194833960](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924194833960.png)

- List 接口的常用方法

  ```java
  package com.hspedu.list_;
  
  import java.util.ArrayList; 
  import java.util.List;
  
  public class ListMethod { @SuppressWarnings({"all"})
      public static void main(String[] args) { 
          List list = new ArrayList();
      	list.add("张三丰");
      	list.add("贾宝玉");
      	//	void add(int index, Object ele):在 index 位置插入 ele 元素
      	//在 index = 1 的位置插入一个对象
          list.add(1, " 韩 顺 平 "); 
          System.out.println("list=" + list);
          //	boolean addAll(int index, Collection eles):从 index 位置开始将 eles 中的所有元素添加进来
          List list2 = new ArrayList(); 
          list2.add("jack");
          list2.add("tom"); 
          list.addAll(1, list2);
          System.out.println("list=" + list);
          //	Object get(int index):获取指定 index 位置的元素
          //说过
          //	int indexOf(Object obj):返回 obj 在集合中首次出现的位置
          System.out.println(list.indexOf("tom"));//2
          //	int lastIndexOf(Object obj):返回 obj 在当前集合中末次出现的位置
          list.add(" 韩 顺 平 "); 
          System.out.println("list=" + list);
          System.out.println(list.lastIndexOf("韩顺平"));
          //	Object remove(int index):移除指定 index 位置的元素，并返回此元素
          list.remove(0); 
          System.out.println("list=" + list);
          //	Object set(int index, Object ele):设置指定 index 位置的元素为 ele ,  相当于是替换.
          list.set(1, " 玛 丽 "); 
          System.out.println("list=" + list);
          //	List subList(int fromIndex, int toIndex):返回从 fromIndex 到 toIndex 位置的子集合
          // 注意返回的子集合 fromIndex <= subList < toIndex
          List returnlist = list.subList(0, 2); 
          System.out.println("returnlist=" + returnlist);  
      }
  }
  ```

  

- List 的三种遍历方式 [ArrayList, LinkedList,Vector]

  ![image-20210924200923989](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924200923989.png)



#### 3. ArrayList 底层结构和源码分析

- ArrayList 的注意事项

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924202754947.png" alt="image-20210924202754947" style="zoom:150%;" />

- ArrayList 的底层操作机制源码分析(重点，难点.)

  ![image-20210924202818228](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924202818228.png)

  ```java
  package com.hspedu.list_;
  
  import java.util.ArrayList;
  
      @SuppressWarnings({"all"})
      public class ArrayListSource {
      public static void main(String[] args) {
          //老韩解读源码
          //注意，注意，注意，Idea 默认情况下，Debug 显示的数据是简化后的，如果希望看到完整的数据
          //需要做设置.
          //使用无参构造器创建 ArrayList 对象
          ArrayList list = new ArrayList(); 
          //ArrayList list = new ArrayList(8);
          //使用 for 给 list 集合添加 1-10 数据
          for (int i = 1; i <= 10; i++) { 
              list.add(i);
          }
          //使用 for 给 list 集合添加 11-15 数据
          for (int i = 11; i <= 15; i++) { 
              list.add(i);
          }
          list.add(100);
          list.add(200); 
          list.add(null);
  
      }
  }
  ```

  示意图:

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924212913848.png" alt="image-20210924212913848"  />

  ![image-20210924212926036](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924212926036.png)

  

#### 4. Vector 底层结构和源码剖析 

- Vector 的基本介绍

  ![image-20210924223340978](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924223340978.png)

- Vector 和ArrayList 的比较

  ![image-20210924231125914](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924231125914.png)

- Vector 源码剖析

```java
package com.hspedu.list_;

import java.util.Vector;

@SuppressWarnings({"all"})
public class Vector_ {
    public static void main(String[] args) {
        //无参构造器
        //有参数的构造
        Vector vector = new Vector(8); 
        for (int i = 0; i < 10; i++) {
        	vector.add(i);
        }
        vector.add(100); 
        System.out.println("vector=" + vector);
        //老韩解读源码
        //1. new Vector() 底层
        /*
        public Vector() {
        	this(10);
        }
        补充：如果是	Vector vector = new Vector(8);
        走的方法:
        public Vector(int initialCapacity) {
        	this(initialCapacity, 0);
        }
        
        2.vector.add(i)
        2.1//下面这个方法就添加数据到 vector 集合
        public synchronized boolean add(E e) { 
            modCount++; 
            ensureCapacityHelper(elementCount + 1); //每次加 都要进去判断一下是否扩容
            elementData[elementCount++] = e;
            return true;
        }
        2.2//确定是否需要扩容 条件 ： minCapacity - elementData.length>0 
        private void ensureCapacityHelper(int minCapacity) {
            // overflow-conscious code
            if (minCapacity - elementData.length > 0)
            	grow(minCapacity); // 如要扩容 就走这个方法
        }
        2.3 //如果 需要的数组大小 不够用，就扩容 , 扩容的算法
        //newCapacity = oldCapacity + ((capacityIncrement > 0) ?
        //		capacityIncrement : oldCapacity);
        //capacityIncrement默认为0，有个构造方法可以自定义扩容增量，传入参数，大于0就返回capacityIncrement；这里 0 > 0,返回 oldCapacity，就是扩容两倍！
        
        private void grow(int minCapacity) {
            // overflow-conscious code
            int oldCapacity = elementData.length;
            int newCapacity = oldCapacity + ((capacityIncrement > 0) ?
            capacityIncrement : oldCapacity);
            if (newCapacity - minCapacity < 0) newCapacity = minCapacity;
            if (newCapacity - MAX_ARRAY_SIZE > 0) newCapacity = hugeCapacity(minCapacity);
            elementData = Arrays.copyOf(elementData, newCapacity);
        }        */

    }
}
```



#### 5. LinkedList 底层结构

- LinkedList 的全面说明

  ![image-20210924234727592](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924234727592.png)

- LinkedList 的底层操作机制

  ![image-20210924234804927](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210924234804927.png)

  ```java
  public class LinkedList01 {
      public static void main(String[] args) {
      //模拟一个简单的双向链表
  
      	Node jack = new Node("jack");
          Node tom = new Node("tom"); 
          Node hsp = new Node("老韩");
  
          //连接三个结点，形成双向链表
          //jack -> tom -> hsp 
          jack.next = tom; 
          tom.next = hsp;
          //hsp -> tom -> jack
          hsp.pre = tom; 
          tom.pre = jack;
  
          Node first = jack;//让 first 引用指向 jack (把jack对象的地址给first),就是双向链表的头结点
          Node last = hsp; //让 last 引用指向 hsp,就是双向链表的尾结点
  
          //演示，从头到尾进行遍历
          System.out.println("===从头到尾进行遍历===");
          while (true) {
          	if(first == null) { 
                  break;
          	}
          //输出 first  信息
              System.out.println(first); 
              first = first.next;
          }
  
          //演示，从尾到头的遍历
          System.out.println("====从尾到头的遍历===="); 
          while (true) {
          	if(last == null) {
                  break;
          	}
          //输出 last  信息
              System.out.println(last);
              last = last.pre;
          }
  
          //演示链表的添加对象/数据，是多么的方便
          //要求，是在 tom --------- 老韩 之间，插入一个对象 smith
  
  
          //1. 先创建一个 Node 结点，name 就是 smith 
          Node smith = new Node("smith");
          //下面就把 smith 加入到双向链表了
          smith.next = hsp;
          smith.pre = tom; 
          hsp.pre = smith; 
          tom.next = smith;
  
          //让 first  再次指向 jack
          first = jack;//让 first 引用指向 jack,就是双向链表的头结点
  
          System.out.println("===从头到尾进行遍历==="); 
          while (true) {
          	if(first == null) {
                  break;
          	}
          //输出 first  信息
              System.out.println(first);
              first = first.next;
          }
  
          last = hsp; //让 last  重新指向最后一个结点
          //演示，从尾到头的遍历
          System.out.println("====从尾到头的遍历===="); 
          while (true) {
          	if(last == null) 
                  break;
          	}
          //输出 last  信息
          System.out.println(last);
          last = last.pre;
          }
      }
  }
  
  
  //定义一个 Node 类，Node 对象 表示双向链表的一个结点
  class Node {
      public Object item; //真正存放数据
      public Node next; //指向后一个结点
      public Node pre; //指向前一个结点
      public Node(Object name) {
      	this.item = name;
      }
      public String toString() {
      	return "Node name=" + item;
      }
  }
  ```

  

- LinkedList 的增删改查案例 （底层源码解读）

  ```java
  package com.hspedu.list_;
  
  import java.util.Iterator; 
  import java.util.LinkedList;
  
  @SuppressWarnings({"all"}) 
  public class LinkedListCRUD {
      public static void main(String[] args) {
  
          LinkedList linkedList = new LinkedList(); 
          linkedList.add(1);
          linkedList.add(2); 
          linkedList.add(3);
          System.out.println("linkedList=" + linkedList);
  
          //演示一个删除结点的
          linkedList.remove(); //  这里默认删除的是第一个结点
          //linkedList.remove(2);
  
          System.out.println("linkedList=" + linkedList);
  
          //修改某个结点对象
          linkedList.set(1, 999);
          System.out.println("linkedList=" + linkedList);
  
          //得到某个结点对象
          //get(1) 是得到双向链表的第二个对象
          Object o = linkedList.get(1);
          System.out.println(o);//999
  
          //因为 LinkedList  是 实现了 List 接口,  遍历方式
          System.out.println("===LinkeList 遍历迭代器===="); 
          Iterator iterator = linkedList.iterator();
          while (iterator.hasNext()) {
          	Object next =	iterator.next(); 
              System.out.println("next=" + next);
          }
  
          System.out.println("===LinkeList 遍历增强 for===="); 
          for (Object o1 : linkedList) {
          	System.out.println("o1=" + o1);
          }
          
          System.out.println("===LinkeList 遍历普通 for===="); 
          for (int i = 0; i < linkedList.size(); i++) {
          	System.out.println(linkedList.get(i));
          }
  
  
          //老韩源码阅读.
          /* 1. LinkedList linkedList = new LinkedList(); 
          	public LinkedList() {} // 进入构造器初始化
          2. 这时 linkeList 的属性 first = null	last = null
          3.执行 添加
          	public boolean add(E e) { 
          		linkLast(e);
          		return true;
          	}
          4.将新的结点，加入到双向链表的最后
          	void linkLast(E e) {
          		final Node<E> l = last;
          		final Node<E> newNode = new Node<>(l, e, null); 
          		last = newNode;
          		if (l == null)
          			first = newNode;
          		else
          			l.next = newNode;
                  size++;
         			modCount++;
          	}
          */
  
          /*
          老韩读源码 linkedList.remove(); //  这里默认删除的是第一个结点
          1. 执行 removeFirst 
          		public E remove() {
          			return removeFirst();
         		    }
          2.执行
          public E removeFirst() { 
          	final Node<E> f = first; 
          	if (f == null)
          		throw new NoSuchElementException(); 
              return unlinkFirst(f);
          	}
          3.执行 unlinkFirst,  将 f 指向的双向链表的第一个结点拿掉
          private E unlinkFirst(Node<E> f) {
              // assert f == first && f != null; 
              final E element = f.item;
              final Node<E> next = f.next; 
              f.item = null;
              f.next = null; // help GC 
              first = next;
              if (next == null)
                  last = null;
              else
                  next.prev = null; 
              size--;
              modCount++; 
              return element;
          }
          */
      }
  }
  ```

  

- ArrayList 和 LinkedList 比较

  ![image-20210925135127576](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925135127576.png)



#### 6. Set 接口和常用方法

- Set 接口基本介绍

  ![image-20210925135552487](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925135552487.png)

- Set 接口的常用方法

  Set 接口也是 Collection 的子接口，因此，常用方法和 Collection 接口一样.

- Set 接口的遍历方式

  ![image-20210925140122832](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925140122832.png)

- Set 接口的常用方法举例

  ```java
  package com.hspedu.set_;
  
  import java.util.HashSet; 
  import java.util.Iterator;
  import java.util.Set;
  
  @SuppressWarnings({"all"})
  public class SetMethod {
      public static void main(String[] args) {
          //老韩解读
          //1. 以 Set  接口的实现类 HashSet  来讲解 Set  接口的方法
          //2. set  接口的实现类的对象(Set 接口对象), 不能存放重复的元素,  可以添加一个 null
          //3. set  接口对象存放数据是无序 (即添加的顺序和取出的顺序不一致)
          //4. 注意：取出的顺序虽然不是添加的顺序，但是他的取出顺序 固定. 
          Set set = new HashSet();
          set.add("john");
          set.add("lucy");
          set.add("john");//重复set.add("jack");
          set.add("hsp");
          set.add("mary"); 
          set.add(null);//
          set.add(null);//再次添加 null
          for(int i = 0; i <10;i ++) { 
              System.out.println("set=" + set);
          }
  
          //遍历
          //方式 1： 使用迭代器
          System.out.println("=====使用迭代器===="); 
          Iterator iterator = set.iterator();
          while (iterator.hasNext()) {
              Object obj = iterator.next();
          	System.out.println("obj=" + obj);
          }
          
          set.remove(null);
  
          //方式 2:  增强 for
          System.out.println("=====增强 for====");
          for (Object o : set) { 
              System.out.println("o=" + o);
          }
  
          //set 接口对象，不能通过索引来获取
      }
  }
  ```

  

#### 7. Set 接口实现类-HashSet

- HashSet 的全面说明

  ![image-20210925141420942](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925141420942.png)

- HashSet 案例说明 （面试题）

  ```java
  package com.hspedu.set_;
  
  import java.util.HashSet;
  
  @SuppressWarnings({"all"}) 
  public class HashSet01 {
      public static void main(String[] args) {
          HashSet set = new HashSet();
          
          //说明
          //1. 在执行 add 方法后，会返回一个 boolean 值
          //2. 如果添加成功，返回 true, 否则返回 false
          //3. 可以通过 remove 指定删除哪个对象
          System.out.println(set.add("john"));//T 
          System.out.println(set.add("lucy"));//T 
          System.out.println(set.add("john"));//F 
          System.out.println(set.add("jack"));//T 
          System.out.println(set.add("Rose"));//T
  
          set.remove("john"); 
          System.out.println("set=" + set);//3 个
  
          //
          set	= new HashSet(); 
          System.out.println("set=" + set);//0
          
          //4 Hashset 不能添加相同的元素/数据?
          set.add("lucy");//添加成功
          set.add("lucy");//加入不了
          
          set.add(new Dog("tom"));//OK 
          set.add(new Dog("tom"));//Ok 
          System.out.println("set=" + set);
  
          //在加深一下. 非常经典的  面试题.
          //看源码，做分析， 先给小伙伴留一个坑，以后讲完源码，你就了然
          //去看他的源码，即 add 到底发生了什么?=> 底层机制. 
          set.add(new String("hsp"));//ok
          set.add(new String("hsp"));//加入不了. 
          System.out.println("set=" + set);
  
      }
  }
  class Dog { //定义了 Dog 类
      private String name;
  
      public Dog(String name) {
          this.name = name;
      }
  
      @Override
      public String toString() { return "Dog{" +
          "name='" + name + '\'' + '}';
      }
  }
  ```

  

- HashSet 底层机制说明

  ![image-20210925145017826](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925145017826.png)

  ![image-20210925145028202](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925145028202.png)

  
  
  - HashSet添加元素的底层实现 （源码）
  
  ![image-20210925145038795](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925145038795.png)
  
  ```java
  package com.hspedu.set_;
  
  import java.util.HashSet;
  
  @SuppressWarnings({"all"})
  public class HashSetSource {
      public static void main(String[] args) {
  
          HashSet hashSet = new HashSet();
          hashSet.add("java");//到此位置，第 1 次 add 分析完毕.
          hashSet.add("php");//到此位置，第 2 次 add 分析完毕
          hashSet.add("java");
          System.out.println("set=" + hashSet);
  
          /*
          老韩对 HashSet  的源码解读
          1.执 行 HashSet() 
          public HashSet() {
          	map = new HashMap<>();
          }
          2.执行 add()
          public boolean add(E e) {//e = "java"
          	return map.put(e, PRESENT)==null; //(static) PRESENT = new Object();
          }
          3.执行 put() , 该方法会执行 hash(key) 得到 key 对应的 hash 值 
          	算法为 h = key.hashCode()) ^ (h >>> 16) 
          public V put(K key, V value) { //key = "java" value = PRESENT 共享
          	return putVal(hash(key), key, value, false, true);
          }
          4.执行 putVal
          final V putVal(int hash, K key, V value, boolean onlyIfAbsent, boolean evict) {
          	Node<K,V>[] tab; Node<K,V> p; int n, i; //定义了辅助变量
          	//table 就是 HashMap 的一个数组，类型是 Node[]
          	//if 语句表示如果当前 table 是 null, 或者 大小=0
          	//就是第一次扩容，到 16 个空间.
          	if ((tab = table) == null || (n = tab.length) == 0) 
          		n = (tab = resize()).length;
  
              //(1)根据 key，得到 hash  去 计算 该 key 应该存放到 table 表的哪个索引位置
              //并把这个位置的对象，赋给 p
              //(2)判断 p  是否为 null
              //(2.1) 如果 p  为 null, 表示还没有存放元素, 就创建一个 Node (key="java",value=PRESENT)
              //(2.2) 就放在该位置 tab[i] = newNode(hash, key, value, null)
  
              if ((p = tab[i = (n - 1) & hash]) == null)
                  tab[i] = newNode(hash, key, value, null); 
              else {
                  //一个开发技巧提示： 在需要局部变量(辅助变量)时候，再创建
                  Node<K,V> e; K k; //
                  //如果当前索引位置对应的链表的第一个元素和准备添加的 key 的 hash 值一样
                  //并且满足 下面两个条件之一:
                  //(1) 准备加入的 key  和 p  指向的 Node 结点的 key 是同一个对象
                  //(2)	p 指向的 Node 结点的 key 的 equals() 和准备加入的 key 比较后相同
                  //就不能加入
                  if (p.hash == hash &&
                  ((k = p.key) == key || (key != null && key.equals(k)))) 
                      e = p;
  
                  //再判断 p  是不是一颗红黑树,
                  //如果是一颗红黑树，就调用 putTreeVal , 来进行添加
                  else if (p instanceof TreeNode)
                      e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
                  else {//如果 table 对应索引位置，已经是一个链表,  就使用 for 循环比较
                  //(1) 依次和该链表的每一个元素比较后，都不相同, 则加入到该链表的最后
                  //	注意在把元素添加到链表后，立即判断 该链表是否已经达到 8 个结点
                  //	, 就调用 treeifyBin() 对当前这个链表进行树化(转成红黑树)
                  //	注意，在转成红黑树时，要进行判断, 判断条件
                  //	if (tab == null || (n = tab.length) < MIN_TREEIFY_CAPACITY(64))
                  //		resize();
                  //	如果上面条件成立，先 table 扩容.
                  //	只有上面条件不成立时，才进行转成红黑树
                  //(2) 依次和该链表的每一个元素比较过程中，如果有相同情况,就直接 break
  
                      for (int binCount = 0; ; ++binCount) { 
                          if ((e = p.next) == null) {  // p的下一个节点为空，直接加！！
                              p.next = newNode(hash, key, value, null);
                              if (binCount >= TREEIFY_THRESHOLD(8) - 1) // -1 for 1st 
                                  treeifyBin(tab, hash);
                              break;
                          }
                          if (e.hash == hash && //这里的e已经指向 p.next，如果该节点不为空,再次判断能否加入！！
                              ((k = e.key) == key || (key != null && key.equals(k)))) 
                                  break;
                          p = e;  //循环变量迭代，让p指向e，即指向 p.next !!
                      }
             	 	}
                  if (e != null) { // existing mapping for key V 
                  	oldValue = e.value;
                      if (!onlyIfAbsent || oldValue == null)
                      	e.value = value;
                      afterNodeAccess(e);
                      return oldValue;
                  }
              }
              ++modCount;
              //size  就是我们每加入一个结点 Node(k,v,h,next), size++ 
              if (++size > threshold)  //临界值threshold 是 table长度*0.75
              	resize();//扩容
              afterNodeInsertion(evict); 
              return null;
          }
        */
      }
  }
  ```
  
  - HashSet的扩容和转成红黑树机制 （源码）
  
  ![image-20210925215617045](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210925215617045.png)
  
  如 size > 临界值，就扩容
  
  ```java
  package com.hspedu.set_;
  
  import java.util.HashSet; 
  import java.util.Objects;
  
  @SuppressWarnings({"all"}) 
  public class HashSetIncrement {
      public static void main(String[] args) {
          /*
          HashSet 底层是 HashMap, 第一次添加时，table 数组扩容到 16， 临界值(threshold)是 16*加载因子(loadFactor)是 0.75 = 12
          如果 table 数组使用到了临界值 12,就会扩容到 16 * 2 = 32新的临界值就是 32*0.75 = 24, 依次类推
          */
          HashSet hashSet = new HashSet();
          //	for(int i = 1; i <= 100; i++) {
          //		hashSet.add(i);//1,2,3,4,5...100
          //	}
          /*
          在 Java8 中, 如果一条链表的元素个数到达 TREEIFY_THRESHOLD(默认是 8 )， 并且 table 的大小 >= MIN_TREEIFY_CAPACITY(默认 64),就会进行树化(红黑树), 否则仍然采用数组扩容机制
          */
          //	for(int i = 1; i <= 12; i++) {
          //		hashSet.add(new A(i));//
          //	}
  
          /*
          当我们向 hashset 增加一个元素，-> Node -> 加入 table ,  就算是增加了一个 size++ （不管是加在table数组第一个位置还是在链表上）
  
          */
  
          for(int i = 1; i <= 7; i++) {//在 table 的某一条链表上添加了 7 个 A 对象
          	hashSet.add(new A(i));//
          }
  
  
          for(int i = 1; i <= 7; i++) {//在 table 的另外一条链表上添加了 7 个 B 对象
          	hashSet.add(new B(i));//
          }
      }
  }
  
  
  class B {
      private int n;
  
  
      public B(int n) {
      	this.n = n;
      }
      @Override
      public int hashCode() { // 对hashCode()重写，以实现让添加的key的hash值一样
          return 200;
      }
  }
  
  
  class A {
      private int n;
      public A(int n) {
      	this.n = n;
      }
      @Override
      public int hashCode() { 
          return 100;
      }
  }
  ```
  
  - 练习
  
  ![image-20210926000314977](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926000314977.png)
  
  ```java
  package com.yt.collection_;
  
  import java.util.HashSet;
  import java.util.Objects;
  
  /**
   * @author Yt
   * @version 1.0
   */
  @SuppressWarnings({"all"})
  public class HashSetExercise02 {
      public static void main(String[] args){
          HashSet hashSet = new HashSet();
          hashSet.add(new Employee02("tt",22,new MyDate(1997,12,5)));
          hashSet.add(new Employee02("dd",23,new MyDate(1999,2,15)));
          hashSet.add(new Employee02("tt",22,new MyDate(1997,12,5)));
  
          for (Object o :hashSet) {
              System.out.println(o);
          }
  
      }
  }
  
  class Employee02{
      private String name;
      private double sal;
      private MyDate birthday;
  
      public Employee02(String name, double sal, MyDate birthday) {
          this.name = name;
          this.sal = sal;
          this.birthday = birthday;
      }
  
      @Override
      public boolean equals(Object o) {
          if (this == o) return true;
          if (o == null || getClass() != o.getClass()) return false;
          Employee02 that = (Employee02) o;
          return Objects.equals(name, that.name) &&
                  Objects.equals(birthday, that.birthday); //到这里得再去判断两个Mydate对象是否相等，所以得重写Mydate类的equals()方法！！
      }
  
      @Override
      public int hashCode() {
          return Objects.hash(name, sal, birthday); //这里会调用MyDate类的hashCode()方法，保证birthday相同的hash值一样，从而让name, sal, birthday相同的hash值一样！！
      }
  
      @Override
      public String toString() {
          return "Employee02{" +
                  "name='" + name + '\'' +
                  ", sal=" + sal +
                  ", birthday=" + birthday +
                  '}';
      }
  
  
  }
  
  class MyDate{
      private int year;
      private int mouth;
      private int day;
  
      public MyDate(int year, int mouth, int day) {
          this.year = year;
          this.mouth = mouth;
          this.day = day;
      }
  
      public int getYear() {
          return year;
      }
  
      public void setYear(int year) {
          this.year = year;
      }
  
      public int getMouth() {
          return mouth;
      }
  
      public void setMouth(int mouth) {
          this.mouth = mouth;
      }
  
      public int getDay() {
          return day;
      }
  
      public void setDay(int day) {
          this.day = day;
      }
  
      @Override
      public String toString() {
          return "MyDate{" +
                  "year=" + year +
                  ", mouth=" + mouth +
                  ", day=" + day +
                  '}';
      }
  
      @Override
      public boolean equals(Object o) {
          if (this == o) return true;
          if (o == null || getClass() != o.getClass()) return false;
          MyDate myDate = (MyDate) o;
          return year == myDate.year &&
                  mouth == myDate.mouth &&
                  day == myDate.day;
      }
  
      @Override
      public int hashCode() {
          return Objects.hash(year, mouth, day);
      }
  }
  
  ```
  
  

#### 8. Set 接口实现类-LinkedHashSet

- LinkedHashSet 的全面说明

  ![image-20210926001131977](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926001131977.png)

  ![image-20210926001208581](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926001208581.png)

  ![image-20210926003325842](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926003325842.png)

  ![image-20210926003447332](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926003447332.png)

### 3. Map 

#### 1. Map 接口和常用方法 (注意遍历方式！！)

- Map 接口实现类的特点 [很实用]

  ![image-20210926121840759](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926121840759.png)

  ```java
  package com.hspedu.map_;
  
  import java.util.HashMap; 
  import java.util.Map;
  
  @SuppressWarnings({"all"})
  public class Map_ {
      public static void main(String[] args) {
          //老韩解读 Map 接口实现类的特点,  使用实现类 HashMap
          //1. Map 与 Collection 并列存在。用于保存具有映射关系的数据:Key-Value(双列元素)
          //2. Map  中的 key  和	value 可以是任何引用类型的数据，会封装到 HashMap$Node 对象中
          //3. Map 中的 key  不允许重复，原因和 HashSet  一样，前面分析过源码.
          //4. Map 中的 value 可以重复
          //5. Map 的 key  可以为 null, value 也可以为 null  ，注意 key  为 null,
          //	只能有一个，value 为 null ,可以多个
          //6. 常用 String 类作为 Map 的 key
          //7. key 和 value 之间存在单向一对一关系，即通过指定的 key 总能找到对应的 value 
          Map map = new HashMap();
          map.put("no1", "韩顺平");//k-v
          map.put("no2", "张无忌");//k-v
          map.put("no1", "张三丰");// 当有相同的 k , 就等价于替换. 
          map.put("no3", "张三丰");//k-v
          map.put(null, null); //k-v 
          map.put(null, "abc"); //等价替换
          map.put("no4", null); //k-v
          map.put("no5", null); //k-v
          map.put(1, "赵敏");//k-v
          map.put(new Object(), "金毛狮王");//k-v
          // 通过 get  方法，传入 key ,会返回对应的 value
          System.out.println(map.get("no2"));//张无忌
          System.out.println("map=" + map);
      }
  }
  ```

  - 为了方便遍历，创建EntrySet集合！EntrySet集合存放元素类型Entry，一个Entry对象就有k，v值（因为真正存放k，v值的HashMap$Node 实现了Entry接口，所以这里相当于向上转型，Entry变量的引用指向了真正存放k，v的Node对象，所以它就有了k，v的地址）

  ![image-20210926122014258](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926122014258.png)

  ![image-20210926133030203](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926133030203.png)

  ![image-20210926132957482](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926132957482.png)

  ![image-20210926134819781](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926134819781.png)

  

- Map 接口常用方法

  ![image-20210926141036066](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926141036066.png)



- Map 接口遍历方法

  ![image-20210926142731451](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926142731451.png)

  ```java
  package com.hspedu.map_;
  
  import java.util.*;
  
  @SuppressWarnings({"all"}) 
  public class MapFor {
      public static void main(String[] args) {
  
          Map map = new HashMap();
          map.put("邓超", "孙俪");
          map.put("王宝强", "马蓉");
          map.put("宋喆", "马蓉");
          map.put("刘令博", null);
          map.put(null, "刘亦菲");
          map.put("鹿晗", "关晓彤");
  
          //第一组: 先取出 所有的 Key ,  通过 Key 取出对应的 Value 
          Set keyset = map.keySet();
          //(1) 增强 for
          System.out.println("-----第一种方式	");
          for (Object key : keyset) {
          System.out.println(key + "-" + map.get(key));
          }
          //(2) 迭代器
          System.out.println("----第二种方式	");
          Iterator iterator = keyset.iterator(); 
          while (iterator.hasNext()) {
          	Object key = iterator.next();
              System.out.println(key + "-" + map.get(key));
          }
  
  
          //第二组: 把所有的 values 取出
          Collection values = map.values();
          //这里可以使用所有的 Collections 使用的遍历方法
          //(1) 增强 for
          System.out.println("---取出所有的 value 增强 for	");
          for (Object value : values) { 
              System.out.println(value);
          }
          //(2) 迭代器
          System.out.println("---取出所有的 value 迭代器	");
          Iterator iterator2 = values.iterator(); 
          while (iterator2.hasNext()) {
          	Object value =	iterator2.next();
          	System.out.println(value);
          }
  
  
          //第三组: 通过 EntrySet  来获取 k-v
          Set entrySet = map.entrySet();// EntrySet<Map.Entry<K,V>>
          //(1) 增强 for
          System.out.println("----使用 EntrySet  的 for 增强(第 3 种)	");
          for (Object entry : entrySet) {
              // 将 entry 转 成 Map.Entry 
              Map.Entry m = (Map.Entry) entry;
              System.out.println(m.getKey() + "-" + m.getValue());
          }
          //(2) 迭代器
          System.out.println("----使用 EntrySet 的 迭代器(第 4 种)	");
          Iterator iterator3 = entrySet.iterator(); 
          while (iterator3.hasNext()) {
          	Object entry =	iterator3.next();
          	//System.out.println(next.getClass());//HashMap$Node -实现-> Map.Entry (getKey,getValue)
          	//向下转型 Map.Entry
          	Map.Entry m = (Map.Entry) entry;
              System.out.println(m.getKey() + "-" + m.getValue());
      }
  }
  ```

  

- 练习

  ![image-20210926150732212](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926150732212.png)

  ```java
  package com.yt.map_;
  
  import java.util.Collection;
  import java.util.HashMap;
  import java.util.Set;
  
  /**
   * @author Yt
   * @version 1.0
   */
  @SuppressWarnings({"all"})
  public class MapExercise {
      public static void main(String[] args){
          HashMap hashMap = new HashMap();
          Employee aa = new Employee("aa", 18900, 1);
          Employee bb = new Employee("bb", 50000, 2);
          Employee cc = new Employee("cc", 10000, 3);
  
          hashMap.put(aa.getId(),aa);
          hashMap.put(bb.getId(),bb);
          hashMap.put(cc.getId(),cc);
  
          Collection values = hashMap.values();
          for (Object o :values) {
              Employee e = (Employee) o;
              if(e.getSal() > 18000){
                  System.out.println(e);
              }
          }
  
          System.out.println("===第二种遍历===");
          Set set = hashMap.keySet();
          for (Object o :set) {
              Employee employee = (Employee) hashMap.get(o);
              if(employee.getSal() > 18000){
                  System.out.println(employee);
              }
          }
  
  
      }
  }
  
  class Employee{
      private String name;
      private double sal;
      private int id;
  
      public Employee(String name, double sal, int id) {
          this.name = name;
          this.sal = sal;
          this.id = id;
      }
  
      public String getName() {
          return name;
      }
  
      public void setName(String name) {
          this.name = name;
      }
  
      public double getSal() {
          return sal;
      }
  
      public void setSal(double sal) {
          this.sal = sal;
      }
  
      public int getId() {
          return id;
      }
  
      public void setId(int id) {
          this.id = id;
      }
  
      @Override
      public String toString() {
          return "Employee{" +
                  "name='" + name + '\'' +
                  ", sal=" + sal +
                  ", id=" + id +
                  '}';
      }
  }
  ```



#### 2. Map 接口实现类-HashMap

- HashMap 小结

  ![image-20210926152228044](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926152228044.png)

- HashMap 底层机制及源码剖析

  ![image-20210926152951829](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926152951829.png)

  ![image-20210926153004616](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926153004616.png)

  如 size > 临界值，就扩容
  
  ```java
  package com.hspedu.map_;
  
  import java.util.HashMap;
  
  @SuppressWarnings({"all"})
  public class HashMapSource1 {
      public static void main(String[] args) { 
          HashMap map = new HashMap(); 
          map.put("java", 10);//ok
          map.put("php", 10);//ok 
          map.put("java", 20);//替换 value
  
          System.out.println("map=" + map);//
  
          /*
          老韩解读 HashMap 的源码+图解
          1.执行构造器 new HashMap()
            初始化加载因子 loadfactor = 0.75 
            HashMap$Node[] table = null
          2.执行 put 调用 hash 方法，计算 key 的 hash 值 (h = key.hashCode()) ^ (h >>> 16) 
            public V put(K key, V value) {//K = "java" value = 10
            	return putVal(hash(key), key, value, false, true);
            }
          3.执行 putVal
            final V putVal(int hash, K key, V value, boolean onlyIfAbsent, boolean evict) {
            	Node<K,V>[] tab; Node<K,V> p; int n, i;//辅助变量
          	//如果底层的 table 数组为 null,  或者 length =0 ,  就扩容到 16 
          	if ((tab = table) == null || (n = tab.length) == 0)
          		n = (tab = resize()).length;
          	//取出 hash 值对应的 table 的索引位置的 Node,  如果为 null,  就直接把加入的 k-v
          	//, 创建成一个 Node ,加入该位置即可
          	if ((p = tab[i = (n - 1) & hash]) == null)
          		tab[i] = newNode(hash, key, value, null); 
          	else {
          		Node<K,V> e; K k;//辅助变量
          		// 如果 table 的索引位置的 key 的 hash 和新的 key 的 hash 值相同，
          		// 并 满足(table 现有的结点的 key 和准备添加的 key 是同一个对象	|| equals 返回真)
          		// 就认为不能加入新的 k-v 
          		if (p.hash == hash &&
          			((k = p.key) == key || (key != null && key.equals(k)))) 
          			e = p;
          		else if (p instanceof TreeNode)//如果当前的 table 的已有的 Node 是红黑树，就按照红黑树的方式处理
          			e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value); 
                  else {
          			//如果找到的结点，后面是链表，就循环比较
          			for (int binCount = 0; ; ++binCount) {//死循环
          				if ((e = p.next) == null) {//如果整个链表，没有和他相同,就加到该链表的最后
          					p.next = newNode(hash, key, value, null);
          					//加入后，判断当前链表的个数，是否已经到 8 个，到 8 个，后
          					//就调用 treeifyBin 方法进行红黑树的转换
          				if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st 
          					treeifyBin(tab, hash);
          					break;
          				}
          				if (e.hash == hash && //如果在循环比较过程中，发现有相同,就 break,就只是替换 value 							((k = e.key) == key || (key != null && key.equals(k))))
          					break; 
          				p = e;
          			}
          		}
          		if (e != null) { // existing mapping for key
              		V oldValue = e.value;
          			if (!onlyIfAbsent || oldValue == null)
          				e.value = value; //替换，key 对应 value 
          				afterNodeAccess(e);
          				return oldValue;
          		}
          	}
          	++modCount;//每增加一个 Node ,就 size++
          	if (++size > threshold[12-24-48])//如 size > 临界值，就扩容
          		resize(); 
          	afterNodeInsertion(evict); 
          	return null;
          }	
  
          5. 关于树化(转成红黑树)
          //如果 table 为 null ,或者大小还没有到 64，暂时不树化，而是进行扩容.
          //否则才会真正的树化 -> 剪枝（红黑树 -> 链表+数组）
          final void treeifyBin(Node<K,V>[] tab, int hash) { 
          	int n, index; Node<K,V> e;
          	if (tab == null || (n = tab.length) < MIN_TREEIFY_CAPACITY) 
          		resize();
          }
          */
      }
  }
  ```
  
  

#### 3. Map 接口实现类-Hashtable

- HashTable 的基本介绍

  ![image-20210926164719067](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926164719067.png)

- Hashtable底层

  ![image-20210926165816448](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926165816448.png)

- Hashtable 和 HashMap 对比

  ![image-20210926165846149](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926165846149.png)



#### 4. Map 接口实现类-Properties

- 基本介绍

  ![image-20210926170803419](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926170803419.png)

- 基本使用

  ```java
  package com.hspedu.map_;
  
  import java.util.Properties;
  
  @SuppressWarnings({"all"}) 
  public class Properties_ {
      public static void main(String[] args) {
          //老韩解读
          //1. Properties 继承	Hashtable
          //2. 可以通过 k-v 存放数据，当然 key  和 value 不能为 null
          //增加
          Properties properties = new Properties();
          //properties.put(null, "abc");//抛出 空指针异常
          //properties.put("abc", null); //抛出 空指针异常
          properties.put("john", 100);//k-v 
          properties.put("lucy", 100);
          properties.put("lic", 100);
          properties.put("lic", 88);//如果有相同的 key  ， value 被替换
       
          System.out.println("properties=" + properties);
          //通过 k  获取对应值
          System.out.println(properties.get("lic"));//88
  		System.out.println(properties.getProperty("lic"));//88
  
          //删除properties.remove("lic");
          System.out.println("properties=" + properties);
  
  
          //修改
          properties.put("john", " 约 翰 ");
          System.out.println("properties=" + properties);
      }
  }
  ```



#### 5. 总结-开发中如何选择集合实现类(记住)

![image-20210926173120513](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926173120513.png)

- TreeSet源码解读

```java
package com.hspedu.set_;

import java.util.Comparator;
import java.util.TreeSet;

@SuppressWarnings({"all"}) 
public class TreeSet_ {
    public static void main(String[] args) {

        //老韩解读
        //1. 当我们使用无参构造器，创建 TreeSet 时，仍然是无序的
        //2. 老师希望添加的元素，按照字符串大小来排序
        //3. 使用 TreeSet 提供的一个构造器，可以传入一个 比较器(匿名内部类)
        //	并指定排序规则
        //4. 简单看看源码
        //老韩解读
        /*
        1.构造器把传入的比较器对象，赋给了 TreeSet 的底层的 TreeMap 的属性 this.comparator

        public TreeMap(Comparator<? super K> comparator) { 
        	this.comparator = comparator;
        }
        
        2.在 调用 treeSet.add("tom"),  在底层会执行到

        if (cpr != null) {//cpr 就是我们的匿名内部类(对象)
        do {
        	parent = t;
            //动态绑定到我们的匿名内部类(对象)
            compare cmp = cpr.compare(key, t.key);
            if (cmp < 0)
            	t = t.left; 
            else if (cmp > 0)
            	t = t.right;
            else //如果相等，即返回 0,这个 Key 就没有加入
            	return t.setValue(value);
            } while (t != null);
        }
        */

        //	TreeSet treeSet = new TreeSet();
        TreeSet treeSet = new TreeSet(new Comparator() { 
            @Override
        	public int compare(Object o1, Object o2) {
        		//下面 调用 String 的 compareTo 方法进行字符串大小比较       	
        		//return ((String) o2).compareTo((String) o1); 
                //如果老韩要求加入的元素，按照长度大小排序
                return ((String) o1).length() - ((String) o2).length();
        	}
        });
        // 添 加 数 据 . 
        treeSet.add("jack");
        treeSet.add("tom");//3 
        treeSet.add("sp");
        treeSet.add("a");
        treeSet.add("abc");//3

        System.out.println("treeSet=" + treeSet);

    }
}
```

- TreeMap源码解读

  ```java
  package com.hspedu.map_;
  
  import java.util.Comparator;
  import java.util.TreeMap;
  
  @SuppressWarnings({"all"})
  public class TreeMap_ {
      public static void main(String[] args) {
  
          //使用默认的构造器，创建 TreeMap, 是无序的(也没有排序)
          /*
          老韩要求：按照传入的 k(String) 的大小进行排序
          */
          //	TreeMap treeMap = new TreeMap();
          TreeMap treeMap = new TreeMap(new Comparator() { 
              @Override
          	public int compare(Object o1, Object o2) {
          		//按照传入的 k(String) 的大小进行排序
          		//按照 K(String) 的长度大小排序
          		//return ((String) o2).compareTo((String) o1); 
                  return ((String) o2).length() - ((String) o1).length();
          	}
          });
          treeMap.put("jack", "杰克");
          treeMap.put("tom", " 汤 姆 ");
          treeMap.put("kristina", "克瑞斯提诺"); 
          treeMap.put("smith", " 斯 密 斯 "); 
          treeMap.put("hsp", "韩顺平");//加入不了
  
          System.out.println("treemap=" + treeMap);
  
          /*
          
          老韩解读源码：
          1.构造器. 把传入的实现了 Comparator 接口的匿名内部类(对象)，传给 TreeMap 的 comparator 
          public TreeMap(Comparator<? super K> comparator) {
          	this.comparator = comparator;
          }
          2.调用 put 方法
          2.1第一次添加, 把 k-v 封装到 Entry 对象，放入 root 
          Entry<K,V> t = root;
          if (t == null) {
          	compare(key, key); // type (and possibly null) check
  
          	root = new Entry<>(key, value, null); 
          	size = 1;
          	modCount++; 
          	return null;
          }
          2.2以后添加
          Comparator<? super K> cpr = comparator; 
          if (cpr != null) {
              do { //遍历所有的 key ,  给当前 key 找到适当位置
                  parent = t;
                  cmp = cpr.compare(key, t.key);//动态绑定到我们的匿名内部类的 compare 
                  if (cmp < 0)
                  	t = t.left; 
                  else if (cmp > 0)
                  	t = t.right;
                  else	//如果遍历过程中，发现准备添加 Key 和当前已有的 Key 相等，就不添加
                  	return t.setValue(value);
          	} while (t != null);
          }
          */
      }
  }
  ```

  

### 4. Collections

- Collections 工具类介绍

  ![image-20210926232626874](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926232626874.png)

- 排序操作：（均为static 方法)

  ![image-20210926232738974](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926232738974.png)

- 查找、替换

  ![image-20210926234054813](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210926234054813.png)

```java
public class Collections_ {
    public static void main(String[] args) {

        //创建 ArrayList 集合，用于测试. 
        List list = new ArrayList(); 
        list.add("tom");
        list.add("smith");
        list.add("king");
        list.add("milan");
        list.add("tom");

        //		reverse(List)：反转 List 中元素的顺序
        Collections.reverse(list); 
        System.out.println("list=" + list);
        //	shuffle(List)：对 List 集合元素进行随机排序
        //	for (int i = 0; i < 5; i++) {
        //		Collections.shuffle(list);
        //		System.out.println("list=" + list);
        //	}

        //	sort(List)：根据元素的自然顺序对指定 List 集合元素按升序排序
        Collections.sort(list);
        System.out.println("自然排序后");
        System.out.println("list=" + list);
        //	sort(List，Comparator)：根据指定的 Comparator 产生的顺序对 List  集合元素进行排序
        //我们希望按照 字符串的长度大小排序
        Collections.sort(list, new Comparator() {
            @Override
        	public int compare(Object o1, Object o2) {
        		//可以加入校验代码.
       			 return ((String) o2).length() - ((String) o1).length();
        	}
        });
        System.out.println("字符串长度大小排序=" + list);
        
        //	swap(List，int， int)：将指定 list 集合中的 i  处元素和 j  处元素进行交换
        //比如
        Collections.swap(list, 0, 1);
        System.out.println("交换后的情况");
        System.out.println("list=" + list);

        
        
        //Object max(Collection)：根据元素的自然顺序，返回给定集合中的最大元素
        System.out.println("自然顺序最大元素=" + Collections.max(list));
        //Object max(Collection，Comparator)：根据 Comparator 指定的顺序，返回给定集合中的最大元素
        //比如，我们要返回长度最大的元素
        Object maxObject = Collections.max(list, new Comparator() { 
            @Override
        	public int compare(Object o1, Object o2) {
        		return ((String)o1).length() - ((String)o2).length();
        	}
        });
        System.out.println("长度最大的元素=" + maxObject);

        //Object min(Collection)
        //Object min(Collection，Comparator)
        //上面的两个方法，参考 max 即可

        //int frequency(Collection，Object)：返回指定集合中指定元素的出现次数
        System.out.println("tom 出现的次数=" + Collections.frequency(list, "tom"));

        //void copy(List dest,List src)：将 src 中的内容复制到 dest 中
        ArrayList dest = new ArrayList();
        //为了完成一个完整拷贝，我们需要先给 dest 赋值，大小和 list.size()一样
        for(int i = 0; i < list.size(); i++) {
        	dest.add("");
        }
        //拷贝Collections.copy(dest, list);
        System.out.println("dest=" + dest);

        //boolean replaceAll(List list，Object oldVal，Object newVal)：使用新值替换 List 对象的所有旧值
        //如果 list 中，有 tom  就替换成 汤姆
        Collections.replaceAll(list, "tom", "汤姆");
        System.out.println("list 替换后=" + list);
    }
}
```



- 练习

  - ![image-20210927010352416](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927010352416.png)

    第5题.解答

    ![image-20210927010607802](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927010607802.png)

    需要将Person类实现Comparable接口就不会报错；

    

  - ![image-20210927012101095](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927012101095.png)

    注意：HashSet在执行remove方法时，也会像add方法那样计算hash值，所以这里因为Person类重写了hashCode方法，

    p1.name又被改了，执行remove方法，计算后返回的hash值，再经过计算得到的table索引就是一个新的索引，就删除不了P1；



## 第十四章 泛型

### 1. 泛型的理解和好处

- 看一个需求

  - ![image-20210927144413042](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927144413042.png)

  - 使用传统方法的问题分析

    ![image-20210927144510966](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927144510966.png)

  - 泛型快速体验-用泛型来解决前面的问题

    ```java
    package com.hspedu.generic.improve;
    
    import java.util.ArrayList;
    
    @SuppressWarnings({"all"}) 
    public class Generic02 {
        public static void main(String[] args) {
    
            //使用传统的方法来解决===> 使用泛型
            //老韩解读
            //1. 当我们 ArrayList<Dog> 表示存放到 ArrayList  集合中的元素是 Dog 类型 (细节后面说...)
            //2. 如果编译器发现添加的类型，不满足要求，就会报错
            //3. 在遍历的时候，可以直接取出 Dog 类型而不是 Object
            //4. public class ArrayList<E> {} E 称为泛型,那么 Dog->E 
            ArrayList<Dog> arrayList = new ArrayList<Dog>(); 
            arrayList.add(new Dog("旺财", 10));
            arrayList.add(new Dog("发财", 1));
            arrayList.add(new Dog("小黄", 5));
            //假如我们的程序员，不小心，添加了一只猫
            //arrayList.add(new Cat("招财猫", 8));
            System.out.println("===使用泛型===="); 
            for (Dog dog : arrayList) {
            	System.out.println(dog.getName() + "-" + dog.getAge());
            }
        }
    }
    
    
    /*
    1.请编写程序，在 ArrayList 中，添加 3 个 Dog 对象
    2.Dog 对象含有 name 和 age,  并输出 name 和 age (要求使用 getXxx())
    3.老师使用泛型来完成代码
    */
    class Dog {
    	private String name; 
        private int age;
        public Dog(String name, int age) { 
            this.name = name;
        	this.age = age;
        }
    
        public String getName() { return name;
        }
    
        public void setName(String name) { this.name = name;
        }
    
        public int getAge() { return age;
        }
    
        public void setAge(int age) { this.age = age;
        }
    }
    
    
    class Cat { //Cat 类private String name; private int age;
        public Cat(String name, int age) { 
            this.name = name;
        	this.age = age;
        }
        public String getName() { return name;
        }
        public void setName(String name) { this.name = name;
        }
        public int getAge() { return age;
        }
        public void setAge(int age) { this.age = age;
        }
    }
    ```

    

- 泛型的好处

  ![image-20210927145405581](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927145405581.png)



- 泛型介绍 (表示用来接收数据类型的数据类型)

  ![image-20210927151045603](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927151045603.png)

  ```java
  package com.hspedu.generic;
  
  import java.util.List;
  
  public class Generic03 {
      public static void main(String[] args) {
  
          //注意，特别强调： E 具体的数据类型在定义 Person 对象的时候指定,即在编译期间，就确定 E 是什么类型
          Person<String> person = new Person<String>("韩顺平教育"); 
          person.show(); //String
  
          /*
          你可以这样理解，上面的 Person 类
          class Person {
              String s ;//E 表示 s 的数据类型, 该数据类型在定义 Person 对象的时候指定,即在编译期间，就确定 E
              是什么类型
  
              public Person(String s) {//E 也可以是参数类型
              	this.s = s;
              }
              
              public String f() {//返回类型使用 E 
              	return s;
              }
          }
          */
  
  
          Person<Integer> person2 = new Person<Integer>(100); 
          person2.show();//Integer
  
          /*
          class Person {
              Integer s ;//E 表示 s 的数据类型, 该数据类型在定义 Person 对象的时候指定,即在编译期间，就确定 E
              是什么类型
  
  
              public Person(Integer s) {//E 也可以是参数类型
              	this.s = s;
              }
  
  
              public Integer f() {//返回类型使用 E 
              	return s;
              }
          }
              */
      }
  }
  
  
          //泛型的作用是：可以在类声明时通过一个标识表示类中某个属性的类型，
          // 或者是某个方法的返回值的类型，或者是参数类型
  
  
  class Person<E> {
      E s ;//E 表示 s 的数据类型,  该数据类型在定义 Person 对象的时候指定,即在编译期间，就确定 E 是什么类型
  
      public Person(E s) {//E 也可以是参数类型
          this.s = s;
      }
  
      public E f() {//返回类型使用 E
          return s;
      }
      public void show() {
          System.out.println(s.getClass());//显示 s 的运行类型
      }
  }
  ```

  

### 2. 泛型基本语法

- 泛型的声明

  ![image-20210927154730783](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927154730783.png)

- 泛型的实例化

  ![image-20210927154957457](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927154957457.png)

- 泛型使用的注意事项和细节

  ![image-20210927155324699](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927155324699.png)

  ```java
  import java.util.List;
  
  @SuppressWarnings({"all"}) 
  public class GenericDetail {
      public static void main(String[] args) {
          //1.给泛型指向数据类型时，要求是引用类型，不能是基本数据类型
          List<Integer> list = new ArrayList<Integer>(); //OK
          //List<int> list2 = new ArrayList<int>();//错误
  
          //2. 说明
          //因为 E 指定了 A 类型,  构造器传入了 new A()
          //在给泛型指定具体类型后，可以传入该类型或者其子类类型
          Pig<A> aPig = new Pig<A>(new A());
          aPig.f();
          Pig<A> aPig2 = new Pig<A>(new B()); 
          aPig2.f();
  
          //3. 泛型的使用形式
          ArrayList<Integer> list1 = new ArrayList<Integer>();
          List<Integer> list2 = new ArrayList<Integer>();
          //在实际开发中，我们往往简写
          //编译器会进行类型推断, 老师推荐使用下面写法
          ArrayList<Integer> list3 = new ArrayList<>(); 
          List<Integer> list4 = new ArrayList<>(); 
          ArrayList<Pig> pigs = new ArrayList<>();
  
          //4. 如果是这样写 泛型默认是 Object
          ArrayList arrayList = new ArrayList();//等价 ArrayList<Object> arrayList = new ArrayList<Object>();
  
  
          /*
          public boolean add(Object e) {
          	ensureCapacityInternal(size + 1);	// Increments modCount!! 
          	elementData[size++] = e;
          	return true;
          }
          */
          Tiger tiger = new Tiger();
          /*
          class Tiger {//类
              Object e;
  
  
              public Tiger() {}
  
              public Tiger(Object e) { 
              	this.e = e;
              }
          }
  
  
          */
  
  
      }
  }
  class Tiger<E> {//类E e;
  
      public Tiger() {}
  
  
      public Tiger(E e) {
          this.e = e;
      }
  }
  
  
  class A {}
  class B extends A {}
  
  
  class Pig<E> {//
  	E e;
  
  
  	public Pig(E e) { 
          this.e = e;
  	}
  
  
      public void f() {
      	System.out.println(e.getClass()); //运行类型
      }
  }
  ```

  

### 3. 自定义泛型

- 自定义泛型类![image-20210927190736189](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927190736189.png)

  ```java
  package com.hspedu.customgeneric;
  
  import java.util.Arrays;
  @SuppressWarnings({"all"})
  public class CustomGeneric_ {
      public static void main(String[] args) {
  
          //T=Double, R=String, M=Integer 
          Tiger<Double,String,Integer> g = new Tiger<>("john"); 
          g.setT(10.9); //OK
          //g.setT("yy"); //错误，类型不对
          System.out.println(g);
          
          Tiger g2 = new Tiger("john~~");//OK T=Object R=Object M=Object 
          g2.setT("yy"); //OK ,因为 T=Object "yy"=String 是 Object 子类
          System.out.println("g2=" + g2);
      }
  }
  
  //老韩解读
  //1. Tiger 后面泛型，所以我们把 Tiger 就称为自定义泛型类
  //2, T, R, M 泛型的标识符, 一般是单个大写字母
  //3. 泛型标识符可以有多个.
  //4. 普通成员可以使用泛型 (属性、方法)
  //5. 使用泛型的数组，不能初始化
  //6. 静态方法中不能使用类的泛型
  class Tiger<T, R, M> { 
      String name;
      R r; //属性使用到泛型
      M m;
      T t;
      //因为数组在 new 时不能确定 T 的类型，就无法在内存开空间
      T[] ts;
  
  
      public Tiger(String name) { this.name = name;
      }
  
      public Tiger(R r, M m, T t) {//构造器使用泛型
      	this.r = r; 
          this.m = m; 
          this.t = t;
      }
      
      public Tiger(String name, R r, M m, T t) {//构造器使用泛型this.name = name;
      	this.r = r; 
          this.m = m; 
          this.t = t;
      }
  
  //因为静态是和类相关的，在类加载时，对象还没有创建
  //所以，如果静态方法和静态属性使用了泛型，JVM 就无法完成初始化
  //	static R r2;
  //	public static void m1(M m) {
  //
  //	}
  
  
  //方法使用泛型
  
      public String getName() { 
          return name;
      }
  
  
      public void setName(String name) { 
          this.name = name;
      }
  
  
      public R getR() { 
          return r;
      }
  
  
      public void setR(R r) {//方法使用到泛型
          this.r = r;
      }
  
  
      public M getM() {//返回类型可以使用泛型. 
          return m;
      }
  
  
      public void setM(M m) {
      	this.m = m;
      }
  
  
      public T getT() { return t;
      }
  
  
      public void setT(T t) { this.t = t;
      }
  
  
      @Override
      public String toString() { return "Tiger{" +
          "name='" + name + '\'' + ", r=" + r +
          ", m=" + m +
          ", t=" + t +
          ", ts=" + Arrays.toString(ts) + '}';
      }
  }
  ```

  

- 自定义泛型接口

  ![image-20210927192755223](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927192755223.png)

  ```java
  
  public class CustomInterfaceGeneric { 
      public static void main(String[] args) {
  
  	}
  }
  
  /**
  *泛型接口使用的说明
  *1. 接口中，静态成员也不能使用泛型
  *2. 泛型接口的类型, 在继承接口或者实现接口时确定
  *3. 没有指定类型，默认为 Object
  */
  
  //在继承接口 指定泛型接口的类型
  interface IA extends IUsb<String, Double> {
  }
  //当我们去实现 IA 接口时，因为 IA 在继承 IUsu 接口时，指定了 U 为 String R 为 Double
  //，在实现 IUsu 接口的方法时，使用 String 替换 U, 是 Double 替换 R 
  class AA implements IA {
  
      @Override
      public Double get(String s) { 
          return null;
      }
      @Override
      public void hi(Double aDouble) {
  
      }
      @Override
      public void run(Double r1, Double r2, String u1, String u2) {
  
      }
  }
  
  //实现接口时，直接指定泛型接口的类型
  //给 U 指定 Integer 给 R 指定了 Float
  //所以，当我们实现 IUsb 方法时，会使用 Integer 替换 U, 使用 Float 替换 R 
  class BB implements IUsb<Integer, Float> {
  
      @Override
      public Float get(Integer integer) { 
          return null;
      }
  
      @Override
      public void hi(Float aFloat) {
  
      }
      @Override
      public void run(Float r1, Float r2, Integer u1, Integer u2) {
  
      }
  }
  
  //没有指定类型，默认为 Object
  //建议直接写成 IUsb<Object,Object>
  class CC implements IUsb { //等价 class CC implements IUsb<Object,Object> { 
      @Override
      public Object get(Object o) {
          return null;
      }
      @Override
      public void hi(Object o) {
      }
      @Override
      public void run(Object r1, Object r2, Object u1, Object u2) {
      }
  
  }
  
  
  interface IUsb<U, R> {
  //接口的属性默认为 public final static 修饰；
      int n = 10;
      //U name; 不能这样使用
  
  
      //普通方法中，可以使用接口泛型
      R get(U u);
  
      void hi(R r);
  
  
      void run(R r1, R r2, U u1, U u2);
  
      //在 jdk8  中，可以在接口中，使用默认方法,  也是可以使用泛型
      default R method(U u) { 
          return null;
      }
  }
  ```

  

- 自定义泛型方法

  ![image-20210927201151755](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927201151755.png)

  4. 泛型方法，可以使用类声明的泛型，也可以使用自己声明的泛型；

### 4.泛型的继承和通配符

- ![image-20210927204129755](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210927204129755.png)

```java
import java.util.ArrayList;
import java.util.List;
/**
*泛型的继承和通配符
*/
public class GenericExtends {
    public static void main(String[] args) {

        Object o = new String("xx");

        //泛型没有继承性
        //List<Object> list = new ArrayList<String>();


        //举例说明下面三个方法的使用
        List<Object> list1 = new ArrayList<>(); 
        List<String> list2 = new ArrayList<>(); 
        List<AA> list3 = new ArrayList<>();
        List<BB> list4 = new ArrayList<>();
        List<CC> list5 = new ArrayList<>();

        //如果是 List<?> c ，可以接受任意的泛型类型
        printCollection1(list1); 
        printCollection1(list2);
        printCollection1(list3);
        printCollection1(list4); 
        printCollection1(list5);

        //List<? extends AA> c： 表示 上限，可以接受 AA 或者 AA 子类
        //	printCollection2(list1);//×
        //	printCollection2(list2);//× 
        printCollection2(list3);//√ 
        printCollection2(list4);//√ 
        printCollection2(list5);//√

        //List<? super AA> c:  支持 AA 类以及 AA 类的父类，不限于直接父类
        printCollection3(list1);//√
        //printCollection3(list2);//×
        printCollection3(list3);//√
        //printCollection3(list4);//×
        //printCollection3(list5);//×

 
    }
    // ? extends AA 表示 上限，可以接受 AA 或者 AA 子类
    public static void printCollection2(List<? extends AA> c) { 
        for (Object object : c) {
    		System.out.println(object);
    	}
    }


    //说明: List<?> 表示 任意的泛型类型都可以接受
    public static void printCollection1(List<?> c) {
    	for (Object object : c) { // 通配符，取出时，就是 Object 
            System.out.println(object);
    	}
    }





    // ? super 子类类名 AA:支持 AA 类以及 AA 类的父类，不限于直接父类，
    //规定了泛型的下限
    public static void printCollection3(List<? super AA> c) { 
        for (Object object : c) {
    		System.out.println(object);
    	}
    }

}

class AA {
}
class BB extends AA {
}
class CC extends BB {
}
```



## 第十五章 坦克大战[1]

### 1. java绘图坐标体系

- 坐标体系-介绍

  ![image-20210928123758573](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928123758573.png)

- 坐标体系-像素

  ![image-20210928123821507](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928123821507.png)

- 案例

  ![image-20210928132711166](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928132711166.png)

  ```java
  package com.hspedu.draw;
  
  import javax.swing.*;
  import java.awt.*;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示如何在面板上画出圆形
  */ 
  @SuppressWarnings({"all"})
  public class DrawCircle extends JFrame { //JFrame 对应窗口,可以理解成是一个画框
  
      //定义一个面板
      private MyPanel mp = null;
  
      public static void main(String[] args) {
          new DrawCircle();
          System.out.println("退出程序~");
      }
  
      public DrawCircle() {//构造器
          //初始化面板
          mp = new MyPanel();
          //把面板放入到窗口(画框) 
          this.add(mp);
          //设置窗口的大小
          this.setSize(400, 300);
          // 当 点 击 窗 口 的 小 ×， 程 序 完 全 退 出 . 
          this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
          this.setVisible(true);//可以显示
      }
  }
  
  //1.先定义一个 MyPanel,  继承 JPanel 类， 画图形，就在面板上画
  class MyPanel extends JPanel {
          //说明:
      //1. MyPanel  对象就是一个画板
      //2. Graphics g  把 g  理解成一支画笔
      //3. Graphics  提供了很多绘图的方法
      //Graphics g 
      @Override
      public void paint(Graphics g) {//绘图方法
      	super.paint(g);//调用父类的方法完成初始化.
      	System.out.println("paint 方法被调用了~");
          //画出一个圆形.
          //g.drawOval(10, 10, 100, 100);
  
          //演示绘制不同的图形..
          //画直线 drawLine(int x1,int y1,int x2,int y2)
          //g.drawLine(10, 10, 100, 100);
          //画矩形边框 drawRect(int x, int y, int width, int height)
          //g.drawRect(10, 10, 100, 100);
          //画椭圆边框 drawOval(int x, int y, int width, int height)
          //填充矩形 fillRect(int x, int y, int width, int height)
          //设置画笔的颜色
          //	g.setColor(Color.blue);
          //	g.fillRect(10, 10, 100, 100);
  
  
          //填充椭圆 fillOval(int x, int y, int width, int height)
          //	g.setColor(Color.red);
          //	g.fillOval(10, 10, 100, 100);
  
  
          //画图片 drawImage(Image img, int x, int y, ..)
          //1. 获取图片资源, /bg.png 表示在该项目的根目录去获取 bg.png 图片资源
          //	Image image = Toolkit.getDefaultToolkit().getImage(Panel.class.getResource("/bg.png"));
          //	g.drawImage(image, 10, 10, 175, 221, this);
          //画字符串 drawString(String str, int x, int y)//写字
          //给画笔设置颜色和字体g.setColor(Color.red);
          g.setFont(new Font("隶书", Font.BOLD, 50));
          //这里设置的 100， 100， 是 "北京你好"左下角
          g.drawString("北京你好", 100, 100);
          //设置画笔的字体 setFont(Font font)
          //设置画笔的颜色 setColor(Color c)
  	}
  }
  ```

  

### 2. java绘图技术

- 绘图原理

  ![image-20210928151931162](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928151931162.png)

- Graphics 类

  ![image-20210928152140631](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928152140631.png)

- 绘出坦克

  ```java
  package com.yt.tankgame;
  
  /**
   * @author Yt
   * @version 1.0
   */
  public class Tank {
      private int x;
      private int y;
  
      public Tank(int x, int y) {
          this.x = x;
          this.y = y;
      }
  
      public int getX() {
          return x;
      }
  
      public void setX(int x) {
          this.x = x;
      }
  
      public int getY() {
          return y;
      }
  
      public void setY(int y) {
          this.y = y;
      }
  }
  ==================================
  package com.yt.tankgame;
  
  /**
   * @author Yt
   * @version 1.0
   */
  public class MyTank extends Tank {
      public MyTank(int x, int y) {
          super(x, y);
      }
  }
  ===============================
  package com.yt.tankgame;
  
  import javax.swing.*;
  import java.awt.*;
  
  /**
   * @author Yt
   * @version 1.0
   */
  public class MyPanel extends JPanel {
      MyTank mt = null;
  
      public MyPanel(){
          mt = new MyTank(100,100);
      }
  
      @Override
      public void paint(Graphics g) {
          super.paint(g);
  
          g.fillRect(0,0,500,600);
  
          Drawtank(mt.getX(),mt.getY(),g,0,0);
  
      }
  
      public void Drawtank(int x,int y,Graphics g,int direct,int type){
  
          switch (type){
              case 0:
                  g.setColor(Color.cyan);
                  break;
              case 1:
                  g.setColor(Color.YELLOW);
                  break;
          }
  
          switch (direct){
              case 0:
                  g.fill3DRect(x, y, 10, 60, false);//画出坦克左边轮子
                  g.fill3DRect(x + 30, y, 10, 60, false);//画出坦克右边轮子
                  g.fill3DRect(x + 10, y + 10, 20, 40, false);//画出坦克盖子
                  g.fillOval(x + 10, y + 20, 20, 20);//画出圆形盖子
                  g.drawLine(x + 20, y + 30, x + 20, y);//画出炮筒
                  break;
              default:
                  System.out.println("暂时没处理");
          }
  
      }
  }
  =====================================
  package com.yt.tankgame;
  
  import javax.swing.*;
  
  /**
   * @author Yt
   * @version 1.0
   */
  public class TankGame01 extends JFrame {
  
      private MyPanel mp = null;
  
      public TankGame01(){
          mp = new MyPanel();
          this.add(mp);//把面板(就是游戏的绘图区域)
          this.setSize(500, 600);
          this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
          this.setVisible(true);
      }
  
  
      public static void main(String[] args){
  
          new TankGame01();
      }
  }
  ```

  

### 3. java事件处理机制

- 基本说明

  ![image-20210928161202109](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928161202109.png)

- 示意图

  ![image-20210928161241250](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928161241250.png)

- 机制分析

  ![image-20210928161331061](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928161331061.png)

- 事件处理机制深入理

  ![image-20210928161553352](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928161553352.png)

  ![image-20210928161809798](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928161809798.png)

  ![image-20210928161837095](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928161837095.png)



### 4. 坦克大战游戏(1.0版)

- 见 IDEA.



## 第十六章 多线程基础

### 1. 线程介绍

- 程序(program)

  ![image-20210928190742761](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928190742761.png)

- 进程

  ![image-20210928190805327](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928190805327.png)

- 什么是线程

  ![image-20210928190824894](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928190824894.png)

- 其他相关概念

  ![image-20210928192026252](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928192026252.png)

  ![image-20210928192058978](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928192058978.png)

### 2. 线程创建

- 创建线程的两种方式

  ![image-20210928193039533](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928193039533.png)

  1. 线程应用案例 1-继承Thread 类

     ![image-20210928195516056](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928195516056.png)

     ![image-20210928210640861](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928210640861.png)

     ```java
     package com.hspedu.threaduse;
     
     /**
     *@author 韩顺平
     *@version 1.0
     *演示通过继承 Thread 类创建线程
     */
     public class Thread01 {
         public static void main(String[] args) throws InterruptedException {
             //创建 Cat 对象，可以当做线程使用
             Cat cat = new Cat();
     
             //老韩读源码
             /*
             (1)
             public synchronized void start() {
             	start0();
             } 
             (2)
             //start0() 是本地方法，是 JVM 调用,  底层是 c/c++实现
             //真正实现多线程的效果， 是 start0(), 而不是 run 
             private native void start0();
             */
     
             cat.start();//启动线程-> 最终会执行 cat 的 run 方法
     
     
     
             //cat.run();//run 方法就是一个普通的方法, 没有真正的启动一个线程，就会把 run 方法执行完毕，才向下执行
             
             //说明: 当 main 线程启动一个子线程 Thread-0, 主线程不会阻塞,  会继续执行
             //这时 主线程和子线程是交替执行..
             System.out.println("主线程继续执行" + Thread.currentThread().getName());//名字 main 
             for(int i = 0; i < 60; i++) {
             	System.out.println("主线程 i=" + i);
             	//让主线程休眠
                 Thread.sleep(1000);
             }
         }
     }
     
     
     
     //老韩说明
     //1. 当一个类继承了 Thread  类， 该类就可以当做线程使用
     //2. 我们会重写 run 方法，写上自己的业务代码
     //3. run  Thread 类 实现了 Runnable 接口的 run 方法
     /*
     @Override
     public void run() {
     	if (target != null) {
         	target.run();
     	}
     }
     */
     
     class Cat extends Thread {
     
         int times = 0;
         @Override
         public void run() {//重写 run 方法，写上自己的业务逻辑
     
     
             while (true) {
                 //该线程每隔 1 秒。在控制台输出 “喵喵,  我是小猫咪”
                 System.out.println("喵喵, 我是小猫咪" + (++times) + " 线程名=" + 	Thread.currentThread().getName());
                 //让该线程休眠 1 秒 ctrl+alt+t 
                 try {
                     Thread.sleep(1000);
                 } catch (InterruptedException e) { 
                     e.printStackTrace();
                 }
                 if(times == 80) {
                     break;//当 times 到 80,  退出 while, 这时线程也就退出..
                 }
             }
         }
     }
     ```

     ![image-20210928200616902](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928200616902.png)

     

  2. 线程应用案例 2-实现Runnable 接口

     ![image-20210928203859550](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928203859550.png)

     <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928203921249.png" alt="image-20210928203921249" style="zoom:67%;" />

     ```java
     package com.hspedu.threaduse;
     /**
     *@author 韩顺平
     *@version 1.0
     *通过实现接口 Runnable 来开发线程
     */
     public class Thread02 {
         public static void main(String[] args) { 
             Dog dog = new Dog();
             //dog.start(); 这里不能调用 start
             
             //创建了 Thread 对象，把 dog 对象(实现 Runnable),放入 Thread 
             Thread thread = new Thread(dog);
             thread.start();
     
             //	Tiger tiger = new Tiger();//实现了 Runnable
             //	ThreadProxy threadProxy = new ThreadProxy(tiger);
             //	threadProxy.start();
         }
     }
     
     
     class Animal {
     }
     
     class Tiger extends Animal implements Runnable {
     
         @Override
         public void run() {
         	System.out.println("老虎嗷嗷叫	");
         }
     }
     
     
     //线程代理类 , 模拟了一个极简的 Thread 类
     class ThreadProxy implements Runnable {//你可以把 Proxy 类当做 ThreadProxy
     
     
         private Runnable target = null;//属性，类型是 Runnable
     
         @Override
         public void run() {
         	if (target != null) {
         		target.run();//动态绑定（运行类型 Tiger）
         	}
         }  
         
         public ThreadProxy(Runnable target) { 
             this.target = target;
         }
     
         public void start() {
         	start0();//这个方法时真正实现多线程方法
         }
     
         public void start0() { 
             run();
         }
     }
     
     
     
     class Dog implements Runnable { //通过实现 Runnable 接口，开发线程
     
         int count = 0;
     
         @Override
         public void run() { //普通方法
             while (true) {
         		System.out.println("小狗汪汪叫..hi" + (++count) + Thread.currentThread().getName());
     
                 //休眠 1 秒
                 try {
                 	Thread.sleep(1000);
                     } catch (InterruptedException e) {
                     	e.printStackTrace();
                 }
                 if (count == 10) {
                     break;
                 }
             }
         }
     }
     ```

     

- 继承 Thread vs 实现 Runnable 的区别

  ![image-20210928210716985](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928210716985.png)

### 3. 线程终止

- 基本说明

  ![image-20210928212928387](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928212928387.png)

- 案例

  ![image-20210928212950832](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928212950832.png)

### 4. 线程方法

- 常用方法第一组

  ![image-20210928213855215](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928213855215.png)

  - 注意事项和细节

    ![image-20210928213939929](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928213939929.png)

  - 应用案例

    ![image-20210928215231177](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928215231177.png)

- 常用方法第二组

  ![image-20210928215257431](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928215257431.png)

  - 案例

    ![image-20210928215323486](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928215323486.png)



### 5. 用户线程和守护线程

![image-20210928221927417](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928221927417.png)

- 案例

  ![image-20210928221948861](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928221948861.png)





### 6. 线程的生命周期

- JDK 中用Thread.State 枚举表示了线程的几种状态

  ![image-20210928223059664](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928223059664.png)

- 线程状态转换图

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928223157978.png" alt="image-20210928223157978" style="zoom: 200%;" />

### 7. Synchronized

- 线程同步机制

  ![image-20210928225053676](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928225053676.png)

  

- 同步具体方法-Synchronized

  ![image-20210928225131420](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210928225131420.png)

### 8. 互斥锁 （重要)

- 分析同步原理

  ![image-20210929133620636](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210929133620636.png)

  这里的锁是非公平锁（比如说 t1 线程返回对象锁后还可能继续拿到锁执行同步方法或同步代码块的，不保证公平）

- 互斥锁

  - 基本介绍

    ![image-20210929133742031](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210929133742031.png)

  - 使用互斥锁来解决售票问题(代码块加锁，方法上加锁)

    ```java
    package com.hspedu.syn;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *使用多线程，模拟三个窗口同时售票 100 张
    */
    public class SellTicket {
        public static void main(String[] args) {
    
            //测试
            //	SellTicket01 sellTicket01 = new SellTicket01();
            //	SellTicket01 sellTicket02 = new SellTicket01();
            //	SellTicket01 sellTicket03 = new SellTicket01();
            //
            //	//这里我们会出现超卖..
            //	sellTicket01.start();//启动售票线程
            //	sellTicket02.start();//启动售票线程
            //	sellTicket03.start();//启动售票线程
    
    
    
            //	System.out.println("===使用实现接口方式来售票=====");
            //	SellTicket02 sellTicket02 = new SellTicket02();
            //
            //	new Thread(sellTicket02).start();//第 1 个线程-窗口
            //	new Thread(sellTicket02).start();//第 2 个线程-窗口
            //	new Thread(sellTicket02).start();//第 3 个线程-窗口
    
    
            //测试一把
            SellTicket03 sellTicket03 = new SellTicket03(); 
            new Thread(sellTicket03).start();//第 1 个线程-窗口
            new Thread(sellTicket03).start();//第 2 个线程-窗口
            new Thread(sellTicket03).start();//第 3 个线程-窗口
    
        }
    }
    
    
    //实现接口方式, 使用 synchronized 实现线程同步
    class SellTicket03 implements Runnable {
        private int ticketNum = 100;//让多个线程共享 ticketNum
        private boolean loop = true;//控制 run 方法变量
        Object object = new Object();
    
    
        //同步方法（静态的）的锁为当前类本身
        //老韩解读
        //1. public synchronized static void m1() {}  锁是加在 SellTicket03.class
        //2. 如果在静态方法中，实现一个同步代码块.
        /*
        synchronized (SellTicket03.class) { 
        	System.out.println("m2");
        }
        */
        public synchronized static void m1() {
        }
        public static	void m2() {
        	synchronized (SellTicket03.class) {
                System.out.println("m2");
        	}
        }
    
    
        //老韩说明
        //1. public synchronized void sell() {} 就是一个同步方法
        //2. 这时锁在 this 对象
        //3. 也可以在代码块上写 synchronize ,同步代码块,  互斥锁还是在 this 对象
        public /*synchronized*/ void sell() { //同步方法,  在同一时刻， 只能有一个线程来执行 sell 方法
        	synchronized (/*this*/ object) { 
                if (ticketNum <= 0) {
        			System.out.println("售票结束...");
        			loop = false;
                    return;
        		}
    
                //休眠 50 毫秒,  模拟
                try {
                	Thread.sleep(50);
                } catch (InterruptedException e) { 
                    e.printStackTrace();
                }
                
                System.out.println("窗口 " + Thread.currentThread().getName() + "  售出一张票"
                + " 剩余票数=" + (--ticketNum));//1 - 0 - -1	- -2
            }
        }
    
    
        	@Override
        	public void run() { 
                while (loop) {
            		sell();//sell 方法是一共同步方法
                }
        	}
    }
    
    
    //使用 Thread 方式
    // new SellTicket01().start();  
    // new SellTicket01().start(); //创建不同对象
    //会出现超卖！
    class SellTicket01 extends Thread {
    
        private static int ticketNum = 100;//让多个线程共享 ticketNum
    
    
        //	public void m1() {
        //		synchronized (this) {
        //			System.out.println("hello");
        //		}
        //	}
    
    
        @Override
        public void run() {
        	while (true) {
    
                if (ticketNum <= 0) {
                	System.out.println("售票结束...");
                    break;
                }
    
                //休眠 50 毫秒,  模拟
                try {
                	Thread.sleep(50);
                } catch (InterruptedException e) { 
                    e.printStackTrace();
                }
    
                System.out.println("窗口 " + Thread.currentThread().getName() + "  售出一张票"
                	+ " 剩余票数=" + (--ticketNum));//1 - 0 - -1	- -2
    
    
                }
        }
    }
    ```

    

- 注意事项和细节

  ![image-20210929143226298](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210929143226298.png)



### 9. 死锁

- 基本介绍

  ![image-20210929145529999](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210929145529999.png)

- 案例  （重要，死锁实现代码 要理解记住！！！）

  ```java
  package com.hspedu.syn;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *模拟线程死锁
  */
  public class DeadLock_ {
      public static void main(String[] args) {
          //模拟死锁现象
          DeadLockDemo A = new DeadLockDemo(true);
          A.setName("A 线程");
          DeadLockDemo B = new DeadLockDemo(false);
          B.setName("B 线程"); 
          A.start();
          B.start();
      }
  }
  
  
  //线程
  class DeadLockDemo extends Thread {
      static Object o1 = new Object();// 保证多线程，共享一个对象,这里使用 static 
      static Object o2 = new Object();
      boolean flag;
  
  
      public DeadLockDemo(boolean flag) {//构造器
          this.flag = flag;
      }
  
  
      @Override
      public void run() {
  
      //下面业务逻辑的分析
      //1. 如果 flag 为 T, 线程 A 就会先得到/持有 o1  对象锁,  然后尝试去获取 o2  对象锁
      //2. 如果线程 A 得不到 o2  对象锁，就会 Blocked
      //3. 如果 flag 为 F, 线程 B  就会先得到/持有 o2  对象锁,  然后尝试去获取 o1  对象锁
      //4. 如果线程 B 得不到 o1 对象锁，就会 Blocked 
          if (flag) {
      		synchronized (o1) {//对象互斥锁,  下面就是同步代码
                  System.out.println(Thread.currentThread().getName() + " 进入 1"); 
                  synchronized (o2) { //  这里获得 li 对象的监视权
      				System.out.println(Thread.currentThread().getName() + " 进入 2");
      			}
  
  
      		}
      	} else {
      		synchronized (o2) { 
                  System.out.println(Thread.currentThread().getName() + " 进入 3"); 
                  synchronized (o1) { //  这里获得 li 对象的监视权
      				System.out.println(Thread.currentThread().getName() + " 进入 4");
      			}
      		}
      	}
      }
  }
  ```
  
  

### 10. 释放锁

- 下面操作会释放锁

  ![image-20210929150447973](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210929150447973.png)

- 下面操作不会释放锁

  ![image-20210929150512387](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20210929150512387.png)



## 第十七章 IO流

### 1. 文件

- 文件是保存数据的地方；

- 文件流

  ![image-20211002143012031](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002143012031.png)



- 常用的文件操作

  - 创建文件对象相关构造器和方法

    ![image-20211002145700553](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002145700553.png)

  - 案例

    ```java 
    package com.hspedu.file;
    
    import org.junit.jupiter.api.Test;
    import java.io.*;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *演示创建文件
    */
    public class FileCreate {
        public static void main(String[] args) {
        }
    
    
        //方式 1 new File(String pathname)
        @Test
        public void create01() {
            String filePath = "e:\\news1.txt"; 
            File file = new File(filePath);
    
            try {
            	file.createNewFile();
            	System.out.println("文件创建成功");
            } catch (IOException e) { 
                e.printStackTrace();
            }
    
        }
        
        
        //方式 2 new File(File parent,String child) //根据父目录文件+子路径构建
        //e:\\news2.txt 
        @Test
        public	void create02() {
            File parentFile = new File("e:\\");
            String fileName = "news2.txt";
            //这里的 file 对象，在 java 程序中，只是一个对象
            //只有执行了 createNewFile 方法，才会真正的，在磁盘创建该文件
            File file = new File(parentFile, fileName);
            try {
            	file.createNewFile();
            	System.out.println("创建成功~");
            } catch (IOException e) { 
                e.printStackTrace();
            }
        }
    
    
        //方式 3 new File(String parent,String child) //根据父目录+子路径构建
        @Test
        public void create03() {
            //String parentPath = "e:\\"; 
            String parentPath = "e:\\";
            String fileName = "news4.txt"; 
            File file = new File(parentPath, fileName);
    
            try {
                file.createNewFile();
                System.out.println("创建成功~");
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    
        //下面四个都是抽象类
        //InputStream
        //OutputStream
        //Reader //字符输入流
        //Writer	//字符输出流
    }
    ```

    

  - 获取文件的相关信息

    ![image-20211002151728037](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002151728037.png)

    ![image-20211002151746947](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002151746947.png)

  - 目录的操作和文件删除

    ![image-20211002152202937](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002152202937.png)

    

### 2. IO流原理及流的分类

- Java IO 流原理

  ![image-20211002154215878](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002154215878.png)

- 流的分类

  ![image-20211002154409141](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002154409141.png)



- IO 流体系图

  ![image-20211002154629367](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002154629367.png)

### 3. 节点流和处理流

- 基本介绍

  ![image-20211002190354859](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002190354859.png)

- 节点流和处理流一览图

  ![image-20211002190653422](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002190653422.png)

- 节点流和处理流的区别和联系

  ![image-20211002191049815](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002191049815.png)

- 处理流的功能主要体现在以下两个方面:

  ![image-20211002191402526](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002191402526.png)



### 4. 输入流(InputStream, Reader)

#### 1. 字节流-InputStream

- 节点流-FileInputStream 介绍

  - 案例：请使用 FileInputStream  读取 hello.txt 文件，并将文件内容显示到控制台

  ```java
  package com.hspedu.inputstream_;
  
  import org.junit.jupiter.api.Test;
  import java.io.FileInputStream;
  import java.io.FileNotFoundException; 
  import java.io.IOException;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 FileInputStream 的使用(字节输入流 文件--> 程序)
  */
  public class FileInputStream_ {
      public static void main(String[] args) {
  
      }
  
      /**
      *演示读取文件...
      *单个字节的读取，效率比较低
      */ 
      @Test
      public void readFile01() {
          String filePath = "e:\\hello.txt";
          int readData = 0;
          FileInputStream fileInputStream = null; 
          try {
          	//创建 FileInputStream  对象，用于读取 文件
          	fileInputStream = new FileInputStream(filePath);
          	//从该输入流读取一个字节的数据。 如果没有输入可用，此方法将阻止。
          	//如果返回-1 ,  表示读取完毕
          	while ((readData = fileInputStream.read()) != -1) {
          		System.out.print((char)readData);//转成 char 显示
          	}
          } catch (IOException e) { 
              e.printStackTrace();
          } finally {
          	//关闭文件流，释放资源.
              try {
              	fileInputStream.close();
              } catch (IOException e) { 
                  e.printStackTrace();
              }
          }
      }
  
  
      
      /**
      * 使用 read(byte[] b) 读取文件，提高效率
      */ 
      @Test
      public void readFile02() {
          String filePath = "e:\\hello.txt";
          //字节数组
          byte[] buf = new byte[8]; //一次读取 8 个字节.
          int readLen = 0;  //实际读取的 字节数
          FileInputStream fileInputStream = null; 
          try {
              //创建 FileInputStream  对象，用于读取 文件
              fileInputStream = new FileInputStream(filePath);
              //从该输入流读取最多 buf.length 字节的数据到字节数组。 此方法将阻塞，直到某些输入可用。
              //如果返回-1 ,  表示读取完毕
              //如果读取正常, 返回实际读取的 字节数
          	while ((readLen = fileInputStream.read(buf)) != -1) {
          		System.out.print(new String(buf, 0, readLen));//显示
          	}
          } catch (IOException e) {
              e.printStackTrace();
          } finally {
              //关闭文件流，释放资源. 
              try {
              	fileInputStream.close();
          	} catch (IOException e) { 
                  e.printStackTrace();
          	}
          }
      }
  }    
  ```

- 处理流-BufferedInputStream

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002204635877.png" alt="image-20211002204635877" style="zoom: 80%;" />

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002204612302.png" alt="image-20211002204612302" style="zoom: 80%;" />

  

- 对象处理流-ObjectInputStream

  ![image-20211002211459195](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002211459195.png)

  ![image-20211002211528823](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002211528823.png)

  - 对象流介绍

    功能：提供了对基本类型或对象类型的序列化和反序列化的方法；
    ObjectOutputStream  提供 序列化功能
    ObjectInputStream  提供 反序列化功能

    ![image-20211002211734917](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002211734917.png)

    案例：![image-20211003185117378](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003185117378.png)

    ```java
    // 1.创建流对象
    ObjectInputStream ois = new ObjectInputStream(new FileInputStream("e:\\data.dat"));
    // 2.读取， 注意顺序(读取的顺序要和保存数据的顺序一致，否则会出现异常)
    System.out.println(ois.readInt()); 
    System.out.println(ois.readBoolean()); 
    System.out.println(ois.readChar()); 
    System.out.println(ois.readDouble());
    System.out.println(ois.readUTF()); 
    System.out.println(ois.readObject()); 
    
    // 3.关闭
    ois.close();
    System.out.println("以反序列化的方式读取(恢复)ok~");
    ```

  - 细节说明：

    ![image-20211003191239476](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003191239476.png)			

- 标准输入输出流

  ![image-20211003192211669](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003192211669.png)

  ![image-20211003192220147](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003192220147.png)



#### 2. 字符流-Reader

- FileReader

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002172933309.png" alt="image-20211002172933309" style="zoom:50%;" />

  - FileReader 相关方法

    ![image-20211002173402839](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002173402839.png)

  - 案例：使用 FileReader 从 story.txt 读取内容，并显示

    ```java
    package com.hspedu.reader_;
    
    import org.junit.jupiter.api.Test;
    import java.io.FileNotFoundException; 
    import java.io.FileReader;
    import java.io.FileWriter;
    import java.io.IOException;
    
    public class FileReader_ {
        public static void main(String[] args) {
        }
    
        /**
        * 单个字符读取文件
        */ 
        @Test
        public void readFile01() {
            String filePath = "e:\\story.txt";
            FileReader fileReader = null; 
            int data = 0;
            //1. 创建 FileReader 对象
            try {
            	fileReader = new FileReader(filePath);
            	//循环读取 使用 read, 单个字符读取
                while ((data = fileReader.read()) != -1) { 
                    System.out.print((char) data);
            	}
            } catch (IOException e) { 
                e.printStackTrace();
            } finally {
                try {
                	if (fileReader != null) { 
                        fileReader.close();
                	}
                } catch (IOException e) { 
                    e.printStackTrace();
                }
            }
        }
    
    
        /**
        * 字符数组读取文件
        */ 
        @Test
        public void readFile02() {
            System.out.println("~~~readFile02 ~~~"); 
            String filePath = "e:\\story.txt"; 
            FileReader fileReader = null;
    
            int readLen = 0;
            char[] buf = new char[8];
            //1. 创建 FileReader 对象   
            try {
            	fileReader = new FileReader(filePath);
            	//循环读取 使用 read(buf), 返回的是实际读取到的字符数
            	//如果返回-1, 说明到文件结束
            	while ((readLen = fileReader.read(buf)) != -1) {
                    System.out.print(new String(buf, 0, readLen));
            	}
            } catch (IOException e) {
                e.printStackTrace();
            } finally {
                try {
                	if (fileReader != null) { 
                        fileReader.close();
                	}
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }                          
    ```

    

- 处理流-BufferedReader 

  ![image-20211002195725043](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002195725043.png)

  ![image-20211002195735686](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002195735686.png)

  ```java
  package com.hspedu.reader_;
  
  import java.io.BufferedReader; 
  import java.io.FileReader;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 bufferedReader 使用
  */
  public class BufferedReader_ {
      public static void main(String[] args) throws Exception {
  
  
          String filePath = "e:\\a.java";
          //创建 bufferedReader
          BufferedReader bufferedReader = new BufferedReader(new FileReader(filePath));
          //读取
          String line; //按行读取,  效率高
          //说明
          //1. bufferedReader.readLine() 是按行读取文件
          //2. 当返回 null 时，表示文件读取完毕
          while ((line = bufferedReader.readLine()) != null) { 
              System.out.println(line);
          }
  
          //关闭流, 这里注意，只需要关闭 BufferedReader ，因为底层会自动的去关闭 节点流
          //FileReader。
          /*
          public void close() throws IOException {
              synchronized (lock) {
              	if (in == null)
              		return;
              	try {
              		in.close();//in 就是我们传入的 new FileReader(filePath), 关闭了.
              	} finally {
              		in = null; 
              		cb = null;
              	}
              }
          }
          */
          bufferedReader.close();
      }
  }    
  ```

  
  
- 转换流-InputStreamReader （要记住它的转换特性 很重要！！！）

  - 先看一个文件乱码问题，引出学习转换流必要性.

    ```java
    import java.io.*;
    
    public class CodeQuestion {
        public static void main(String[] args) throws IOException {
            //读取 e:\\a.txt  文件到程序
            //思路
            //1. 创建字符输入流 BufferedReader [处理流]
            //2. 使用 BufferedReader 对象读取 a.txt
            //3. 默认情况下，读取文件是按照 utf-8  编码
            String filePath = "e:\\a.txt";
            BufferedReader br = new BufferedReader(new FileReader(filePath));
    
            String s = br.readLine();
            System.out.println("读取到的内容: " + s); br.close();
    
            //InputStreamReader
            //OutputStreamWriter
        }
    }
    ```

    结果：出现乱码

    ![image-20211003195710922](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003195710922.png)

    原因：a.txt的编码是gbk，而默认情况下，读取文件是按照 utf-8  编码，所以出现乱码；

    So：引出转换流，可以指定编码格式去读取文件。

  - 介绍

    ![image-20211003200215029](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003200215029.png)

  - 案例

    ![image-20211003200245930](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003200245930.png)

    ```java
    package com.hspedu.transformation;
    
    import java.io.*;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *演示使用 InputStreamReader 转换流解决中文乱码问题
    *将字节流 FileInputStream 转成字符流	InputStreamReader, 指定编码 gbk/utf-8
    */
    public class InputStreamReader_ {
        public static void main(String[] args) throws IOException {
    
            String filePath = "e:\\a.txt";
            //解读
            //1. 把 FileInputStream  转成 InputStreamReader
            //2. 指定编码 gbk
            //InputStreamReader isr = new InputStreamReader(new FileInputStream(filePath), "gbk");
            //3. 把 InputStreamReader 传入 BufferedReader
            //BufferedReader br = new BufferedReader(isr);
    
            //将 2  和 3  合在一起
            BufferedReader br = new BufferedReader(new InputStreamReader(
            											new FileInputStream(filePath), "gbk"));
    
            //4. 读取
            String s = br.readLine();
            System.out.println("读取内容=" + s);
            //5. 关闭外层流
            br.close();
        }
    }
    ```

    







### 5. 输出流(OutputStream, Writer)

#### 1. 字节流-OutputStream

- FileOutputStream 介绍

![image-20211002165151666](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002165151666.png)

​		案例1：请使用 FileOutputStream 在 a.txt 文件，中写入 “hello，world”. [老师代码演示], 如果文件不存在，会创建文件(注意：前提是目录已经存在.)

```java
/**
*演示使用 FileOutputStream  将数据写到文件中,
*如果该文件不存在，则创建该文件
*/ 
@Test
public void writeFile() {

    //创建 FileOutputStream 对象
    String filePath = "e:\\a.txt"; 
    FileOutputStream fileOutputStream = null; 
    try {
        //得到 FileOutputStream 对象 
        //老师说明
        //1. new FileOutputStream(filePath) 创建方式，会覆盖原来的内容
        //2. new FileOutputStream(filePath, true) 创建方式，是追加到文件后面
        fileOutputStream = new FileOutputStream(filePath, true);
        //写入一个字节
        //fileOutputStream.write('H');//
        //写入字符串
        String str = "hsp,world!";
        //str.getBytes() 可以把 字符串-> 字节数组
        //fileOutputStream.write(str.getBytes());
        /*
        write(byte[] b, int off, int len) 将 len 字节从位于偏移量 off 的指定字节数组写入此文件输出流
        */
        fileOutputStream.write(str.getBytes(), 0, 3);
    } catch (IOException e) { 
        e.printStackTrace();
    } finally {
        try {
         	fileOutputStream.close();
        } catch (IOException e) { 
            e.printStackTrace();
        }
    }
} 
```

​		案例2：编程完成图片/音乐 的拷贝.

```java
package com.hspedu.outputstream_;

import com.hspedu.inputstream_.FileInputStream_;
import java.io.*;

public class FileCopy {
    public static void main(String[] args) {
        //完成 文件拷贝，将 e:\\Koala.jpg  拷贝到 e:\\Koala3.jpg
        //思路分析
        //1. 创建文件的输入流 , 将文件读入到程序
        //2. 创建文件的输出流， 将读取到的文件数据，写入到指定的文件. 
        String srcFilePath = "e:\\Koala.jpg";
        String destFilePath = "e:\\Koala3.jpg"; 
        FileInputStream fileInputStream = null; 
        FileOutputStream fileOutputStream = null;

        try {
            fileInputStream = new FileInputStream(srcFilePath); 
            fileOutputStream = new FileOutputStream(destFilePath);
            //定义一个字节数组,提高读取效果
            byte[] buf = new byte[1024]; 
            int readLen = 0;
            while ((readLen = fileInputStream.read(buf)) != -1) {
                //读取到后，就写入到文件 通过 fileOutputStream
                //即，是一边读，一边写
                fileOutputStream.write(buf, 0, readLen);//一定要使用这个方法
            }
            System.out.println("拷贝 ok~");
        } catch (IOException e) { 
            e.printStackTrace();
        } finally {
            try {
                //关闭输入流和输出流，释放资源
                if (fileInputStream != null) {
                	fileInputStream.close();
            	}
            	if (fileOutputStream != null) {
                    fileOutputStream.close();
            	}
            } catch (IOException e) { 
                e.printStackTrace();
            }
        }
    }
}    
```

- 处理流-BufferedOutputStream

  ![image-20211002205042649](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002205042649.png)

  - 案例：编程完成图片/视频 的拷贝.

    ```java
    import java.io.*;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *演示使用 BufferedOutputStream  和 BufferedInputStream 使用
    *使用他们，可以完成二进制文件拷贝.
    *
    *思考：字节流可以操作二进制文件，可以操作文本文件吗？当然可以
    */
    
    public class BufferedCopy02 {
        public static void main(String[] args) {
    
            //	String srcFilePath = "e:\\Koala.jpg";
            //	String destFilePath = "e:\\hsp.jpg";
            //	String srcFilePath = "e:\\0245_韩顺平零基础学 Java_引出 this.avi";
            //	String destFilePath = "e:\\hsp.avi"; 
            String srcFilePath = "e:\\a.java"; 
            String destFilePath = "e:\\a3.java";
    
            //创建 BufferedOutputStream 对象 BufferedInputStream 对象
            BufferedInputStream bis = null; 
            BufferedOutputStream bos = null;
    
            try {
                //因为 FileInputStream	是 InputStream  子类
                bis = new BufferedInputStream(new FileInputStream(srcFilePath));
                bos = new BufferedOutputStream(new FileOutputStream(destFilePath));
    
                //循环的读取文件，并写入到 destFilePath
                byte[] buff = new byte[1024];
                int readLen = 0;
                //当返回 -1 时，就表示文件读取完毕
                while ((readLen = bis.read(buff)) != -1) { 
                    bos.write(buff, 0, readLen);
                }
                System.out.println("文件拷贝完毕~~~");
            } catch (IOException e) { 
                e.printStackTrace();
            } finally {
                //关闭流 ,  关闭外层的处理流即可，底层会去关闭节点流
                try {
                	if(bis != null) {
                		bis.close();
                	}
                	if(bos != null) {
                		bos.close();
                	}
                } catch (IOException e) { 
                    e.printStackTrace();   
                }
            }
        }
    }
    ```

  
  
- 对象处理流-ObjectOutputStream

  ObjectOutputStream 提供 序列化功能

  ![image-20211003184428685](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003184428685.png)

  ![image-20211003184441571](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003184441571.png)

  ```java
  
  import java.io.FileOutputStream;
  import java.io.ObjectOutputStream; 
  import java.io.Serializable;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 ObjectOutputStream 的使用,  完成数据的序列化
  */
  public class ObjectOutStream_ {
      public static void main(String[] args) throws Exception {
      	//序列化后，保存的文件格式，不是存文本，而是按照他的格式来保存
          String filePath = "e:\\data.dat";
          ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(filePath));
  
          //序列化数据到 e:\data.dat
          oos.writeInt(100);// int -> Integer ( 实 现 了 Serializable) 
          oos.writeBoolean(true);// boolean -> Boolean (实现了 Serializable)
          oos.writeChar('a');// char -> Character ( 实 现 了 Serializable)
          oos.writeDouble(9.5);// double -> Double (实现了 Serializable)
          oos.writeUTF("韩顺平教育");//String
          //保存一个 dog 对象
          oos.writeObject(new Dog("旺财", 10)); 
          oos.close();
          System.out.println("数据保存完毕(序列化形式)");
      }
  }  
  ```

  

- 打印流-PrintStream

  打印流只有输出流，没有输入流

  - ![image-20211003202317516](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003202317516.png)

  - 案例

    ```java
    package com.hspedu.printstream;
    
    import java.io.IOException; 
    import java.io.PrintStream;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *演示 PrintStream  （字节打印流/输出流）
    */
    public class PrintStream_ {
        public static void main(String[] args) throws IOException {
    
            PrintStream out = System.out;
            //在默认情况下，PrintStream 输出数据的位置是 标准输出，即显示器
            /*
            public void print(String s) { 
            	if (s == null) {
            		s = "null";
            	}
            	write(s);
            }
            */
            out.print("john, hello");
            //因为 print 底层使用的是 write ,  所以我们可以直接调用 write 进行打印/输出
            out.write("韩顺平,你好".getBytes()); 
            out.close();
    
            //我们可以去修改打印流输出的位置/设备
            //1. 输出修改成到 "e:\\f1.txt"
            //2. "hello,  韩顺平教育~"  就会输出到 e:\f1.txt
            //3. public static void setOut(PrintStream out) {
            //		checkIO();
            //		setOut0(out); // native 方法，修改了 out
            //	}
            System.setOut(new PrintStream("e:\\f1.txt"));
            System.out.println("hello, 韩顺平教育~");
        }
    }
    ```

    







#### 2. 字符流-Writer

- FileWriter介绍

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002173247794.png" alt="image-20211002173247794" style="zoom:50%;" />

  - FileWriter 常用方法

    ![image-20211002173335121](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002173335121.png)

  - 案例：使用 FileWriter 将 “风雨之后，定见彩虹” 写入到 note.txt 文件中, 注意细节

    ```java
    
    import java.io.FileWriter;
    import java.io.IOException;
    
    public class FileWriter_ {
        public static void main(String[] args) {
    
            String filePath = "e:\\note.txt";
            //创建 FileWriter 对象
            FileWriter fileWriter = null; 
            char[] chars = {'a', 'b', 'c'}; 
            try {
            fileWriter = new FileWriter(filePath);//默认是覆盖写入
            //	3) write(int):写入单个字符
            fileWriter.write('H');
            //	4) write(char[]):写入指定数组
            fileWriter.write(chars);
            //	5) write(char[],off,len):写入指定数组的指定部分
            fileWriter.write("韩顺平教育".toCharArray(), 0, 3);
            //	6) write（string）：写入整个字符串
            fileWriter.write(" 你好北京~");
            fileWriter.write("风雨之后，定见彩虹");
            //	7) write(string,off,len):写入字符串的指定部分
            fileWriter.write("上海天津", 0, 2);
            //在数据量大的情况下，可以使用循环操作.
            } catch (IOException e) { 
                e.printStackTrace();
            } finally {
                //对应 FileWriter , 一定要关闭流，或者 flush 才能真正的把数据写入到文件
                //老韩看源码就知道原因.
                /*
                看看代码
                private void writeBytes() throws IOException { 
                    this.bb.flip();
                    int var1 = this.bb.limit();
                    int var2 = this.bb.position();
    
                    assert var2 <= var1;
    
                    int var3 = var2 <= var1 ? var1 - var2 : 0; 
                    if (var3 > 0) {
                        if (this.ch != null) {
                            assert this.ch.write(this.bb) == var3 : var3;
                        } else {
                            this.out.write(this.bb.array(), this.bb.arrayOffset() + var2, var3);   
                        }
                    }
                this.bb.clear();
                }
                */ 
                try {
                    //fileWriter.flush();
                    //关闭文件流，等价 flush() + 关闭
                    fileWriter.close();
                } catch (IOException e) { 
                    e.printStackTrace();
                }
    
            }
            System.out.println("程序结束...");
    
        }
    }
    ```

    

- 处理流-BufferedWriter

  ![image-20211002200429728](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002200429728.png)

  ```java
  package com.hspedu.writer_;
  
  
  import java.io.BufferedWriter; 
  import java.io.FileWriter; 
  import java.io.IOException;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 BufferedWriter 的使用
  */
  public class BufferedWriter_ {
      public static void main(String[] args) throws IOException { 
          String filePath = "e:\\ok.txt";
          //创建 BufferedWriter
          //说明:
          //1. new FileWriter(filePath, true) 表示以追加的方式写入
          //2. new FileWriter(filePath) ,  表示以覆盖的方式写入
          BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(filePath));
          bufferedWriter.write("hello, 韩顺平教育!");
          bufferedWriter.newLine();//插入一个和系统相关的换行
          bufferedWriter.write("hello2, 韩顺平教育!"); 
          bufferedWriter.newLine();
          bufferedWriter.write("hello3, 韩顺平教育!");
          bufferedWriter.newLine();
  
          //说明：关闭外层流即可 ， 传入的 new FileWriter(filePath) ,会在底层关闭
          bufferedWriter.close();
      }
  }                                                           
  ```

  ![image-20211002202002288](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211002202002288.png)

  ```java
  package com.hspedu.writer_;
  
  import java.io.*;
  
  public class BufferedCopy_ {
      public static void main(String[] args) {
  
          //老韩说明
          //1. BufferedReader 和 BufferedWriter 是安装字符操作
          //2. 不要去操作 二进制文件[声音，视频，doc, pdf ], 可能造成文件损坏
          //BufferedInputStream
          //BufferedOutputStream
          
          String srcFilePath = "e:\\a.java"; 
          String destFilePath = "e:\\a2.java";
          //	String srcFilePath = "e:\\0245_韩顺平零基础学 Java_引出 this.avi";
          //		String destFilePath = "e:\\a2 韩顺平.avi"; 
          BufferedReader br = null;
          BufferedWriter bw = null; 
          String line;
          try {
          	br = new BufferedReader(new FileReader(srcFilePath)); 
              bw = new BufferedWriter(new FileWriter(destFilePath));
  
              //说明: readLine 读取一行内容，但是没有换行
              while ((line = br.readLine()) != null) {
                  //每读取一行，就写入
                  bw.write(line);
                  //插入一个换行
                  bw.newLine();    
          }
          System.out.println("拷贝完毕...");
          } catch (IOException e) {
              e.printStackTrace();
          } finally {
              //关闭流
              try {
                  if(br != null) {
                      br.close();
                  }
                  if(bw != null) {
                      bw.close();
                  }
              } catch (IOException e) { 
                  e.printStackTrace();
              }
          }
      }
  }    
  ```

  
  
- 转换流-OutputStreamWriter

  - 案例

    ![image-20211003200631217](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003200631217.png)

    ```java
    // 1.创建流对象
    OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream("d:\\a.txt"), "gbk");
    // 2.写入
    osw.write("hello,韩顺平教育~");
    // 3.关闭
    osw.close();
    System.out.println("保存成功~");
    ```

    

- 打印流-PrintWriter

  - ![image-20211003202607625](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003202607625.png)

  - 案例：

    ```java
    package com.hspedu.transformation;
    
    import java.io.FileWriter; 
    import java.io.IOException; 
    import java.io.PrintWriter;
    
    /**
    * @author 韩顺平
    *@version 1.0
    *演示 PrintWriter 使用方式
    */
    public class PrintWriter_ {
        public static void main(String[] args) throws IOException {
    
            //PrintWriter printWriter = new PrintWriter(System.out);
            PrintWriter printWriter = new PrintWriter(new FileWriter("e:\\f2.txt"));
            printWriter.print("hi, 北京你好~~~~");
            printWriter.close();//flush + 关闭流, 才会将数据写入到文件.. (真正的写入在这里！！！)
        }
    }
    ```

    

### 6. Properties类

- 基本介绍

  ![image-20211003212642453](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003212642453.png)

  ![image-20211003212647074](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003212647074.png)

- 案例

  ![image-20211003212925221](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211003212925221.png)

  ```java
  package com.hspedu.properties_;
  
  import java.io.FileNotFoundException; 
  import java.io.FileReader;
  import java.io.IOException;
  import java.util.Properties;
  
  public class Properties02 {
      public static void main(String[] args) throws IOException {
          //使用 Properties 类来读取 mysql.properties  文件
  
          //1. 创建 Properties 对象
          Properties properties = new Properties();
          //2. 加载指定配置文件
          properties.load(new FileReader("src\\mysql.properties"));
          //3. 把 k-v 显示控制台
          properties.list(System.out);
          //4. 根据 key  获取对应的值
          String user = properties.getProperty("user"); 
          String pwd = properties.getProperty("pwd");
          System.out.println("用户名=" + user);
          System.out.println("密码是=" + pwd);
  
      }
  }
  ```

  ```java
  package com.hspedu.properties_;
  
  import java.io.FileNotFoundException;
  import java.io.FileOutputStream;
  import java.io.IOException; 
  import java.util.Properties;
  
  public class Properties03 {
      public static void main(String[] args) throws IOException {
          //使用 Properties 类来创建 配置文件,  修改配置文件内容
  
          Properties properties = new Properties();
          //创建
          //1.如果该文件没有 key  就是创建
          //2.如果该文件有 key ,就是修改
          /*
          Properties 父类是 Hashtable ， 底层就是 Hashtable 核心方法
          public synchronized V put(K key, V value) {
          // Make sure the value is not null 
          	if (value == null) {
          		throw new NullPointerException();
          	}
  
          // Makes sure the key is not already in the hashtable. 
          	Entry<?,?> tab[] = table;
              int hash = key.hashCode();
              int index = (hash & 0x7FFFFFFF) % tab.length; 
              @SuppressWarnings("unchecked") 
              Entry<K,V> entry = (Entry<K,V>)tab[index];
              for(; entry != null ; entry = entry.next) {
              	if ((entry.hash == hash) && entry.key.equals(key)) { 
              		V old = entry.value;
              		entry.value = value;//如果 key 存在，就替换
              		return old;
              	}
          	}
          	addEntry(hash, key, value, index);//如果是新 k, 就 addEntry 
          	return null;
          }
          */
          properties.setProperty("charset", "utf8");
          properties.setProperty("user", "汤姆");//注意保存时，是中文的 unicode 码值
          properties.setProperty("pwd", "888888");
  
          //将 k-v 存储文件中即可
          properties.store(new FileOutputStream("src\\mysql2.properties"), null); //第二个参数是注释
          System.out.println("保存配置文件成功~");
      }
  }
  ```

## 第十八章 网络编程

### 1. 网络基础

- 网络的相关概念

  - 网络通信

    ![image-20211005202945640](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005202945640.png)

  - 网络

    ![image-20211005203249473](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005203249473.png)

  - ip地址

    ![image-20211005214542537](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005214542537.png)

  - ipv4 地址分类

    ![image-20211005215855640](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005215855640.png)

    ![image-20211005215921432](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005215921432.png)

  - 域名

    ![image-20211005221801973](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005221801973.png)

    说明：在网络开发中，不用使用0-1024的端口，已被占用！

  - 网络通信协议

    - 网络协议-数据的组织方式

    ![image-20211005225219976](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005225219976.png)

    - 协议(tcp/ip)

      ![image-20211005225540852](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005225540852.png)

    - 网络通信协议

      ![image-20211005230940322](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005230940322.png)

    ![image-20211005231118249](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005231118249.png)

  - TCP  和 UDP

    ![image-20211005233254513](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005233254513.png)



### 2. InetAddress

- 相关方法

  ![image-20211005234300928](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211005234300928.png)

- 应用案例

  编写代码，获取计算机的主机名和 IP 地址相关 API

  ```java
  // 获 取 本 机 InetAddress 对 象   getLocalHost 
  InetAddress localHost = InetAddress.getLocalHost(); 
  System.out.println(localHost);
  
  //根据指定主机名/域名获取 ip 地址对象 getByName 
  InetAddress host2 = InetAddress.getByName("ThinkPad-PC"); 
  System.out.println(host2);
  InetAddress host3 = InetAddress.getByName("www.hsp.com"); 
  System.out.println(host3);
  
  //获取 InetAddress 对象的主机名 getHostName 
  String host3Name = host3.getHostName(); 
  System.out.println(host3Name);
  
  //获取 InetAddress 对象的地址 getHostAddress
  String host3Address = host3.getHostAddress(); 
  System.out.println(host3Address);
  ```

  

### 3. Socket

- 基本介绍

  ![image-20211006000027831](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211006000027831.png)

  示意图：

  ![image-20211006000047765](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211006000047765.png)



### 4. TCP编程

- 基本介绍

  ![image-20211006000223437](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211006000223437.png)

  ![image-20211006000243142](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211006000243142.png)
  
  - 案例
  
    ![image-20211007173230549](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007173230549.png)
  
    ```java
    package com.hspedu.socket;
    
    import java.io.IOException; 
    import java.io.InputStream; 
    import java.net.ServerSocket; 
    import java.net.Socket;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *服务端
    */
    public class SocketTCP01Server {
        public static void main(String[] args) throws IOException {
            //思路
            //1. 在本机 的 9999 端口监听, 等待连接
            //	细节: 要求在本机没有其它服务在监听 9999
            //	细节：这个 ServerSocket 可以通过 accept()  返回多个 Socket[多个客户端连接服务器的并发] 
            ServerSocket serverSocket = new ServerSocket(9999);
            System.out.println("服务端，在 9999 端口监听，等待连接..");
            
            //2. 当没有客户端连接 9999 端口时，程序会 阻塞, 等待连接
            // 如果有客户端连接，则会返回 Socket 对象，程序继续
            Socket socket = serverSocket.accept();
            System.out.println("服务端 socket =" + socket.getClass());
            
            //3. 通过 socket.getInputStream() 读取客户端写入到数据通道的数据,  显示
            InputStream inputStream = socket.getInputStream();
            //4. IO 读取
            byte[] buf = new byte[1024]; 
            int readLen = 0;
            while ((readLen = inputStream.read(buf)) != -1) {
            	System.out.println(new String(buf, 0, readLen));//根据读取到的实际长度，显示内容.
            }
            //5.关闭流和 socket 
            inputStream.close();
            socket.close();
            serverSocket.close();//关闭
        }
    }
    
    ===========================
    import java.io.IOException; 
    import java.io.OutputStream; 
    import java.net.InetAddress; 
    import java.net.Socket;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *客户端，发送 "hello, server" 给服务端
    */
    
    public class SocketTCP01Client {
        public static void main(String[] args) throws IOException {
            //思路
            //1. 连接服务端 (ip ,  端口）
            //解读: 连接本机的 9999 端口,  如果连接成功，返回 Socket 对象
            Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
            System.out.println("客户端 socket 返回=" + socket.getClass());
            //2. 连接上后，生成 Socket,  通过 socket.getOutputStream()
            //	得到 和 socket 对象关联的输出流对象
            OutputStream outputStream = socket.getOutputStream();
            //3. 通过输出流，写入数据到 数据通道
            outputStream.write("hello, server".getBytes());
            //4. 关闭流对象和 socket, 必须关闭
            outputStream.close(); socket.close();
            System.out.println("客户端退出	");
        }
    }    
    ```
  
  - 案例2
  
    ![image-20211007212553743](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007212553743.png)
  
    思路：
  
    ![image-20211007212613086](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007212613086.png)
  
    ```java
    package com.hspedu.socket;
    
    import java.io.IOException; 
    import java.io.InputStream; 
    import java.net.ServerSocket; 
    import java.net.Socket;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *服务端
    */
    public class SocketTCP01Server {
        public static void main(String[] args) throws IOException {
            //思路
            //1. 在本机 的 9999 端口监听, 等待连接
            //	细节: 要求在本机没有其它服务在监听 9999
            //	细节：这个 ServerSocket 可以通过 accept()  返回多个 Socket[多个客户端连接服务器的并发] 
            ServerSocket serverSocket = new ServerSocket(9999);
            System.out.println("服务端，在 9999 端口监听，等待连接..");
            
            //2. 当没有客户端连接 9999 端口时，程序会 阻塞, 等待连接
            // 如果有客户端连接，则会返回 Socket 对象，程序继续
            Socket socket = serverSocket.accept();
            System.out.println("服务端 socket =" + socket.getClass());
            
            //3. 通过 socket.getInputStream() 读取客户端写入到数据通道的数据,  显示
            InputStream inputStream = socket.getInputStream();
            //4. IO 读取
            byte[] buf = new byte[1024]; 
            int readLen = 0;
            while ((readLen = inputStream.read(buf)) != -1) {
            	System.out.println(new String(buf, 0, readLen));//根据读取到的实际长度，显示内容.
            }
            
            //5. 获取 socket 相关联的输出流
    		OutputStream outputStream = socket.getOutputStream(); 
            outputStream.write("hello, client".getBytes());
    		//	设置结束标记
    		socket.shutdownOutput();
            
            //6.关闭流和 socket 
            outputStream.close();
            inputStream.close();
            socket.close();
            serverSocket.close();//关闭
        }
    }
    
    ===========================
    import java.io.IOException; 
    import java.io.OutputStream; 
    import java.net.InetAddress; 
    import java.net.Socket;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *客户端，发送 "hello, server" 给服务端
    */
    
    public class SocketTCP01Client {
        public static void main(String[] args) throws IOException {
            //思路
            //1. 连接服务端 (ip ,  端口）
            //解读: 连接本机的 9999 端口,  如果连接成功，返回 Socket 对象
            Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
            System.out.println("客户端 socket 返回=" + socket.getClass());
            //2. 连接上后，生成 Socket,  通过 socket.getOutputStream()
            //	得到 和 socket 对象关联的输出流对象
            OutputStream outputStream = socket.getOutputStream();
            
            //3. 通过输出流，写入数据到 数据通道
            outputStream.write("hello, server".getBytes());
            //	设置结束标记
    		socket.shutdownOutput();
            
            //4. 获取和 socket 关联的输入流.  读取数据(字节)，并显示
    		InputStream inputStream = socket.getInputStream(); 
            byte[] buf = new byte[1024];
    		int readLen = 0;
    		while ((readLen = inputStream.read(buf)) != -1) { 
                System.out.println(new String(buf, 0, readLen));
    		}
            
            //5. 关闭流对象和 socket, 必须关闭
            inputStream.close();
            outputStream.close(); 
            socket.close();
            System.out.println("客户端退出	");
        }
    }
    ```
  
  - 案例3
  
    ![image-20211007213148477](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007213148477.png)
  
    ```java
    package com.yt.socket;
    
    import java.io.*;
    import java.net.ServerSocket;
    import java.net.Socket;
    
    /**
     * @author Yt
     * @version 1.0
     * 服务端, 使用字符流方式读写
     */
    public class SocketTCP02Server {
        public static void main(String[] args) throws IOException {
            ServerSocket serverSocket = new ServerSocket(9999);
            Socket socket = serverSocket.accept();
    		//IO 读取, 使用字符流, 使用 InputStreamReader  将 inputStream 转成字符流
            BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            String line = bufferedReader.readLine();
            System.out.println(line);
            //注意这里也可以用While循环来读取：
            //        while((line = bufferedReader.readLine()) != null){
    		//            System.out.println(line);
    		//        }
            //但是，如果客户端的写入是用 bufferedWriter.newLine() 来表示写入的内容结束，那么服务端执行第二次bufferedReader.readLine() 时就会因为客户端的写入没有相应的 bufferedWriter.newLine() 来表示写入的内容的结束，就会进入等待状态，不会结束，它不知道客户端的写入有没有结束，进而报错。 所以，如果要用While循环来读取客户端写入数据通道的内容，客户端的写入就要用 socket.shutdownOutput() 来表示写入的内容结束！！ (客户端要读取服务端写入的数据亦然！)
            
    
            BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
            bufferedWriter.write("hello,client");
            bufferedWriter.newLine(); // 插入一个换行符，表示回复内容的结束
            bufferedWriter.flush(); //注意需要手动的 flush
    //        socket.shutdownOutput();
    
            bufferedWriter.close();
            bufferedReader.close();
            socket.close();
            serverSocket.close();
    
    
        }
    }
    =====================================
    package com.yt.socket;
    
    import java.io.*;
    import java.net.InetAddress;
    import java.net.Socket;
    
    /**
     * @author Yt
     * @version 1.0
     * 客户端，发送 "hello, server" 给服务端， 使用字符流
     */
    public class SocketTCP02Client {
        public static void main(String[] args) throws IOException {
            Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
    
            BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
            bufferedWriter.write("hello,server");
            bufferedWriter.newLine();//插入一个换行符，表示写入的内容结束, 注意，要求对方使用 readLine()!!!!
            bufferedWriter.flush();// 如果使用的字符流，需要手动刷新，否则数据不会写入数据通道
    //        socket.shutdownOutput();
    
            BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            String line = bufferedReader.readLine();
            System.out.println(line);
    
            bufferedReader.close();
            bufferedWriter.close();
            socket.close();
    
        }
    }
    
    ```
  
    

- netstat 指令

  ![image-20211007234119223](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007234119223.png)



- TCP 网络通讯不为人知的秘密

  ![image-20211007234818274](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007234818274.png)

  ![image-20211007234848809](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007234848809.png)



### 5. UDP编程

- 基本介绍

  ![image-20211007235807898](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007235807898.png)

  ![image-20211007235850437](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211007235850437.png)

  

- 基本流程

  ![image-20211008000111635](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008000111635.png)

- 案例

  ![image-20211008002819467](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008002819467-16336241021784.png)

  ```java
  import java.io.IOException; 
  import java.net.DatagramPacket; 
  import java.net.DatagramSocket; 
  import java.net.InetAddress; 
  import java.net.SocketException;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *UDP 接收端
  */
  public class UDPReceiverA {
      public static void main(String[] args) throws IOException {
          //1. 创建一个 DatagramSocket  对象，准备在 9999 接收数据
          DatagramSocket socket = new DatagramSocket(9999);
          //2. 构建一个 DatagramPacket  对象，准备接收数据
          //	在前面讲解 UDP 协议时，老师说过一个数据包最大 64k 
          byte[] buf = new byte[1024];
          DatagramPacket packet = new DatagramPacket(buf, buf.length);
          //3. 调用 接收方法,  将通过网络传输的 DatagramPacket  对象
          //	填充到 packet 对象
          //老师提示: 当有数据包发送到 本机的 9999 端口时，就会接收到数据
          //	如果没有数据包发送到 本机的 9999 端口, 就会阻塞等待.
          System.out.println("接收端 A 等待接收数据..");
          socket.receive(packet);
          //4. 可以把 packet  进行拆包，取出数据，并显示.
          int length = packet.getLength();//实际接收到的数据字节长度
          byte[] data = packet.getData();//接收到数据
          String s = new String(data, 0, length);
          System.out.println(s);
  
  
          //===回复信息给 B 端
          //将需要发送的数据，封装到 DatagramPacket 对象
          data = "好的,  明天见".getBytes();
          //说明: 封装的 DatagramPacket 对象 data 内容字节数组 , data.length , 主机(IP) ,  端口
          packet =
          	new DatagramPacket(data, data.length, InetAddress.getByName("192.168.12.1"), 9998);
          socket.send(packet);//发送
  
          //5. 关闭资源
          socket.close();
          System.out.println("A 端退出...");
  
      }
  } 
  
  =================================
  import java.io.IOException;
  import java.net.*;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *发送端 B ====> 也可以接收数据
  */ @SuppressWarnings({"all"}) 
  public class UDPSenderB {
      public static void main(String[] args) throws IOException {
  
          //1.创建 DatagramSocket  对象，准备在 9998 端口 接收数据
          DatagramSocket socket = new DatagramSocket(9998);
  
  
          //2. 将需要发送的数据，封装到 DatagramPacket 对象
          byte[] data = "hello  明天吃火锅~".getBytes(); //
  
  
          //说明: 封装的 DatagramPacket 对象 data 内容字节数组 , data.length , 主机(IP) ,  端口
          DatagramPacket packet =
          	new DatagramPacket(data, data.length, InetAddress.getByName("192.168.12.1"), 9999);
          socket.send(packet);
  
  
          //3.=== 接收从 A 端回复的信息
          //(1)	构建一个 DatagramPacket 对象，准备接收数据
          //	在前面讲解 UDP 协议时，老师说过一个数据包最大 64k 
          byte[] buf = new byte[1024];
          packet = new DatagramPacket(buf, buf.length);
          //(2)	调用 接收方法,  将通过网络传输的 DatagramPacket 对象
          //	填充到 packet 对象
          //老师提示: 当有数据包发送到 本机的 9998 端口时，就会接收到数据
          //	如果没有数据包发送到 本机的 9998 端口, 就会阻塞等待. 
          socket.receive(packet);
  
          //(3)	可以把 packet  进行拆包，取出数据，并显示.
          int length = packet.getLength();//实际接收到的数据字节长度
          data = packet.getData();//接收到数据
          String s = new String(data, 0, length); 
          System.out.println(s);
  
          //关闭资源
          socket.close();
          System.out.println("B 端退出");
      }
  }    
  ```

  

## 第十九章 多用户即时通信系统

### 1.  QQ 聊天项目演示

| ![](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008184100286.png) | ![image-20211008184108934](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008184108934.png) | ![image-20211008184115629](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008184115629.png) |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |

### 2. 项目开发流程

![image-20211008183904464](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008183904464.png)

- 需求分析

  ![image-20211008191958495](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008191958495.png)

- 界面设计

- 功能实现-用户登录

  ![image-20211008192247101](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008192247101.png)

  ![image-20211008192258620](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211008192258620.png)

- 功能实现-拉取在线用户列表

  ![image-20211009213539653](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211009213539653.png)

- 功能实现-无异常退出

- 功能实现-私聊

  ![image-20211009213628895](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211009213628895.png)

  ![image-20211009213634982](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211009213634982.png)


- 功能实现-群聊

  ![image-20211010104900387](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010104900387.png)

- 功能说明-发文件

  ![image-20211010104937254](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010104937254.png)

  ![image-20211010104948777](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010104948777.png)

- 功能实现-服务器推送新闻

  ![image-20211010105025345](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010105025345.png)

  ![image-20211010105037252](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010105037252.png)



## 第二十章 反射

### 1. 反射机制

- Java Reflection

  ![image-20211010164432553](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010164432553.png)

- Java 反射机制原理示意图 !!!

  ![image-20211010165923331](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010165923331.png)

- Java 反射机制可以完成

  ![image-20211010173911613](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010173911613.png)

- 反射相关的主要类

  ![image-20211010173952653](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010173952653.png)

  ```java
  package com.hspedu.reflection;
  
  import java.io.FileInputStream;
  import java.io.FileNotFoundException; 
  import java.lang.reflect.Constructor; 
  import java.lang.reflect.Field;
  import java.lang.reflect.Method; 
  import java.util.Properties;
  
  public class Reflection01 {
      public static void main(String[] args) throws Exception {
  
          //1. 使用 Properties 类,  可以读写配置文件
          Properties properties = new Properties(); 
          properties.load(new FileInputStream("src\\re.properties"));
          String classfullpath = properties.get("classfullpath").toString();//"com.hspedu.Cat" 
          String methodName = properties.get("method").toString();//"hi"
  
  
          //2. 使用反射机制解决
          //(1) 加载类, 返回 Class 类型的对象 cls 
          Class cls = Class.forName(classfullpath);
          //(2) 通过 cls  得到你加载的类 com.hspedu.Cat  的对象实例
          Object o = cls.newInstance();
          System.out.println("o 的运行类型=" + o.getClass()); //运行类型
          //(3) 通过 cls 得到你加载的类 com.hspedu.Cat 的 methodName"hi"	的方法对象
          //	即：在反射中，可以把方法视为对象（万物皆对象）
          Method method1 = cls.getMethod(methodName);
          //(4) 通过 method1  调用方法: 即通过方法对象来实现调用方法
          System.out.println("=============================");
          method1.invoke(o); //传统方法 对象.方法() ,  反射机制 方法对象.invoke(对象)
  
  
          //java.lang.reflect.Field: 代表类的成员变量, Field 对象表示某个类的成员变量
          //得到 name 字段
          //getField 不能得到私有的属性
          Field nameField = cls.getField("age"); //
          System.out.println(nameField.get(o)); // 传统写法 对象.成员变量 , 反射 :	成员变量对象.get(对象)
  
  
          //java.lang.reflect.Constructor: 代表类的构造方法, Constructor 对象表示构造器
          Constructor constructor = cls.getConstructor(); //()中可以指定构造器参数类型, 返回无参构造器
          System.out.println(constructor);//Cat()
  
          Constructor constructor2 = cls.getConstructor(String.class); // 这里老师传入的 String.class 就是 String 类的 Class 对象
          System.out.println(constructor2);//Cat(String name)
      }
  }    
  ```

  

- 反射优点和缺点

  ![image-20211010190038527](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010190038527.png)

  ```java
  package com.hspedu.reflection;
  
  
  import com.hspedu.Cat;
  import java.io.FileInputStream;
  import java.lang.reflect.Constructor;
  import java.lang.reflect.Field;
  import java.lang.reflect.InvocationTargetException; 
  import java.lang.reflect.Method;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *测试反射调用的性能，和优化方案
  */
  public class Reflection02 {
      public	static	void	main(String[]	args)	throws	ClassNotFoundException,	NoSuchMethodException, InvocationTargetException, InstantiationException, IllegalAccessException {
  
          //Field
          //Method
          //Constructor
          m1();//传统
          m2();//反射
          m3();//反射优化
      }
  
  
      //传统方法来调用 hi 
      public static void m1() {
  
          Cat cat = new Cat();
          long start = System.currentTimeMillis();
          for (int i = 0; i < 90; i++) {
          	cat.hi();
          }
          long end = System.currentTimeMillis();
          System.out.println("m1() 耗时=" + (end - start));
      }
  
  
      //反射机制调用方法 hi
      public	static	void	m2()	throws	ClassNotFoundException,	IllegalAccessException,	InstantiationException, NoSuchMethodException, InvocationTargetException {
  
          Class cls = Class.forName("com.hspedu.Cat");
          Object o = cls.newInstance();
          Method hi = cls.getMethod("hi");
          long start = System.currentTimeMillis(); 
          for (int i = 0; i < 900000000; i++) {
              hi.invoke(o);//反射调用方法
          }
          long end = System.currentTimeMillis();
          System.out.println("m2() 耗时=" + (end - start));
      }
  
  
      //反射调用优化 + 关闭访问检查
  
      public	static	void	m3()	throws	ClassNotFoundException,	IllegalAccessException,	InstantiationException, NoSuchMethodException, InvocationTargetException {
  
          Class cls = Class.forName("com.hspedu.Cat");
          Object o = cls.newInstance();
          Method hi = cls.getMethod("hi");
          hi.setAccessible(true);//在反射调用方法时，取消访问检查
          long start = System.currentTimeMillis();
          for (int i = 0; i < 900000000; i++) {
              hi.invoke(o);//反射调用方法
          }
          long end = System.currentTimeMillis();
          System.out.println("m3() 耗时=" + (end - start));
      }
  }
  ```

- 反射调用优化-关闭访问检查

  ![image-20211010190441743](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010190441743.png)



### 2. Class类

- 基本介绍

  ![image-20211010194842858](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010194842858.png)

  ![image-20211010194847698](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010194847698.png)

  ```java
  package com.hspedu.reflection.class_;
  
  import com.hspedu.Cat;
  import java.util.ArrayList;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *对 Class 类特点的梳理
  */
  public class Class01 {
      public static void main(String[] args) throws ClassNotFoundException {
          //看看 Class 类图
          //1. Class 也是类，因此也继承 Object 类
          //Class
          //2. Class 类对象不是 new 出来的，而是系统创建的
          //(1) 传统 new 对象
          /*	ClassLoader 类
          public Class<?> loadClass(String name) throws ClassNotFoundException { 
          	return loadClass(name, false);
          }
          */
          //Cat cat = new Cat();
          //(2) 反射方式, 刚才老师没有 debug 到 ClassLoader 类的 loadClass, 原因是，我没有注销 Cat cat = new Cat();
          /*
          ClassLoader 类,  仍然是通过 ClassLoader 类加载 Cat 类的 Class 对象
          public Class<?> loadClass(String name) throws ClassNotFoundException {
          	return loadClass(name, false);
          }
          */
          Class cls1 = Class.forName("com.hspedu.Cat");
  
  
          //3. 对于某个类的 Class 类对象，在内存中只有一份，因为类只加载一次
          Class cls2 = Class.forName("com.hspedu.Cat"); 
          System.out.println(cls1.hashCode());
          System.out.println(cls2.hashCode());
          Class cls3 = Class.forName("com.hspedu.Dog"); 
          System.out.println(cls3.hashCode());
      }
  }    
  ```

  

- Class类常用方法

  ![image-20211010204649388](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010204649388.png)

  ```java
  package com.hspedu.reflection.class_;
  
  import com.hspedu.Car;
  import java.lang.reflect.Field;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 Class 类的常用方法
  */
  
  public class Class02 {
      public	static	void	main(String[]	args)	throws	ClassNotFoundException,	IllegalAccessException, InstantiationException, NoSuchFieldException {
  
          String classAllPath = "com.hspedu.Car";
          //1 .  获取到 Car 类 对应的 Class 对象
          //<?> 表示不确定的 Java 类型
          Class<?> cls = Class.forName(classAllPath);
          //2. 输出 cls
          System.out.println(cls); //显示 cls 对象, 是哪个类的 Class 对象 com.hspedu.Car
          System.out.println(cls.getClass());//输出 cls 运行类型 java.lang.Class    (因为cls是Car类的Class类对象)
          //3. 得到包名
          System.out.println(cls.getPackage().getName());//包名
          //4. 得到全类名
          System.out.println(cls.getName());
          //5. 通过 cls 创建对象实例
          Car car = (Car) cls.newInstance(); 
          System.out.println(car);//car.toString()
          //6. 通过反射获取属性 brand
          Field brand = cls.getField("brand");
          System.out.println(brand.get(car));//宝马
          //7. 通过反射给属性赋值
          brand.set(car, "奔驰");
          System.out.println(brand.get(car));//奔驰
          //8 我希望大家可以得到所有的属性(字段)
          System.out.println("=======所有的字段属性===="); 
          Field[] fields = cls.getFields();
          for (Field f : fields) {
          	System.out.println(f.getName());//名称
          }  
      }
  }
  ```

  

- 获取 Class 类对象（6种方式）

  ![image-20211010212426286](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010212426286.png)

  ![image-20211010212446791](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010212446791.png)

  ![image-20211010212453965](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010212453965.png)

  ```java
  import com.hspedu.Car;
  /**
  *@author 韩顺平
  *@version 1.0
  *演示得到 Class 对象的各种方式(6)
  */
  public class GetClass_ {
      public static void main(String[] args) throws ClassNotFoundException {
  
          //1. Class.forName
          String classAllPath = "com.hspedu.Car"; //通过读取配置文件获取
          Class<?> cls1 = Class.forName(classAllPath); 
          System.out.println(cls1);
  
          //2. 类名.class , 应用场景:  用于 参数传递
          Class cls2 = Car.class; 
          System.out.println(cls2);
  
          //3. 对象.getClass(), 应用场景，有对象实例
          Car car = new Car();
          Class cls3 = car.getClass(); 
          System.out.println(cls3);
  
          //4. 通过类加载器【4 种】来获取到类的 Class 对象
          //(1)先得到类加载器 car
          ClassLoader classLoader = car.getClass().getClassLoader();
          //(2)通过类加载器得到 Class 对象
          Class cls4 = classLoader.loadClass(classAllPath); 
          System.out.println(cls4);
  
          //cls1 , cls2 , cls3 , cls4 其实是同一个对象
          System.out.println(cls1.hashCode());
          System.out.println(cls2.hashCode()); 
          System.out.println(cls3.hashCode()); 
          System.out.println(cls4.hashCode());
  
          //5. 基本数据(int, char,boolean,float,double,byte,long,short) 按如下方式得到 Class 类对象
          Class<Integer> integerClass = int.class; 
          Class<Character> characterClass = char.class;
          Class<Boolean> booleanClass = boolean.class;
          System.out.println(integerClass);//int
  
          //6. 基本数据类型对应的包装类，可以通过 .TYPE 得到 Class 类对象
          Class<Integer> type1 = Integer.TYPE;
          Class<Character> type2 = Character.TYPE; //其它包装类 BOOLEAN, DOUBLE, LONG,BYTE 等待
          System.out.println(type1);
  
          System.out.println(integerClass.hashCode());//? 
          System.out.println(type1.hashCode());//?  相同！
  
      }
  }
  ```

  

- 哪些类型有 Class 对象

  ![image-20211010213942178](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010213942178.png)

  ```java
  package com.hspedu.reflection.class_;
  import java.io.Serializable;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示哪些类型有 Class 对象
  */
  public class AllTypeClass {
      public static void main(String[] args) {
      Class<String> cls1 = String.class;//外部类
          Class<Serializable> cls2 = Serializable.class;//接口
          Class<Integer[]> cls3 = Integer[].class;//数组
          Class<float[][]> cls4 = float[][].class;//二维数组
          Class<Deprecated> cls5 = Deprecated.class;//注解
      	Class<Thread.State> cls6 = Thread.State.class; //枚举
          Class<Long> cls7 = long.class;//基本数据类型
          Class<Void> cls8 = void.class;//void 数据类型
          Class<Class> cls9 = Class.class;//
  
      	System.out.println(cls1);
          System.out.println(cls2); 
          System.out.println(cls3); 
          System.out.println(cls4); 
          System.out.println(cls5);
          System.out.println(cls6); 
          System.out.println(cls7); 
          System.out.println(cls8); 
          System.out.println(cls9);
      }
  }    
  ```

  

### 3. 类加载 （面试）

- 基本说明 (静态加载和动态加载)

  ![image-20211010222849351](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010222849351.png)

- 类加载时机

  ![image-20211010222908770](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010222908770.png)



- 类加载过程图

  ![image-20211010224235507](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010224235507.png)

- 类加载各阶段完成任务

  ![image-20211010224303509](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010224303509.png)

  - 加载阶段

    ![image-20211010225728810](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010225728810.png)

  - 连接阶段

    - 验证 

    ![image-20211010225818907](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010225818907.png)

    - 准备

    ![image-20211010225857988](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010225857988.png)

    ```java
    package com.hspedu.reflection.classload_;
    
    /**
    *@author 韩顺平
    *@version 1.0
    *我们说明一个类加载的链接阶段-准备
    */
    public class ClassLoad02 {
        public static void main(String[] args) {
        }
    }
    class A {
        //属性-成员变量-字段
        //老韩分析类加载的链接阶段-准备 属性是如何处理
        //1. n1 是实例属性, 不是静态变量，因此在准备阶段，是不会分配内存
        //2. n2 是静态变量，分配内存 n2 是默认初始化 0 ,而不是 20
        //3. n3  是 static final 是常量,  他和静态变量不一样, 因为一旦赋值就不变 n3 = 30 
        public int n1 = 10;
        public static int n2 = 20; 
        public static final	int n3 = 30;
    }    
        
    ```

    - 解析

    ![image-20211010230310403](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010230310403.png)

  - Initialization（初始化)

    ![image-20211010231740897](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211010231740897.png)

    ```java
    //演示类加载-初始化阶段
    public class ClassLoad03 {
        public static void main(String[] args) throws ClassNotFoundException {
            //老韩分析
            //1. 加载 B 类，并生成 B 的 class 对象
            //2. 链接 num = 0
            //3. 初始化阶段
            //	依次自动收集类中的所有静态变量的赋值动作和静态代码块中的语句,并合并
            /*
            clinit() {
            	System.out.println("B 静态代码块被执行");
            	//num = 300;
            	num = 100;
            }
            合并: num = 100
    
            */
    
            //new B();//类加载
            System.out.println(B.num);//100, 如果直接使用类的静态属性，也会导致类的加载
    
    
            //看看加载类的时候，是有同步机制控制
            /*
            protected Class<?> loadClass(String name, boolean resolve)
            	throws ClassNotFoundException
            {
            	//正因为有这个机制，才能保证某个类在内存中, 只有一份 Class 对象
            	synchronized (getClassLoadingLock(name)) {
            	//....
            	}
            }
            */
            B b = new B();
        }
    }
    
    
    class B {
        static {
        	System.out.println("B 静态代码块被执行"); 
            num = 300;
        }
    
        static int num = 100;
    
        public B() {//构造器
        	System.out.println("B() 构造器被执行");
        }
    }
    ```

    

### 4. 通过反射获取类的结构信息

- 第一组: java.lang.Class 类 (类的Class类(对象)下的方法)

  ![image-20211011012626871](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011012626871.png)

- 第二组: java.lang.reflect.Field 类 （字段类(对象)的方法）

  ![image-20211011014220890](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011014220890.png)

- 第三组: java.lang.reflect.Method 类 （方法类(对象)的方法）

  ![image-20211011014250352](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011014250352.png)

- 第四组: java.lang.reflect.Constructor 类 （构造器类(对象)的方法）

  ![image-20211011014301127](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011014301127.png)

  ```java
  import org.junit.jupiter.api.Test;
  
  import java.lang.annotation.Annotation;
  import java.lang.reflect.Constructor;
  import java.lang.reflect.Field;
  import java.lang.reflect.Method;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示如何通过反射获取类的结构信息
  */
  public class ReflectionUtils {
      public static void main(String[] args) {
  
      }
  
      @Test
      public void api_02() throws ClassNotFoundException, NoSuchMethodException {
          //得到 Class 对象
          Class<?> personCls = Class.forName("com.hspedu.reflection.Person");
          //getDeclaredFields:获取本类中所有属性
          //规定 说明:  默认修饰符 是 0  ， public	是 1 ，private 是 2 ，protected 是 4 , static 是 8 ，final 是 16 
          Field[] declaredFields = personCls.getDeclaredFields();
          for (Field declaredField : declaredFields) {
          	System.out.println("本类中所有属性=" + declaredField.getName()
          		+ "  该属性的修饰符值=" + declaredField.getModifiers()
          		+ "  该属性的类型=" + declaredField.getType());
          }
  
          //getDeclaredMethods:获取本类中所有方法
          Method[] declaredMethods = personCls.getDeclaredMethods(); 
          for (Method declaredMethod : declaredMethods) {
          	System.out.println("本类中所有方法=" + declaredMethod.getName()
          		+ "  该方法的访问修饰符值=" + declaredMethod.getModifiers()
          		+ " 该方法返回类型" + declaredMethod.getReturnType());
  
              //输出当前这个方法的形参数组情况
              Class<?>[] parameterTypes = declaredMethod.getParameterTypes(); 
              for (Class<?> parameterType : parameterTypes) {
              	System.out.println("该方法的形参类型=" + parameterType);
              }
          }
  
  
          //getDeclaredConstructors:获取本类中所有构造器
          Constructor<?>[] declaredConstructors = personCls.getDeclaredConstructors(); 
          for (Constructor<?> declaredConstructor : declaredConstructors) {
          	System.out.println("====================");
          	System.out.println("本类中所有构造器=" + declaredConstructor.getName());//这里老师只是输出名
  
              Class<?>[] parameterTypes = declaredConstructor.getParameterTypes(); 
              for (Class<?> parameterType : parameterTypes) {
              	System.out.println("该构造器的形参类型=" + parameterType);
              }
          }
      }
  
      //第一组方法 API 
      @Test
      public void api_01() throws ClassNotFoundException, NoSuchMethodException {
  
          //得到 Class 对象
          Class<?> personCls = Class.forName("com.hspedu.reflection.Person");
          //getName:获取全类名
          System.out.println(personCls.getName());//com.hspedu.reflection.Person
          //getSimpleName:获取简单类名
          System.out.println(personCls.getSimpleName());//Person
          //getFields:获取所有 public 修饰的属性，包含本类以及父类的
          Field[] fields = personCls.getFields(); 
          for (Field field : fields) {//增强 for
          	System.out.println("本类以及父类的属性=" + field.getName());
          }
          //getDeclaredFields:获取本类中所有属性
          Field[] declaredFields = personCls.getDeclaredFields(); 
          for (Field declaredField : declaredFields) {
          	System.out.println("本类中所有属性=" + declaredField.getName());
          }
          //getMethods:获取所有 public 修饰的方法，包含本类以及父类的
          Method[] methods = personCls.getMethods();
          for (Method method : methods) {
          	System.out.println("本类以及父类的方法=" + method.getName());
          }
          //getDeclaredMethods:获取本类中所有方法
          Method[] declaredMethods = personCls.getDeclaredMethods();
          for (Method declaredMethod : declaredMethods) {
          	System.out.println("本类中所有方法=" + declaredMethod.getName());
          }
          //getConstructors: 获取所有 public 修饰的构造器，包含本类
          Constructor<?>[] constructors = personCls.getConstructors(); 
          for (Constructor<?> constructor : constructors) {
          	System.out.println("本类的构造器=" + constructor.getName());
          }
          //getDeclaredConstructors:获取本类中所有构造器
          Constructor<?>[] declaredConstructors = personCls.getDeclaredConstructors();
          for (Constructor<?> declaredConstructor : declaredConstructors) {
          	System.out.println("本类中所有构造器=" + declaredConstructor.getName());//这里老师只是输出名
          }
          //getPackage:以 Package 形式返回 包信息
          System.out.println(personCls.getPackage());//com.hspedu.reflection
          //getSuperClass:以 Class 形式返回父类信息 
          Class<?> superclass = personCls.getSuperclass();
          System.out.println("父类的 class 对象=" + superclass);//
          //getInterfaces:以 Class[]形式返回接口信息
          Class<?>[] interfaces = personCls.getInterfaces(); 
          for (Class<?> anInterface : interfaces) {
          	System.out.println("接口信息=" + anInterface);
          }
          //getAnnotations:以 Annotation[] 形式返回注解信息
          Annotation[] annotations = personCls.getAnnotations(); 
          for (Annotation annotation : annotations) {
          	System.out.println("注解信息=" + annotation);//注解
          }
      }
  }
  
  
  class A {
      public String hobby;
  
  
      public void hi() {
  
  
      }
  
  
      public A() {
      }    
  
  
      public A(String name) {
      }
  }
  
  
  interface IA {
  }
  
  
  interface IB {
  }
  
  
  @Deprecated
  class Person extends A implements IA, IB {
      //属性
      public String name;
      protected static int age; // 4 + 8 = 12 String job;
      private double sal;
  
  
      //构造器
      public Person() {
      }
  
  
      public Person(String name) {
      }
  
  
      //私有的
      private Person(String name, int age) {
  
  
      }
  
  
      //方法
      public void m1(String name, int age, double sal) {
  
  
      }
  
  
      protected String m2() { return null;
      }
  
  
      void m3() {
  
  
      }
  
  
      private void m4() {
  
  
      }
  }
  ```

  

### 5. 通过反射创建对象 (私有就需要暴破)

![image-20211011110144092](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011110144092.png)

案例：

测试 1：通过反射创建某类的对象，要求该类中必须有 public 的无参构造

测试 2：通过调用某个特定构造器的方式，实现创建某类的对象

```java
package com.hspedu.reflection;

import java.lang.reflect.Constructor;
import java.lang.reflect.InvocationTargetException;

/**
*@author 韩顺平
*@version 1.0
*演示通过反射机制创建实例
*/
public class ReflecCreateInstance {
    public	static	void	main(String[]	args)	throws	ClassNotFoundException,	IllegalAccessException, InstantiationException, NoSuchMethodException, InvocationTargetException {


    //1. 先获取到 User 类的 Class 对象
    Class<?> userClass = Class.forName("com.hspedu.reflection.User");
    //2. 通过 public 的无参构造器创建实例
    Object o = userClass.newInstance(); 
    System.out.println(o);
        
    //3. 通过 public 的有参构造器创建实例
        /*
        constructor 对象就是
        public User(String name) {//public 的有参构造器
        	this.name = name;
        }
        */
    //3.1 先得到对应构造器
    Constructor<?> constructor = userClass.getConstructor(String.class);
    //3.2 创建实例，并传入实参
    Object hsp = constructor.newInstance("hsp"); 
    System.out.println("hsp=" + hsp);
        
    //4. 通过非 public 的有参构造器创建实例
    //4.1 得到 private 的构造器对象
    Constructor<?> constructor1 = userClass.getDeclaredConstructor(int.class, String.class);
    //4.2 创建实例
    //暴破【暴力破解】 ,  使用反射可以访问 private 构造器/方法/属性,  反射面前，都是纸老虎
    constructor1.setAccessible(true); //要用非 public 的有参构造器创建实例的话，就要暴力破解！！！
    Object user2 = constructor1.newInstance(100, "张三丰"); 
        System.out.println("user2=" + user2);
    }
}


class User { //User 类
    private int age = 10;
    private String name = "韩顺平教育";

    public User() {//无参 public
    }

    public User(String name) {//public 的有参构造器
    	this.name = name;
    }

    private User(int age, String name) {//private 有参构造器
    	this.age = age; 
        this.name = name;
    }

    public String toString() {
    	return "User [age=" + age + ", name=" + name + "]";
    }
}    
```



### 6. 通过反射访问类中的成员 (私有就需要暴破)

- 访问属性

  ![image-20211011111933640](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011111933640-16339223758281.png)

  ```java
  package com.hspedu.reflection;
  
  import java.lang.reflect.Field;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示反射操作属性
  */
  public class ReflecAccessProperty {
      public	static	void	main(String[]	args)	throws	ClassNotFoundException,	IllegalAccessException, InstantiationException, NoSuchFieldException {
  
          //1. 得到 Student 类对应的 Class 对象
          Class<?> stuClass = Class.forName("com.hspedu.reflection.Student");
          //2. 创建对象
          Object o = stuClass.newInstance();//o 的运行类型就是 Student 
          System.out.println(o.getClass());//Student
          //3. 使用反射得到 age 属性对象
          Field age = stuClass.getField("age"); 
          age.set(o, 88);//通过反射来操作属性
          System.out.println(o);//
          System.out.println(age.get(o));//返回 age 属性的值
  
          //4. 使用反射操作 name 属性
          Field name = stuClass.getDeclaredField("name");
          //对 name 进行暴破,  可以操作 private 属性
          name.setAccessible(true);  //取消访问检查
          //name.set(o, "老韩");
          name.set(null, "老韩~");//因为 name 是 static 属性，因此 o 也可以写出 null 
          System.out.println(o);
          System.out.println(name.get(o)); //获取属性值
          System.out.println(name.get(null));//获取属性值, 要求 name 是 static
      }
  }
  
  class Student {//类
      public int age;
      private static String name;
  
      public Student() {//构造器
      }   
      public String toString() {
      	return "Student [age=" + age + ", name=" + name + "]";
      }
  }
  ```

  

- 访问方法

  ![image-20211011112545362](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011112545362.png)

  ```java
  package com.hspedu.reflection;
  
  import java.lang.reflect.InvocationTargetException; 
  import java.lang.reflect.Method;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示通过反射调用方法
  */
  public class ReflecAccessMethod {
      public	static	void	main(String[]	args)	throws	ClassNotFoundException,	NoSuchMethodException, IllegalAccessException, InstantiationException, InvocationTargetException {
  
          //1. 得到 Boss 类对应的 Class 对象
          Class<?> bossCls = Class.forName("com.hspedu.reflection.Boss");
          //2. 创建对象
          Object o = bossCls.newInstance();
          //3. 调用 public 的 hi 方法
          //Method hi = bossCls.getMethod("hi", String.class);//OK
          //3.1 得到 hi 方法对象
          Method hi = bossCls.getDeclaredMethod("hi", String.class);//OK
          //3.2 调用
          hi.invoke(o, "韩顺平教育~");
  
  
          //4. 调用 private static 方法
          //4.1 得到 say 方法对象
          Method say = bossCls.getDeclaredMethod("say", int.class, String.class, char.class);
          //4.2 因为 say 方法是 private,  所以需要暴破，原理和前面讲的构造器和属性一样
          say.setAccessible(true); //在反射调用方法时，取消访问检查
          System.out.println(say.invoke(o, 100, "张三", '男'));
          //4.3 因为 say 方法是 static 的，还可以这样调用 ，可以传入 null
          System.out.println(say.invoke(null, 200, "李四", '女'));
  
  
          //5. 在反射中，如果方法有返回值，统一返回 Object ,  但是他运行类型和方法定义的返回类型一致
          Object reVal = say.invoke(null, 300, "王五", '男');
          System.out.println("reVal 的运行类型=" + reVal.getClass());//String  
          
          //在演示一个返回的案例
          Method m1 = bossCls.getDeclaredMethod("m1"); 
          Object reVal2 = m1.invoke(o);
          System.out.println("reVal2 的运行类型=" + reVal2.getClass());//Monster
      }
  }
  
  
  class Monster {}
  class Boss {//类
      public int age;
      private static String name;
  
      public Boss() {//构造器
      }
  
      public Monster m1() { 
          return new Monster();
      }
  
      private static String say(int n, String s, char c) {//静态方法
          return n + " " + s + " " + c;
      }
  
      public void hi(String s) {//普通 public 方法 
          System.out.println("hi " + s);
      }
  }
  ```

  

## 第二十一章 MySQL基础

### 1. 数据库

- 使用命令行窗口连接MYSQL 数据库[示意图]

  ![image-20211011165054617](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011165054617.png)

- 操作示意图

  ![image-20211011165139639](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011165139639.png)



- 数据库三层结构

  ![image-20211011212956221](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011212956221.png)

  ![image-20211011213029824](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011213029824.png)

- 数据在数据库中的存储方式

  ![image-20211011214411283](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011214411283.png)

- SQL 语句分类

  ![image-20211011214431448](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011214431448.png)



- 创建数据库    (校对规则细节！！！)

  - IF NOT EXISTS 如果不写的话，创建数据库时已经有存在的该数据库就会报错。写了的话 数据库存在就不创建！
  - 表也可以指定校对规则，如果不指定就用它所属数据库的校对规则！！！

  ![image-20211011215721579](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011215721579.png)

  ```mysql
  # 演示数据库的操作
  #创建一个名称为 hsp_db01 的数据库。[图形化和指令 演示]
  
  #使用指令创建数据库 
  CREATE DATABASE hsp_db01;
  #删除数据库指令
  DROP DATABASE hsp_db01
  #创建一个使用 utf8 字符集的 hsp_db02 数据库
  CREATE DATABASE hsp_db02 CHARACTER SET utf8
  #创建一个使用 utf8 字符集，并带校对规则的 hsp_db03 数据库
  CREATE DATABASE hsp_db03 CHARACTER SET utf8 COLLATE utf8_bin
  #校对规则 utf8_bin  区分大小     默认 utf8_general_ci  不区分大小写
  
  #下面是一条查询的 sql , select 查询 *  表示所有字段 FROM  从哪个表
  #WHERE 从哪个字段 NAME = 'tom' 查询名字是 tom 
  SELECT *
  	FROM t1
  	WHERE NAME = 'tom'
  ```

  

- 查看、删除数据库

  ![image-20211011220839365](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011220839365.png)

  ```mysql
  #演示删除和查询数据库
  #查看当前数据库服务器中的所有数据库
  SHOW DATABASES
  #查看前面创建的 hsp_db01 数据库的定义信息
  SHOW CREATE DATABASE `hsp_db01`
  #老师说明 在创建数据库,表的时候，为了规避关键字，可以使用反引号解决
  #删除前面创建的 hsp_db01 数据库
  DROP DATABASE hsp_db01
  ```

- 备份恢复数据库

  ![image-20211011221936755](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011221936755.png)

  ```mysql
  #练习 : database03.sql  备份 hsp_db02 和 hsp_db03  库中的数据，并恢复
  
  #备份, 要在 Dos 下执行 mysqldump 指令 指令在 mysql 安装目录\bin
  #这个备份的文件，就是对应的 sql 语句
  mysqldump -u root -p -B hsp_db02 hsp_db03 > d:\\bak.sql
  
  DROP DATABASE hsp_db02;
  
  #恢复数据库(注意：进入 Mysql 命令行再执行) 
  source d:\\bak.sql
  
  #第二个恢复方法， 直接将 bak.sql 的内容放到查询编辑器中，执行
  ```

  

- 备份恢复数据库的表

  ![image-20211011221904520](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011221904520.png)



- 练习

  ![image-20211011222821908](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011222821908.png)

  ```mysql
  #这是一个 ecshop  的数据库，包括 ecshop 所有的表，请导入到 mysql 数据库中[备份]
  #进入到 mysql 命令行: source ecshop 备份文件路径
  #再将 ecshop 整个数据库备份到你的 d:\\ecshop.sql 到 dos 下 :
  mysqldump -u root -p -B ecshop > d:\\ecshop.sql
  #将 mysql 的 ecshop 数据库删除,  并通过备份的 d:\\ecshop.sql 恢复
  #进入 mysql 命令行
  source d:\\ecshop.sql
  ```

  

### 2. 表

- 创建表

  ![image-20211011224921800](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011224921800.png)

  ```mysql
  #指令创建表
  #注意：hsp_db02 创建表时，要根据需保存的数据创建相应的列，并根据数据的类型定义相应的列类型。例：user表 (快速入门案例 create_tab01.sql )
  #id	整形	[图形化，指令]
  #name	字符串
  #password  字符串
  #birthday	日期
  CREATE TABLE `user` ( id INT,
  	`name` VARCHAR(255),
  	`password` VARCHAR(255),
  	`birthday` DATE)
  	CHARACTER SET utf8 COLLATE utf8_bin ENGINE INNODB;
  ```

- 修改表-基本介绍 （重要）

  ![image-20211012155852997](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012155852997.png)

  练习：

  ```mysql
  #修改表的操作练习
  --	员工表 emp 的上增加一个 image 列，varchar 类型(要求在 resume 后面)。
  ALTER TABLE emp
  	ADD image VARCHAR(32) NOT NULL DEFAULT '' AFTER RESUME
  	
  DESC employee -- 显示表结构，可以查看表的所有列
  
  --	修改 job 列，使其长度为 60。
  ALTER TABLE emp
  	MODIFY job VARCHAR(60) NOT NULL DEFAULT ''
  	
  --	删除 sex 列。
  ALTER TABLE emp
  	DROP sex
  	
  --	表名改为 employee。
  RENAME TABLE emp TO employee
  
  --	修改表的字符集为 utf8
  ALTER TABLE employee CHARACTER SET utf8
  
  --	列名 name 修改为 user_name 
  ALTER TABLE employee
  	CHANGE `name` `user_name` VARCHAR(64) NOT NULL DEFAULT ''
  	
  DESC employee
  ```

  

  

### 3. Mysql数据类型 (细节！)

- Mysql 常用数据类型(列类型)

  ![image-20211011225251022](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211011225251022.png)

- 数值型(整数)的基本使用

  ![image-20211012132556268](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012132556268.png)

  ![image-20211012133058121](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012133058121.png)

  ```mysql
  #演示整型的是一个
  #老韩使用 tinyint 来演示范围 有符号 -128 ~ 127	如果没有符号 0-255
  #说明： 表的字符集，校验规则, 存储引擎，老师使用默认
  #1. 如果没有指定 unsinged ,  则 TINYINT 就是有符号
  #2. 如果指定 unsinged , 则 TINYINT 就是无符号 0-255 
  CREATE TABLE t3 (
  	id TINYINT); 
  
  CREATE TABLE t4 (
  	id TINYINT UNSIGNED);
  
  INSERT INTO t3 VALUES(127); #这是非常简单的添加语句
  SELECT * FROM t3
  
  INSERT INTO t4 VALUES(255);
  SELECT * FROM t4;
  ```

- 数值型(bit)的使用

  ![image-20211012133433891](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012133433891.png)

  ```mysql
  #演示 bit 类型使用
  #说明
  #1. bit(m) m是bit位数 在 1-64
  #2. 添加数据 范围 按照你给的位数来确定，比如 m = 8  表示一个字节 0~255
  #3. 显示按照 bit （二进制数据显示）
  #4. 查询时，仍然可以按照数来查询
  CREATE TABLE t05 (num BIT(8)); 
  INSERT INTO t05 VALUES(255); 
  SELECT * FROM t05;
  SELECT * FROM t05 WHERE num = 1;
  ```

- 数值型(小数)的基本使用

  ![image-20211012140456933](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012140456933.png)

  ```mysql
  #演示 decimal 类型、float、double 使用
  
  #创建表
  CREATE TABLE t06 ( num1 FLOAT, num2 DOUBLE,
  num3 DECIMAL(30,20));
  #添加数据
  INSERT INTO t06 VALUES(88.12345678912345, 88.12345678912345,88.12345678912345); 
  SELECT * FROM t06;
  
  #decimal 可以存放很大的数    M指定长度！！！！！
  CREATE TABLE t07 ( num DECIMAL(65)); 
  INSERT INTO t07 VALUES(8999999933338388388383838838383009338388383838383838383);
  SELECT * FROM t07; 
  
  CREATE TABLE t08(
  	num BIGINT UNSIGNED)
  INSERT INTO t08 VALUES(8999999933338388388383838838383009338388383838383838383); 
  SELECT * FROM t08; #加不进去
  ```

- 字符串的基本使用    (注意字符和字节！！！！)

  ![image-20211012142934336](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012142934336.png)

  ```mysql
  #演示字符串类型使用 char varchar
  #注释的快捷键 shift+ctrl+c ,  注销注释 shift+ctrl+r
  -- CHAR(size)
  -- 固定长度字符串 最大size 255  字符
  -- VARCHAR(size)	0~65535 字节
  -- 可变长度字符串 最大 65532 字节 那么最大size字符数根据编码确定！！！	【utf8 编码最大 21844 字符 1-3 个字节用于记录大小】
  -- 如果表的编码是 utf8 varchar(size) size = (65535-3) / 3 = 21844
  -- 如果表的编码是 gbk varchar(size) size = (65535-3) / 2 = 32766 
  CREATE TABLE t09 (
  	`name` CHAR(255));
  CREATE TABLE t10 (
  	`name` VARCHAR(32766)) CHARSET gbk;
  
  DROP TABLE t10;
  ```

- 字符串使用细节 （重要！！）

  ![image-20211012152538990](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012152538990.png)

  ![image-20211012152617012](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012152617012.png)

  ![image-20211012152633705](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012152633705.png)

  ![image-20211012152658700](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012152658700.png)

  ```mysql
  #演示字符串类型的使用细节
  #char(4) 和 varchar(4) 这个 4 表示的是字符，而不是字节,  不区分字符是汉字还是字母
  CREATE TABLE t11(
  	`name` CHAR(4));
  INSERT INTO t11 VALUES('韩顺平好');
  SELECT * FROM t11;
  
  CREATE TABLE t12(
  	`name` VARCHAR(4));
  INSERT INTO t12 VALUES('韩顺平好'); 
  INSERT INTO t12 VALUES('ab 北京'); 
  SELECT * FROM t12;
  
  #如果 varchar 不够用，可以考虑使用 mediumtext  或者 longtext,
  #如果想简单点，可以使用直接使用 text
  CREATE TABLE t13( content TEXT, content2 MEDIUMTEXT , content3 LONGTEXT); 
  INSERT INTO t13 VALUES('韩顺平教育', '韩顺平教育 100', '韩顺平教育 1000~~');
  SELECT * FROM t13;
  ```

- 日期类型的基本使用

  ![image-20211012153821388](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012153821388.png)

  ```mysql
  #演示时间相关的类型
  #创建一张表, date , datetime , timestamp 
  CREATE TABLE t14 (
      birthday DATE , -- 生日
      job_time DATETIME, -- 记录年月日 时分秒
      login_time TIMESTAMP
      	NOT NULL DEFAULT CURRENT_TIMESTAMP
      	ON UPDATE CURRENT_TIMESTAMP); -- 登录时间, 如果希望 login_time 列自动更新, 需要配置
  
  
  SELECT * FROM t14;
  INSERT INTO t14(birthday, job_time) VALUES('2022-11-11','2022-11-11 10:10:10');
  -- 如果我们更新 t14 表的某条记录，login_time 列会自动的以当前时间进行更新 (重要！！！)
  ```

  

### 4. CRUD

#### 1. Insert	语句

- ![image-20211012192839051](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012192839051.png)

  ```mysql
  #练习 insert  语句
  -- 创建一张商品表 goods (id int , goods_name varchar(10), price double );
  -- 添加 2 条记录
  CREATE TABLE `goods` ( id INT ,
  	goods_name VARCHAR(10), -- 长度 10
  	price DOUBLE NOT NULL DEFAULT 100 );
  	
  -- 添加数据
  INSERT INTO `goods` (id, goods_name, price) 	VALUES(10, '华为手机', 2000);
  INSERT INTO `goods` (id, goods_name, price) 	VALUES(20, '苹果手机', 3000);
  SELECT * FROM goods;
  ```

- 细节说明

  ```mysql
  #说明 insert  语句的细节
  -- 1.插入的数据应与字段的数据类型相同。
  --  比如 把 'abc' 添加到 int 类型会错误
  INSERT INTO `goods` (id, goods_name, price)
  	VALUES('韩顺平', '小米手机', 2000);
  	
  -- 2.  数据的长度应在列的规定范围内，例如：不能将一个长度为 80 的字符串加入到长度为 40 的列中。
  INSERT INTO `goods` (id, goods_name, price)
  	VALUES(40, 'vovo 手机 vovo 手机 vovo 手机 vovo 手机 vovo 手机', 3000);
  
  -- 3.  在 values 中列出的数据位置必须与被加入的列的排列位置相对应。
  INSERT INTO `goods` (id, goods_name, price)	-- 不对
  	VALUES('vovo 手机',40, 2000);
  
  -- 4. 字符和日期型数据应包含在单引号中。
  INSERT INTO `goods` (id, goods_name, price)
  	VALUES(40, vovo 手机, 3000); -- 错误的 vovo 手机 应该 'vovo 手机'
  	
  -- 5. 列可以插入空值[前提是该字段允许为空]，insert into table value(null) 
  INSERT INTO `goods` (id, goods_name, price)
  	VALUES(40, 'vovo 手机', NULL);
  	
  -- 6. insert into tab_name (列名..)	values (),(),()	形式添加多条记录
  INSERT INTO `goods` (id, goods_name, price) 
  	VALUES(50, '三星手机', 2300),(60, '海尔手机', 1800);
  	
  -- 7.  如果是给表中的所有字段添加数据，可以不写前面的字段名称
  INSERT INTO `goods` VALUES(70, 'IBM 手机', 5000);
  
  -- 8.  默认值的使用，当不给某个字段值时，如果有默认值就会添加默认值，否则报错
  -- 如果某个列 没有指定 not null ,那么当添加数据时，没有给定值，则会默认给 null
  -- 如果我们希望指定某个列的默认值，可以在创建表时指定
  INSERT INTO `goods` (id, goods_name) VALUES(80, '格力手机');
  SELECT * FROM goods; 
  ```

#### 2. update 语句

- 使用 update 语句修改表中数据

  ![image-20211012193652070](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012193652070.png)

- 基本使用

  ![image-20211012193728536](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012193728536.png)

  ```mysql
  -- 演示 update 语句
  -- 要求:  在上面创建的 employee 表中修改表中的纪录
  -- 1. 将所有员工薪水修改为 5000 元。[如果没有带 where 条件，会修改所有的记录，因此要小心] 
  UPDATE employee SET salary = 5000
  
  -- 2. 将姓名为 小妖怪 的员工薪水修改为 3000 元。
  UPDATE employee SET salary = 3000
  	WHERE user_name = '小妖怪'
  	
  -- 3. 将 老妖怪 的薪水在原有基础上增加 1000 元
  INSERT INTO employee
  	VALUES(200, '老妖怪', '1990-11-11', '2000-11-11 10:10:10', '捶背的', 5000, '给大王捶背', 'd:\\a.jpg');
  UPDATE employee
  	SET salary = salary + 1000 WHERE user_name = '老妖怪'
  
  -- 可以修改多个列的值
  UPDATE employee
  	SET salary = salary + 1000 , job = '出主意的' WHERE user_name = '老妖怪'
  SELECT * FROM employee;
  ```

- 使用细节

  ![image-20211012193909205](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012193909205.png)



#### 3. delete 语句

- 使用 delete 语句删除表中数据

  ![image-20211012194041403](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194041403.png)

  ```mysql
  -- 删除表中名称为’老妖怪’的记录。
  DELETE FROM employee WHERE user_name = '老妖怪';
  -- 删除表中所有记录, 老师提醒，一定要小心
  DELETE FROM employee;
  
  -- Delete 语句不能删除某一列的值（可使用 update 设为 null 或者 ''） 
  UPDATE employee SET job = '' WHERE user_name = '老妖怪';
  SELECT * FROM employee
  
  -- 要删除这个表
  DROP TABLE employee;
  ```

- 细节

  ![image-20211012194249682](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194249682.png)

  

#### 4. select 语句

##### 1. 单表

- 基本语法

  ![image-20211012194333826](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194333826.png)

  - 注意事项

  ![image-20211012194401234](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194401234.png)

  - 练习

  ![image-20211012194432506](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194432506-16340390740632.png)

  ```mysql
  -- select 语句【重点 难点】
  CREATE TABLE student(
      id INT NOT NULL DEFAULT 1,
      NAME VARCHAR(20) NOT NULL DEFAULT '',
      chinese FLOAT NOT NULL DEFAULT 0.0,
      english FLOAT NOT NULL DEFAULT 0.0,
      math FLOAT NOT NULL DEFAULT 0.0
  );
  
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(1,'韩顺平',89,78,90); 
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(2,'张飞',67,98,56); 
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(3,'宋江',87,78,77); 
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(4,'关羽',88,98,90); 
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(5,'赵云',82,84,67); 
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(6,'欧阳锋',55,85,45); 
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(7,'黄蓉',75,65,30);
  INSERT INTO student(id,NAME,chinese,english,math) VALUES(8,'韩信',45,65,99);
  
  SELECT * FROM student;
  
  -- 查询表中所有学生的信息。
  SELECT * FROM student;
  -- 查询表中所有学生的姓名和对应的英语成绩。
  SELECT `name`,english FROM student;
  -- 过滤表中重复数据 distinct  。
  SELECT DISTINCT english FROM student;
  -- 要查询的记录，每个字段都相同，才会去重
  SELECT DISTINCT `name`, english FROM student;
  ```

- 使用表达式对查询的列进行运算

  ![image-20211012194733826](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194733826.png)

- 在select 语句中可使用 as 语句  (as 可以不写！！)

  ![image-20211012194801056](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194801056.png)

  - 练习

  ```mysql
  -- select 语句的使用
  
  -- 统计每个学生的总分
  SELECT `name`, (chinese+english+math) FROM student;
  -- 在所有学生总分加 10 分的情况
  SELECT `name`, (chinese + english + math + 10) FROM student;
  -- 使用别名表示学生分数。
  SELECT `name` AS '名字', (chinese + english + math + 10) AS total_score FROM student;
  ```

- 在where 子句中经常使用的运算符

  ![image-20211012194929702](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012194929702.png)

  - 使用where 子句，进行过滤查询

    ```mysql
    -- select 语句
    -- 查询姓名为赵云的学生成绩
    SELECT * FROM student WHERE `name` = '赵云'
    -- 查询英语成绩大于 90 分的同学
    SELECT * FROM student WHERE english > 90
    -- 查询总分大于 200 分的所有同学
    SELECT * FROM student
    WHERE (chinese + english + math) > 200
    
    -- 查询 math 大于 60  并且(and) id 大于 4 的学生成绩
    SELECT * FROM student WHERE math >60 AND id > 4
    -- 查询英语成绩大于语文成绩的同学
    SELECT * FROM student WHERE english > chinese
    
    -- 查询总分大于 200 分 并且 数学成绩小于语文成绩,的姓赵的学生.
    -- 赵% 表示 名字以赵开头的就可以
    SELECT * FROM student
    	WHERE (chinese + english + math) > 200 AND math < chinese AND `name` LIKE '赵%'
    -- 查询英语分数在 80－90 之间的同学。
    SELECT * FROM student
    	WHERE english >= 80 AND english <= 90; SELECT * FROM student
    	WHERE english BETWEEN 80 AND 90; -- between .. and ..  是 闭区间
    	
    -- 查询数学分数为 89,90,91 的同学。
    SELECT * FROM student
    WHERE math = 89 OR math = 90 OR math = 91; SELECT * FROM student
    WHERE math IN (89, 90, 91);
    -- 查询所有姓韩的学生成绩。
    SELECT * FROM student WHERE `name` LIKE '韩%'
    ```

- 使用order by 子句排序查询结果

  ![image-20211012195322917](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012195322917.png)

  ```mysql
  -- 演示 order by 使用
  -- 对数学成绩排序后输出【升序】。
  SELECT * FROM student ORDER BY math;
  -- 对总分按从高到低的顺序输出 [降序] -- 使用别名排序
  SELECT `name` , (chinese + english + math) AS total_score FROM student ORDER BY total_score DESC;
  -- 对姓韩的学生成绩[总分]排序输出(升序) where + order by
  SELECT `name`, (chinese + english + math) AS total_score FROM student WHERE `name` LIKE '韩%' ORDER BY total_score;
  
  ```

  

##### 2. 查询加强

- 介绍

  ![image-20211013140004056](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013140004056.png)

  ```mysql
  -- 查询加强
  -- ■ 使用 where 子句
  -- ?如何查找 1992.1.1 后入职的员工
  -- 老师说明： 在 mysql 中,日期类型可以直接比较,  需要注意格式
  SELECT * FROM emp
  	WHERE hiredate > '1992-01-01'
  	
  -- ■ 如何使用 like 操作符(模糊)
  -- %: 表示 0 到多个任意字符   _:  表示单个任意字符
  -- ?如何显示首字符为 S 的员工姓名和工资
  SELECT ename, sal FROM emp WHERE ename LIKE 'S%'
  -- ?如何显示第三个字符为大写 O 的所有员工的姓名和工资
  SELECT ename, sal FROM emp WHERE ename LIKE '__O%'
  
  -- ■ 如何显示没有上级的雇员的情况
  SELECT * FROM emp WHERE mgr IS NULL;
  -- ■ 查询表结构
  DESC emp
  
  -- 使用 order by 子句
  -- ?如何按照工资的从低到高的顺序[升序]，显示雇员的信息
  SELECT * FROM emp
  	ORDER BY sal
  -- ?按照部门号升序而雇员的工资降序排列 , 显示雇员信息
  SELECT * FROM emp
  	ORDER BY deptno ASC , sal DESC;
  ```

- 分页查询

  ![image-20211013140237966](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013140237966.png)

  ```mysql
  -- 分页查询
  -- 按雇员的 id 号升序取出， 每页显示 3 条记录，请分别显示 第 1 页，第 2 页，第 3 页
  
  -- 第 1 页
  SELECT * FROM emp
  	ORDER BY empno
      LIMIT 0, 3;
  -- 第 2 页
  SELECT * FROM emp
  	ORDER BY empno
      LIMIT 3, 3;
  -- 第 3 页
  SELECT * FROM emp
  	ORDER BY empno
      LIMIT 6, 3;
  -- 推导一个公式
  SELECT * FROM emp
  	ORDER BY empno
  	LIMIT 每页显示记录数 * (第几页-1) ,  每页显示记录数
  
  ```

- 使用分组函数和分组子句 group by

  ![image-20211013141503026](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013141503026.png)

  ```mysql
  -- 增强 group by  的使用
  
  
  -- (1) 显示每种岗位的雇员总数、平均工资。
  SELECT COUNT(*), AVG(sal), job
  FROM emp GROUP BY job;
  
  -- (2) 显示雇员总数，以及获得补助的雇员数。
  -- 思路: 获得补助的雇员数 就是 comm  列为非 null, 就是 count(列)，如果该列的值为 null,  是
  -- 不会统计 , SQL 非常灵活，需要我们动脑筋. 
  SELECT COUNT(*), COUNT(comm)
  FROM emp
  
  
  -- 老师的扩展要求：统计没有获得补助的雇员数
  SELECT COUNT(*), COUNT(IF(comm IS NULL, 1, NULL))
  FROM emp
  
  SELECT COUNT(*), COUNT(*) - COUNT(comm)
  FROM emp
  
  
  -- (3) 显示管理者的总人数。小技巧:尝试写->修改->尝试[正确的] 
  SELECT COUNT(DISTINCT mgr)
  FROM emp;
  
  -- (4) 显示雇员工资的最大差额。
  -- 思路： max(sal) - min(sal) 
  SELECT MAX(sal) - MIN(sal)
  FROM emp;
  
  
  SELECT * FROM emp;
  select * from dept;
  
  -- 应用案例：请统计各个部门 group by  的平均工资 avg，
  -- 并且是大于 1000 的 having，并且按照平均工资从高到低排序， order by
  -- 取出前两行记录 limit 0, 2
  
  SELECT deptno, AVG(sal) AS avg_sal FROM emp
  	GROUP BY deptno 
  	HAVING	avg_sal > 1000 
  	ORDER BY avg_sal DESC
  	LIMIT 0,2
  ```

  

##### 3. 多表

1. 

   - 说明

     ![image-20211013164757042](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013164757042.png)

   - 多表查询练习

     ![image-20211013164810922](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013164810922.png)

     ```mysql
     -- 多表查询
     -- ?显示雇员名,雇员工资及所在部门的名字 【笛卡尔集】
     /*
     老韩分析
     1. 雇员名,雇员工资 来自 emp 表
     2.部门的名字 来自 dept 表
     3.需求对 emp  和 dept 查询	ename,sal,dname,deptno
     4.当我们需要指定显示某个表的列是，需要 表.列表
     */
     SELECT ename,sal,dname,emp.deptno 
     FROM emp, dept
     WHERE emp.deptno = dept.deptno
     
     
     -- 老韩小技巧：多表查询的条件不能少于 表的个数-1,  否则会出现笛卡尔集
     -- ?如何显示部门号为 10 的部门名、员工名和工资
     SELECT ename,sal,dname,emp.deptno 
     FROM emp, dept
     WHERE emp.deptno = dept.deptno AND emp.deptno = 10
     
     
     -- ?显示各个员工的姓名，工资，及其工资的级别
     -- 思路 姓名，工资 来自 emp 13
     -- 工资级别 salgrade 5
     
     -- 写 sql , 先写一个简单，然后加入过滤条件... 
     select ename, sal, grade
     from emp , salgrade
     where 
     sal between losal and hisal;
     ```

2. 自连接

- ![image-20211013165306057](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013165306057.png)

  ```mysql
  -- 多表查询的 自连接
  
  -- 思考题:  显示公司员工名字和他的上级的名字
  
  -- 老韩分析： 员工名字 在 emp, 上级的名字的名字 emp
  -- 员工和上级是通过 emp 表的 mgr 列关联
  
  -- 这里老师小结：
  -- 自连接的特点 1.  把同一张表当做两张表使用
  -- 2. 需要给表取别名   表名 表别名
  -- 3. 列名不明确，可以指定列的别名 列名 as  列的别名
  
  SELECT worker.ename AS '职员名' , boss.ename AS '上级名' 
  FROM emp worker, emp boss
  WHERE worker.mgr = boss.empno;
  
  SELECT * FROM emp;
  ```



##### 4. 子查询

- 子查询是指嵌入在其它 sql 语句中的 select 语句,也叫嵌套查询；
- 单行子查询
  - 单行子查询是指只返回一行数据的子查询语句；

- 多行子查询

  - 多行子查询指返回多行数据的子查询	(使用关键字 in)

  ```mysql
  -- 子查询的演示
  -- 请思考：如何显示与 SMITH 同一部门的所有员工?
  /*
  1.先查询到 SMITH 的部门号得到
  2.把上面的 select  语句当做一个子查询来使用
  */
  SELECT deptno FROM emp
  	WHERE ename = 'SMITH'
  
  -- 下面的答案. 
  SELECT *
  	FROM emp 
  	WHERE deptno = (
  		SELECT deptno FROM emp
  			WHERE ename = 'SMITH'
  	)
  
  
  -- 课堂练习:如何查询和部门 10 的工作相同的雇员的
  -- 名字、岗位、工资、部门号,  但是不含 10 号部门自己的雇员.
  
  /*
  1.查询到 10 号部门有哪些工作
  2.把上面查询的结果当做子查询使用
  */
  select distinct job from emp
  	where deptno = 10;
  
  -- 下面语句完整
  
  select ename, job, sal, deptno 
  	from emp
  	where job in (
  		SELECT DISTINCT job
  			FROM emp WHERE deptno = 10
  	) and deptno <> 10
  ```

- 子查询当做临时表使用

  ![image-20211013170707099](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013170707099.png)

  ```mysql
  -- 查询 ecshop 中各个类别中，价格最高的商品
  
  -- 查询 商品表
  -- 先得到 各个类别中，价格最高的商品 max + group by cat_id,  当做临时表
  
  -- 把子查询当做一张临时表可以解决很多很多复杂的查询
  
  select cat_id , max(shop_price) from ecs_goods
  group by cat_id
  
  -- 这个最后答案
  select goods_id, ecs_goods.cat_id, goods_name, shop_price 
  	from (
  		SELECT cat_id , MAX(shop_price) as max_price 
          	FROM ecs_goods
  			GROUP BY cat_id
  	) temp , ecs_goods
  	where temp.cat_id = ecs_goods.cat_id
  	and temp.max_price = ecs_goods.shop_price
  ```

  

- 在多行子查询中使用 all ,any 操作符

  ![image-20211013170805599](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013170805599.png)

  ```mysql
  -- all  和 any 的使用
  
  -- 请思考:显示工资比部门 30 的所有员工的工资高的员工的姓名、工资和部门号
  
  SELECT ename, sal, deptno FROM emp
      WHERE sal > ALL(
                  SELECT sal
                      FROM emp
                          WHERE deptno = 30
                  )
  -- 可以这样写
  SELECT ename, sal, deptno FROM emp
  	WHERE sal > ( SELECT MAX(sal)
  					FROM emp WHERE deptno = 30
  				)
  
  -- 请思考:如何显示工资比部门 30 的其中一个员工的工资高的员工的姓名、工资和部门号
  
  SELECT ename, sal, deptno FROM emp
  WHERE sal > any( SELECT sal
  FROM emp WHERE deptno = 30
  )
  
  SELECT ename, sal, deptno FROM emp
  WHERE sal > ( SELECT min(sal)
  FROM emp
     WHERE deptno = 30
  )
  ```

  

- 多列子查询

  ![image-20211013171549150](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013171549150.png)

  ```mysql
  -- 多列子查询
  
  -- 请思考如何查询与 allen 的部门和岗位完全相同的所有雇员(并且不含 allen 本人)
  -- (字段 1， 字段 2 ...) = (select  字段 1，字段 2 from  。。。。)
  
  -- 分析: 1.  得到 smith 的部门和岗位
  
  SELECT deptno , job FROM emp
  WHERE ename = 'ALLEN'
  
  -- 分析: 2	把上面的查询当做子查询来使用，并且使用多列子查询的语法进行匹配
  SELECT *
  FROM emp
  WHERE (deptno , job) = ( SELECT deptno , job 
                          	FROM emp
  							WHERE ename = 'ALLEN'
  						) AND ename != 'ALLEN'
  
  
  -- 请查询 和宋江数学，英语，语文
  -- 成绩 完全相同的学生
  SELECT *
  FROM student
  WHERE (math, english, chinese) = ( SELECT math, english, chinese FROM student
  WHERE `name` = '宋江'
  )
  
  SELECT * FROM student;
  ```

  

- 在from 子句中使用子查询

  ![image-20211013172034584](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013172034584.png)

```mysql
-- 子查询练习

-- 请思考：查找每个部门工资高于本部门平均工资的人的资料
-- 这里要用到数据查询的小技巧，把一个子查询当作一个临时表使用

-- 1. 先得到每个部门的 部门号和 对应的平均工资
SELECT deptno, AVG(sal) AS avg_sal FROM emp GROUP BY deptno

-- 2.  把上面的结果当做子查询,  和 emp 进行多表查询
--
SELECT ename, sal, temp.avg_sal, emp.deptno 
FROM emp, (
    SELECT deptno, AVG(sal) AS avg_sal FROM emp
		GROUP BY deptno
	) temp
WHERE emp.deptno = temp.deptno AND emp.sal > temp.avg_sal


-- 查找每个部门工资最高的人的详细资料
SELECT ename, sal, temp.max_sal, emp.deptno 
FROM emp, (
	SELECT deptno, MAX(sal) AS max_sal FROM emp
		GROUP BY deptno
	) temp
WHERE emp.deptno = temp.deptno AND emp.sal = temp.max_sal


-- 查询每个部门的信息(包括：部门名,编号,地址)和人员数量,我们一起完成。
-- 1.  部门名,编号,地址 来自 dept 表
-- 2.  各个部门的人员数量 -》 构建一个临时表

SELECT COUNT(*), deptno FROM emp
GROUP BY deptno;

SELECT dname, dept.deptno, loc , tmp.per_num AS '人数'
FROM dept, (
	SELECT COUNT(*) AS per_num, deptno FROM emp
		GROUP BY deptno
	) tmp
WHERE tmp.deptno = dept.deptno

-- 还有一种写法 表.*  表示将该表所有列都显示出来,  可以简化 sql 语句

-- 在多表查询中，当多个表的列不重复时，才可以直接写列名

SELECT tmp.* , dname, loc FROM dept, (
SELECT COUNT(*) AS per_num, deptno FROM emp
GROUP BY deptno
) tmp
WHERE tmp.deptno = dept.deptno
```



##### 5. 表复制

- 自我复制数据(蠕虫复制) （有主键的表不能自我复制，主键列不能重复）

  ![image-20211013172753496](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013172753496.png)

  ```mysql
  -- 表的复制
  -- 为了对某个 sql 语句进行效率测试，我们需要海量数据时，可以使用此法为表创建海量数据
  
  CREATE TABLE my_tab01 ( id INT,
  `name` VARCHAR(32), sal DOUBLE,
  job VARCHAR(32),
  deptno INT);
  DESC my_tab01
  SELECT * FROM my_tab01;
  
  -- 演示如何自我复制
  -- 1. 先把 emp 表的记录复制到 my_tab01 
  INSERT INTO my_tab01
  (id, `name`, sal, job,deptno)
  SELECT empno, ename, sal, job, deptno FROM emp;
  -- 2. 自我复制
  INSERT INTO my_tab01 
  	SELECT * FROM my_tab01;
  	
  SELECT COUNT(*) FROM my_tab01;
  
  -- 如何删除掉一张表重复记录
  -- 1.  先创建一张表 my_tab02,
  -- 2.  让 my_tab02 有重复的记录
  
  CREATE TABLE my_tab02 LIKE emp; -- 这个语句 把 emp 表的结构(列)，复制到 my_tab02
  DESC my_tab02;
  
  INSERT INTO my_tab02 SELECT * FROM emp;
  
  SELECT * FROM my_tab02;
  
  (面试题！！！！！)
  -- 3.  考虑去重 my_tab02 的记录 （重要！！！）
  /*
  思路
  (1)先创建一张临时表 my_tmp ,  该表的结构和 my_tab02 一样
  (2)把 my_tmp  的记录 通过 distinct  关键字 处理后 把记录复制到 my_tmp
  (3)清除掉 my_tab02 记录
  (4)把 my_tmp  表的记录复制到 my_tab02
  (5)drop 掉 临时表 my_tmp
  */
  -- (1) 先创建一张临时表 my_tmp ,  该表的结构和 my_tab02 一样
  
  create table my_tmp like my_tab02
  
  -- (2) 把 my_tmp 的记录 通过 distinct 关键字 处理后 把记录复制到 my_tmp 
  insert into my_tmp
  	select distinct * from my_tab02;
  	
  -- (3) 清除掉 my_tab02 记录
  delete from my_tab02;
  
  -- (4) 把 my_tmp 表的记录复制到 my_tab02 
  insert into my_tab02
  	select * from my_tmp;
  	
  -- (5) drop 掉 临时表 my_tmp 
  drop table my_tmp;
  
  select * from my_tab02;
  ```

  

##### 6. 合并查询

- 介绍

  ![image-20211013173516649](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013173516649.png)

  ```mysql
  -- 合并查询
  
  SELECT ename,sal,job FROM emp WHERE sal>2500 -- 5
  
  SELECT ename,sal,job FROM emp WHERE job='MANAGER' -- 3
  
  
  -- union all  就是将两个查询结果合并，不会去重
  SELECT ename,sal,job FROM emp WHERE sal>2500 -- 5 UNION ALL
  SELECT ename,sal,job FROM emp WHERE job='MANAGER' -- 3
  
  -- union	就是将两个查询结果合并，会去重
  SELECT ename,sal,job FROM emp WHERE sal>2500 -- 5 UNION
  SELECT ename,sal,job FROM emp WHERE job='MANAGER' -- 3
  ```

  

### 5. 函数

#### 1. 合计/统计函数

1. count

   ![image-20211012200237897](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211012200237897-16340401593743.png)

   ```mysql
   -- 演示 mysql 的统计函数的使用
   -- 统计一个班级共有多少学生？
   SELECT COUNT(*) FROM student;
   -- 统计数学成绩大于 90 的学生有多少个？
   SELECT COUNT(*) FROM student WHERE math > 90
   -- 统计总分大于 250 的人数有多少？
   SELECT COUNT(*) FROM student
   	WHERE (math + english + chinese) > 250
   	
   -- count(*) 和 count(列) 的区别
   -- 解释 :count(*) 返回满足条件的记录的行数
   -- count(列): 统计满足条件的某列有多少个，但是会排除 为 null 的情况
   CREATE TABLE t15 (
   	`name` VARCHAR(20)); 
   INSERT INTO t15 VALUES('tom'); 
   INSERT INTO t15 VALUES('jack'); 
   INSERT INTO t15 VALUES('mary'); 
   INSERT INTO t15 VALUES(NULL); 
   SELECT * FROM t15;
   SELECT COUNT(*) FROM t15; -- 4 
   SELECT COUNT(`name`) FROM t15;-- 3
   ```
   
2. sum

   ![image-20211013103145502](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013103145502.png)

   ```mysql
   -- 演示 sum 函数的使用
   -- 统计一个班级数学总成绩？
   SELECT SUM(math) FROM student;
   -- 统计一个班级语文、英语、数学各科的总成绩
   SELECT SUM(math) AS math_total_score,SUM(english),SUM(chinese) FROM student;
   -- 统计一个班级语文、英语、数学的成绩总和
   SELECT SUM(math + english + chinese) FROM student;
   -- 统计一个班级语文成绩平均分
   SELECT SUM(chinese)/ COUNT(*)	FROM student; 
   ```

3. avg

   ![image-20211013103514809](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013103514809.png)

   ```mysql
   -- 演示 avg 的使用
   -- 练习：
   -- 求一个班级数学平均分？
   SELECT AVG(math) FROM student;
   -- 求一个班级总分平均分
   SELECT AVG(math + english + chinese) FROM student;
   ```

4. max/min

   ![image-20211013103544909](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013103544909.png)

   ```mysql
   -- 演示 max 和 min 的使用
   -- 求班级最高分和最低分（数值范围在统计中特别有用）
   SELECT MAX(math + english + chinese), MIN(math + english + chinese) FROM student;
   -- 求出班级数学最高分和最低分
   SELECT MAX(math) AS math_high_socre, MIN(math)	AS math_low_socre FROM student;
   ```

5. 使用group by 子句对列进行分组

   ![image-20211013103841044](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013103841044.png)

6. 使用having 子句对分组后的结果进行过滤

   ![image-20211013103857741](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013103857741.png)

   ![image-20211013103902395](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013103902395.png)

   ```mysql
   CREATE TABLE dept( /*部门表*/
   	deptno MEDIUMINT UNSIGNED NOT NULL	DEFAULT 0, 
       dname VARCHAR(20) NOT NULL	DEFAULT "",
   	loc VARCHAR(13) NOT NULL DEFAULT ""
   );
   INSERT INTO dept VALUES(10, 'ACCOUNTING', 'NEW YORK'), (20, 'RESEARCH', 'DALLAS'),
   (30, 'SALES', 'CHICAGO'),(40, 'OPERATIONS', 'BOSTON');
   
   SELECT * FROM dept;
   
   -- 员工表
   
   CREATE TABLE emp(
       empno	MEDIUMINT UNSIGNED	NOT NULL	DEFAULT 0, /*编号*/ 
       ename VARCHAR(20) NOT NULL DEFAULT "", /*名字*/
   	job VARCHAR(9) NOT NULL DEFAULT "",/*工作*/
   	mgr MEDIUMINT UNSIGNED ,/*上级编号*/ 
       hiredate DATE NOT NULL,/*入职时间*/
   	sal DECIMAL(7,2)	NOT NULL,/*薪水*/ 
       comm DECIMAL(7,2) ,/*红利 奖金*/
   	deptno MEDIUMINT UNSIGNED NOT NULL DEFAULT 0 /*部门编号*/
   );
   
   -- 添加测试数据
   INSERT INTO emp VALUES(7369, 'SMITH', 'CLERK', 7902, '1990-12-17', 800.00,NULL , 20), (7499, 'ALLEN', 'SALESMAN', 7698, '1991-2-20', 1600.00, 300.00, 30),
   (7521, 'WARD', 'SALESMAN', 7698, '1991-2-22', 1250.00, 500.00, 30),
   (7566, 'JONES', 'MANAGER', 7839, '1991-4-2', 2975.00,NULL,20),
   (7654, 'MARTIN', 'SALESMAN', 7698, '1991-9-28',1250.00,1400.00,30),
   (7698, 'BLAKE','MANAGER', 7839,'1991-5-1', 2850.00,NULL,30),
   (7782, 'CLARK','MANAGER', 7839, '1991-6-9',2450.00,NULL,10),
   (7788, 'SCOTT','ANALYST',7566, '1997-4-19',3000.00,NULL,20),
   (7839, 'KING','PRESIDENT',NULL,'1991-11-17',5000.00,NULL,10),
   (7844, 'TURNER', 'SALESMAN',7698, '1991-9-8', 1500.00, NULL,30),
   (7900, 'JAMES','CLERK',7698, '1991-12-3',950.00,NULL,30),
   (7902, 'FORD', 'ANALYST',7566,'1991-12-3',3000.00, NULL,20),
   (7934,'MILLER','CLERK',7782,'1992-1-23', 1300.00, NULL,10);
   
   SELECT * FROM emp;
   
   -- 工资级别
   #工资级别表
   CREATE TABLE salgrade (
   	grade MEDIUMINT UNSIGNED NOT NULL DEFAULT 0, /*工资级别*/
   	losal DECIMAL(17,2)	NOT NULL, /* 该级别的最低工资 */ 
       hisal DECIMAL(17,2)	NOT NULL /* 该级别的最高工资*/
   );
   
   INSERT INTO salgrade VALUES (1,700,1200); 
   INSERT INTO salgrade VALUES (2,1201,1400); 
   INSERT INTO salgrade VALUES (3,1401,2000);
   INSERT INTO salgrade VALUES (4,2001,3000); 
   INSERT INTO salgrade VALUES (5,3001,9999);
   SELECT * FROM salgrade; 
   SELECT * FROM dept; 
   SELECT * FROM emp;
   
   # 演示 group by + having
   -- GROUP by 用于对查询的结果分组统计, (示意图)
   -- having 子句用于限制分组显示结果.
   -- ?如何显示每个部门的平均工资和最高工资
   -- 老韩分析: avg(sal) max(sal)
   -- 按照部分来分组查询
   SELECT AVG(sal), MAX(sal) , deptno FROM	emp GROUP BY deptno;
   -- 使用数学方法，对小数点进行处理
   SELECT FORMAT(AVG(sal),2), MAX(sal) , deptno FROM	emp GROUP BY deptno;
   
   -- ?显示每个部门的每种岗位的平均工资和最低工资
   -- 老师分析 1.  显示每个部门的平均工资和最低工资
   -- 2. 显示每个部门的每种岗位的平均工资和最低工资
   SELECT AVG(sal), MIN(sal) , deptno, job FROM	emp GROUP BY deptno, job;
   
   -- ?显示平均工资低于 2000 的部门号和它的平均工资 // 别名
   
   -- 老师分析 [写 sql 语句的思路是化繁为简,各个击破]
   -- 1. 显示各个部门的平均工资和部门号
   -- 2. 在 1 的结果基础上，进行过滤，保留 AVG(sal) < 2000
   -- 3. 使用别名进行过滤
   
   
   SELECT AVG(sal), deptno
   FROM emp GROUP BY deptno HAVING AVG(sal) < 2000;
   -- 使用别名
   SELECT AVG(sal) AS avg_sal, deptno FROM emp GROUP BY deptno
   HAVING avg_sal < 2000;
   ```

   

#### 2. 字符串相关函数

![image-20211013105040682](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013105040682.png)

```mysql
-- CHARSET(str)	返回字符串字符集
SELECT CHARSET(ename) FROM emp;

-- CONCAT (string2 [,... ]) 连接字串, 将多个列拼接成一列
SELECT CONCAT(ename, ' 工作是 ', job) FROM emp;

-- INSTR (string ,substring ) 返回 substring 在 string 中出现的位置,没有返回 0
-- dual 亚元表,  系统表 可以作为测试表使用
SELECT INSTR('hanshunping', 'ping') FROM DUAL;

-- UCASE (string2 ) 转换成大写
SELECT UCASE(ename) FROM emp;

-- LCASE (string2 ) 转换成小写

SELECT LCASE(ename) FROM emp;

-- LEFT (string2 ,length )从 string2 中的左边起取 length 个字符
-- RIGHT (string2 ,length )	从 string2 中的右边起取 length 个字符
SELECT LEFT(ename, 2) FROM emp;


-- LENGTH (string ) string 长度[按照字节] 
SELECT LENGTH(ename) FROM emp;

-- REPLACE (str ,search_str ,replace_str )
-- 在 str 中用 replace_str 替换 search_str
-- 如果是 manager 就替换成 经理
SELECT ename, REPLACE(job,'MANAGER', '经理')	FROM emp;

-- STRCMP (string1 ,string2 )	逐字符比较两字串大小
SELECT STRCMP('hsp', 'hsp') FROM DUAL;

-- SUBSTRING (str , position [,length ])
-- 从 str 的 position 开始【从 1 开始计算】,取 length 个字符
-- 从 ename 列的第一个位置开始取出 2 个字符
SELECT SUBSTRING(ename, 1, 2) FROM emp;

-- LTRIM (string2 ) RTRIM (string2 )	TRIM(string)
-- 去除前端空格或后端空格
SELECT LTRIM('	韩顺平教育') FROM DUAL; 
SELECT RTRIM('韩顺平教育	') FROM DUAL; 
SELECT TRIM('		韩顺平教育		') FROM DUAL;

-- 练习:  以首字母小写的方式显示所有员工 emp 表的姓名
-- 方法 1
-- 思路先取出 ename 的第一个字符，转成小写的
-- 把他和后面的字符串进行拼接输出即可
SELECT CONCAT(LCASE(SUBSTRING(ename,1,1)),	SUBSTRING(ename,2)) AS new_name
FROM emp;

SELECT CONCAT(LCASE(LEFT(ename,1)),	SUBSTRING(ename,2)) AS new_name
FROM emp;
```



#### 3. 数学相关函数

![image-20211013105439711](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013105439711.png)

```mysql
-- 演示数学相关函数

-- ABS(num)	绝对值
SELECT ABS(-10) FROM DUAL;
-- BIN (decimal_number )十进制转二进制
SELECT BIN(10) FROM DUAL;
-- CEILING (number2 ) 向上取整,  得到比 num2 大的最小整数
SELECT CEILING(-1.1) FROM DUAL;

-- CONV(number2,from_base,to_base)	进制转换
-- 下面的含义是 8  是十进制的 8,  转成 2 进制输出
SELECT CONV(8, 10, 2) FROM DUAL;
-- 下面的含义是 16  是 16 进制的 16,  转成 10 进制输出
SELECT CONV(16, 16, 10) FROM DUAL; -- 22

-- FLOOR (number2 )	向下取整,得到比 num2 小的最大整数
SELECT FLOOR(-1.1) FROM DUAL;

-- FORMAT (number,decimal_places )	保留小数位数(四舍五入) 
SELECT FORMAT(78.125458,2) FROM DUAL;

-- HEX (DecimalNumber )	转十六进制

-- LEAST (number , number2  [,..])	求最小值
SELECT LEAST(0,1, -10, 4) FROM DUAL;

-- MOD (numerator ,denominator )	求余
SELECT MOD(10, 3) FROM DUAL;

-- RAND([seed])	RAND([seed]) 返回随机数 其范围为 0 ≤ v ≤ 1.0
-- 老韩说明
-- 1.  如果使用 rand() 每次返回不同的随机数 ，在 0 ≤ v ≤ 1.0
-- 2.  如果使用 rand(seed) 返回随机数,  范围 0 ≤ v ≤ 1.0, 如果 seed 不变，
-- 该随机数也不变了
SELECT RAND() FROM DUAL;
```



#### 4. 时间日期相关函数

![image-20211013105858109](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013105858109.png)

LAST_DAY(日期)，可以返回该日期所在月份的最后一天

![image-20211013110145574](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013110145574.png)

![img](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\wps4-16340941716532.png)

```mysql
-- 日期时间相关函数

-- CURRENT_DATE (   )	当前日期
SELECT CURRENT_DATE() FROM DUAL;
-- CURRENT_TIME ( )当前时间
SELECT CURRENT_TIME()	FROM DUAL;
-- CURRENT_TIMESTAMP (	)  当前时间戳
SELECT CURRENT_TIMESTAMP()	FROM DUAL;


-- 创建测试表 信息表
CREATE TABLE mes(
	id INT ,
	content VARCHAR(30), 
    send_time DATETIME);

-- 添加一条记录
INSERT INTO mes VALUES(1, '北京新闻', CURRENT_TIMESTAMP()); 
INSERT INTO mes VALUES(2, '上海新闻', NOW()); 
INSERT INTO mes VALUES(3, '广州新闻', NOW());

SELECT * FROM mes; 
SELECT NOW() FROM DUAL;

-- 上应用实例
-- 显示所有新闻信息，发布日期只显示 日期，不用显示时间. 
SELECT id, content, DATE(send_time) FROM mes;

-- 请查询在 10 分钟内发布的新闻,  思路一定要梳理一下. 
SELECT * FROM mes
	WHERE DATE_ADD(send_time, INTERVAL 10 MINUTE) >= NOW()

SELECT * FROM mes
	WHERE send_time >= DATE_SUB(NOW(), INTERVAL 10 MINUTE)  
	
-- 请在 mysql 的 sql 语句中求出 2011-11-11 和 1990-1-1  相差多少天
SELECT DATEDIFF('2011-11-11', '1990-01-01') FROM DUAL;

-- 请用 mysql 的 sql 语句求出你活了多少天? [练习] 1986-11-11 出生
SELECT DATEDIFF(NOW(), '1986-11-11') FROM DUAL;

-- 如果你能活 80 岁，求出你还能活多少天.[练习] 1986-11-11 出生
-- 先求出活 80 岁 时,  是什么日期 X
-- 然后在使用 datediff(x, now()); 1986-11-11->datetime
-- INTERVAL 80 YEAR  ： YEAR 可以是 年月日，时分秒
-- '1986-11-11' 可以 date,datetime timestamp
SELECT DATEDIFF(DATE_ADD('1986-11-11', INTERVAL 80 YEAR), NOW()) FROM DUAL;

SELECT TIMEDIFF('10:11:11', '06:10:10') FROM DUAL;


-- YEAR|Month|DAY| DATE (datetime ) 
SELECT YEAR(NOW()) FROM DUAL; 
SELECT MONTH(NOW()) FROM DUAL; 
SELECT DAY(NOW()) FROM DUAL; 
SELECT MONTH('2013-11-10') FROM DUAL;

-- unix_timestamp() :  返回的是 1970-1-1  到现在的秒数
SELECT UNIX_TIMESTAMP() FROM DUAL;

-- FROM_UNIXTIME() : 可以把一个 unix_timestamp  秒数[时间戳]，转成指定格式的日期
-- %Y-%m-%d 格式是规定好的，表示年月日
-- 意义：在开发中，可以存放一个整数，然后表示时间，通过 FROM_UNIXTIME 转换
SELECT FROM_UNIXTIME(1618483484, '%Y-%m-%d') FROM DUAL;
SELECT FROM_UNIXTIME(1618483100, '%Y-%m-%d %H:%i:%s') FROM DUAL;
```



#### 5. 加密和系统函数

![image-20211013110942867](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013110942867.png)

```mysql
-- 演示加密函数和系统函数

-- USER()	查询用户
-- 可以查看登录到 mysql 的有哪些用户，以及登录的 IP
SELECT USER() FROM DUAL; -- 用户@IP 地址

-- DATABASE()查询当前使用数据库名称
SELECT DATABASE();

-- MD5(str) 为字符串算出一个 MD5 32 的字符串，常用(用户密码)加密
-- root  密码是 hsp -> 加密 md5 -> 在数据库中存放的是加密后的密码
SELECT MD5('hsp') FROM DUAL;
SELECT LENGTH(MD5('hsp')) FROM DUAL;

-- 演示用户表，存放密码时，是 md5 
CREATE TABLE hsp_user(
    id INT ,
	`name` VARCHAR(32) NOT NULL DEFAULT '', 
    pwd CHAR(32) NOT NULL DEFAULT '');
    
INSERT INTO hsp_user
	VALUES(100, '韩顺平', MD5('hsp'));
SELECT * FROM hsp_user; -- csdn

SELECT * FROM hsp_user	-- SQL 注入问题
	WHERE `name`='韩顺平' AND pwd = MD5('hsp')


-- PASSWORD(str) -- 加密函数, MySQL 数据库的用户密码就是 PASSWORD 函数加密
SELECT PASSWORD('hsp') FROM DUAL; -- 数据库的 *81220D972A52D4C51BB1C37518A2613706220DAC

-- select * from mysql.user \G	从原文密码 str 计算并返回密码字符串
-- 通常用于对 mysql 数据库的用户密码加密
-- mysql.user 表示 数据库.表
SELECT * FROM mysql.user
```



#### 6. 流程控制函数

![image-20211013111249617](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013111249617.png)

![image-20211013111520231](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013111520231.png)

```mysql
# 演示流程控制语句


# IF(expr1,expr2,expr3) 如果 expr1 为 True ,则返回 expr2 否则返回 expr3 
SELECT IF(TRUE, '北京', '上海') FROM DUAL;

# IFNULL(expr1,expr2) 如果 expr1 不为空 NULL,则返回 expr1,否则返回 expr2
SELECT IFNULL( NULL, '韩顺平教育') FROM DUAL;

# SELECT CASE WHEN expr1 THEN expr2 WHEN expr3 THEN expr4 ELSE expr5 END; [类似多重分支.]
# 如果 expr1 为 TRUE,则返回 expr2,如果 expr2  为 t, 返回 expr4,  否则返回 expr5

SELECT CASE
WHEN TRUE THEN 'jack'	-- jack 
WHEN FALSE THEN 'tom'
ELSE 'mary' END


-- 1.  查询 emp 表,  如果 comm 是 null ,  则显示 0.0
-- 老师说明，判断是否为 null 要使用 is null, 判断不为空 使用 is not 
SELECT ename, IF(comm IS NULL , 0.0, comm) FROM emp;
SELECT ename, IFNULL(comm, 0.0) FROM emp;

-- 2.  如果 emp 表的 job 是 CLERK 则显示 职员， 如果是 MANAGER 则显示经理
-- 如果是 SALESMAN 则显示 销售人员，其它正常显示

SELECT ename, (SELECT CASE
				WHEN job = 'CLERK' THEN ' 职 员 ' 
               	WHEN job = 'MANAGER' THEN '经理'
				WHEN job = 'SALESMAN' THEN '销售人员'
				ELSE job END) AS 'job' 
				FROM emp;

SELECT * FROM emp;
SELECT * FROM dept;
SELECT * FROM salgrade;
```



### 6. 内连接

### 7. 外连接

- ![image-20211013184247828](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013184247828.png)

  ![image-20211013184302486](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013184302486.png)

  ```mysql
  -- 外连接
  
  
  -- 比如：列出部门名称和这些部门的员工名称和工作，
  -- 同时要求 显示出那些没有员工的部门。
  
  -- 使用我们学习过的多表查询的 SQL， 看看效果如何?
  
  SELECT dname, ename, job FROM emp, dept
  WHERE emp.deptno = dept.deptno
  ORDER BY dname SELECT * FROM dept;
  
  SELECT * FROM emp;
  
  
  -- 创建 stu
  /*
  id	name
  1Jack
  2Tom
  3Kity
  4nono
  */
  CREATE TABLE stu (
  id INT,
  `name` VARCHAR(32));
  INSERT INTO stu VALUES(1, 'jack'),(2,'tom'),(3, 'kity'),(4, 'nono'); 
  SELECT * FROM stu;
  -- 创建 exam
  /*
  id	grade
  1	56
  2	76
  11	8
  */
  CREATE TABLE exam(
  id INT, grade INT);
  INSERT INTO exam VALUES(1, 56),(2,76),(11, 8);
  SELECT * FROM exam;
  
  -- 使用左连接
  -- （显示所有人的成绩，如果没有成绩，也要显示该人的姓名和 id 号,成绩显示为空）
  
  SELECT `name`, stu.id, grade 
  	FROM stu, exam
      WHERE stu.id = exam.id;
  
  -- 改成左外连接
  SELECT `name`, stu.id, grade 
  	FROM stu LEFT JOIN exam
      ON stu.id = exam.id;
  
  -- 使用右外连接（显示所有成绩，如果没有名字匹配，显示空)
  -- 即：右边的表(exam) 和左表没有匹配的记录，也会把右表的记录显示出来
  SELECT `name`, stu.id, grade 
  	FROM stu RIGHT JOIN exam 
  	ON stu.id = exam.id;
  
  
  -- 列出部门名称和这些部门的员工信息(名字和工作)，
  -- 同时列出那些没有员工的部门名。5min
  -- 使用左外连接实现
  SELECT dname, ename, job 
      FROM dept LEFT JOIN emp 
      ON dept.deptno = emp.deptno
  
  -- 使用右外连接实现
  SELECT dname, ename, job 
      FROM emp RIGHT JOIN dept 
      ON dept.deptno = emp.deptno
  ```

  

### 8. 约束

- 基本介绍

  ![image-20211013185659147](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013185659147.png)

- primary key(主键)-基本使用

  ![image-20211013185731706](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013185731706.png)

  ![image-20211013185736348](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013185736348.png)

  ```mysql
  -- 主键使用
  
  -- id	name	email 
  CREATE TABLE t17
  (id INT PRIMARY KEY, -- 表示 id 列是主键
  `name` VARCHAR(32),
   email VARCHAR(32));
  
  -- 主键列的值是不可以重复
  INSERT INTO t17
  VALUES(1, 'jack', 'jack@sohu.com'); 
  INSERT INTO t17
  VALUES(2, 'tom', 'tom@sohu.com');
  
  INSERT INTO t17
  VALUES(1, 'hsp', 'hsp@sohu.com'); -- 报错的
  
  SELECT * FROM t17;
  
  
  -- 主键使用的细节讨论
  -- primary key 不能重复而且不能为 null。
  INSERT INTO t17
  VALUES(NULL, 'hsp', 'hsp@sohu.com');
  
  -- 一张表最多只能有一个主键,  但可以是复合主键(比如 id+name)
  CREATE TABLE t18
  (id INT PRIMARY KEY, -- 表示 id 列是主键
  `name` VARCHAR(32), PRIMARY KEY -- 错误的
  email VARCHAR(32));
  -- 演示复合主键 (id  和 name 做成复合主键)
  CREATE TABLE t18 (id INT ,
  `name` VARCHAR(32),
   email VARCHAR(32),
  PRIMARY KEY (id, `name`) -- 这里就是复合主键
  );
  
  INSERT INTO t18
  VALUES(1, 'tom', 'tom@sohu.com'); 
  INSERT INTO t18
  VALUES(1, 'jack', 'jack@sohu.com'); 
  INSERT INTO t18
  VALUES(1, 'tom', 'xx@sohu.com'); -- 这里就违反了复合主键
  SELECT * FROM t18;
  
  
  -- 主键的指定方式 有两种
  -- 1.  直接在字段名后指定：字段名	primakry key
  -- 2.  在表定义最后写 primary key(列名);
  CREATE TABLE t19 (id INT ,
  `name` VARCHAR(32) PRIMARY KEY,
  email VARCHAR(32)
  );
  
  CREATE TABLE t20 (id INT ,
  `name` VARCHAR(32) , email VARCHAR(32),
  PRIMARY KEY(`name`) -- 在表定义最后写 primary key(列名)
                    );
  
  -- 使用 desc 表名，可以看到 primary key 的情况
  DESC t20 -- 查看 t20 表的结果，显示约束的情况
  DESC t18
  ```

- not null(非空)

  ![image-20211013190444906](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013190444906.png)

- unique(唯一)

  ![image-20211013190510135](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013190510135.png)

  ![image-20211013190518338](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013190518338.png)

  ```mysql
  -- unique 的使用
  
  CREATE TABLE t21
  (id INT UNIQUE ,	-- 表示 id  列是不可以重复的.
  `name` VARCHAR(32) , 
   email VARCHAR(32)
  );
  
  INSERT INTO t21
  VALUES(1, 'jack', 'jack@sohu.com');
  
  INSERT INTO t21
  VALUES(1, 'tom', 'tom@sohu.com'); --  加不进去
  
  
  -- unqiue 使用细节
  -- 1. 如果没有指定 not null ,  则 unique 字段可以有多个 null
  -- 如果一个列(字段)， 是 unique not null 使用效果类似 primary key 
  INSERT INTO t21
  VALUES(NULL, 'tom', 'tom@sohu.com'); 
  SELECT * FROM t21;
  
  -- 2. 一张表可以有多个 unique 字段
  CREATE TABLE t22
  (id INT UNIQUE ,	-- 表示 id  列是不可以重复的.
  `name` VARCHAR(32) UNIQUE , -- 表示 name 不可以重复
  email VARCHAR(32)
  ); 
  DESC t22
  ```

- foreign key(外键)

   ![image-20211013191224023](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013191224023.png)

   细节：![img](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\wps11-16341243259213.png)

  ```mysql
  -- 外键演示
  
  -- 创 建 主 表 my_class 
  CREATE TABLE my_class (
  id INT PRIMARY KEY , -- 班级编号
  `name` VARCHAR(32) NOT NULL DEFAULT '');
  
  
  -- 创 建 从 表 my_stu 
  CREATE TABLE my_stu (
  id INT PRIMARY KEY , -- 学生编号
  `name` VARCHAR(32) NOT NULL DEFAULT '',
  class_id INT , -- 学生所在班级的编号
  -- 下面指定外键关系
  FOREIGN KEY (class_id) REFERENCES my_class(id))
  
  -- 测试数据
  INSERT INTO my_class VALUES(100, 'java'), (200, 'web');
  INSERT INTO my_class VALUES(300, 'php');
  
  SELECT * FROM my_class; 
  INSERT INTO my_stu
  VALUES(1, 'tom', 100);
  INSERT INTO my_stu VALUES(2, 'jack', 200);
  INSERT INTO my_stu
  VALUES(3, 'hsp', 300);
  INSERT INTO my_stu
  VALUES(4, 'mary', 400); -- 这里会失败...因为 400 班级不存在
  
  INSERT INTO my_stu
  VALUES(5, 'king', NULL); -- 可以, 外键 没有写 not null 
  SELECT * FROM my_class;
  
  -- 一旦建立主外键的关系，数据不能随意删除了
  DELETE FROM my_class 
  	WHERE id = 100;
  ```

- check

  ![image-20211013193201853](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013193201853.png)

  ```mysql
  -- 演示 check 的使用
  -- mysql5.7 目前还不支持 check ,只做语法校验，但不会生效
  -- 了解
  -- 学习 oracle, sql server, 这两个数据库是真的生效.
  
  -- 测试
  CREATE TABLE t23 (
  id INT PRIMARY KEY,
  `name` VARCHAR(32) ,
  -- 可以使用枚举  ENUM('男','女')  生效！！！！！
  sex VARCHAR(6) CHECK (sex IN('man','woman')), 
  sal DOUBLE CHECK ( sal > 1000 AND sal < 2000)
  );
  
  -- 添加数据
  INSERT INTO  t23 VALUES(1, 'jack', 'mid', 1);
  SELECT * FROM t23;
  ```

- 自增长

  - 介绍

    ![image-20211013194938361](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013194938361.png)

  - 自增长使用细节

    ![image-20211013195012442](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211013195012442.png)

    ```mysql
    -- 演示自增长的使用
    -- 创建表
    CREATE TABLE t24
    (id INT PRIMARY KEY AUTO_INCREMENT, 
     email VARCHAR(32)NOT NULL DEFAULT '',
    `name` VARCHAR(32)NOT NULL DEFAULT ''); 
    DESC t24
    
    -- 测试自增长的使用
    INSERT INTO t24
    VALUES(NULL, 'tom@qq.com', 'tom');
    
    INSERT INTO t24
    (email, `name`) VALUES('hsp@sohu.com', 'hsp');
    
    SELECT * FROM t24;
    
    -- 修改默认的自增长开始值
    ALTER TABLE t25 AUTO_INCREMENT = 100 
    CREATE TABLE t25
    (id INT PRIMARY KEY AUTO_INCREMENT, 
     email VARCHAR(32)NOT NULL DEFAULT '',
    `name` VARCHAR(32)NOT NULL DEFAULT '');
    
    INSERT INTO t25
    VALUES(NULL, 'mary@qq.com', 'mary'); 
    INSERT INTO t25
    VALUES(666, 'hsp@qq.com', 'hsp'); 
    SELECT * FROM t25;
    ```

    

### 9. 索引

- ```mysql
  -- 创建测试数据库 tmp 
  CREATE DATABASE tmp;
  
  CREATE TABLE dept( /*部门表*/
  	deptno MEDIUMINT	UNSIGNED		NOT NULL	DEFAULT 0, 
      dname VARCHAR(20)	NOT NULL	DEFAULT "",
  	loc VARCHAR(13) NOT NULL DEFAULT ""
  ) ;
  
  #创建表 EMP 雇员
  CREATE TABLE emp(
      empno	MEDIUMINT UNSIGNED	NOT NULL	DEFAULT 0, /*编号*/ 
   	ename VARCHAR(20) NOT NULL DEFAULT "", /*名字*/
  	job VARCHAR(9) NOT NULL DEFAULT "",/*工作*/
  	mgr MEDIUMINT UNSIGNED NOT NULL DEFAULT 0,/*上级编号*/
  	hiredate DATE NOT NULL,/*入职时间*/ 
      sal DECIMAL(7,2)	NOT NULL,/*薪水*/ 
      comm DECIMAL(7,2) NOT NULL,/*红利*/
  	deptno MEDIUMINT UNSIGNED NOT NULL DEFAULT 0 /*部门编号*/
  ) ;
  
  
  #工资级别表
  CREATE TABLE salgrade (
  	grade MEDIUMINT UNSIGNED NOT NULL DEFAULT 0, 
      losal DECIMAL(17,2)	NOT NULL,
  	hisal DECIMAL(17,2)	NOT NULL
  );
  
  #测试数据
  INSERT INTO salgrade VALUES (1,700,1200);
  INSERT INTO salgrade VALUES (2,1201,1400); 
  INSERT INTO salgrade VALUES (3,1401,2000); 
  INSERT INTO salgrade VALUES (4,2001,3000); 
  INSERT INTO salgrade VALUES (5,3001,9999);
  
  DELIMITER $$
  
  #创建一个函数，名字 rand_string，可以随机返回我指定的个数字符串
  CREATE FUNCTION rand_string(n INT)
  	RETURNS VARCHAR(255) #该函数会返回一个字符串
      BEGIN
  	#定义了一个变量 chars_str， 类型	varchar(100)
  	#默认给 chars_str  初始值	'abcdefghijklmnopqrstuvwxyzABCDEFJHIJKLMNOPQRSTUVWXYZ'
  	DECLARE chars_str VARCHAR(100) DEFAULT 'abcdefghijklmnopqrstuvwxyzABCDEFJHIJKLMNOPQRSTUVWXYZ';
      DECLARE return_str VARCHAR(255) DEFAULT '';
  	DECLARE i INT DEFAULT 0;
  	WHILE i < n 
  		DO
  		# concat 函数 : 连接函数 mysql 函数
  			SET return_str =CONCAT(return_str,SUBSTRING(chars_str,FLOOR(1+RAND()*52),1)); 
  			SET i = i + 1;
  	END WHILE;
  	RETURN return_str;	
  	END $$
  
  
  
  #这里我们又自定了一个函数,返回一个随机的部门号
  CREATE FUNCTION rand_num( )
      RETURNS INT(5) 
      BEGIN
      DECLARE i INT DEFAULT 0; 
      SET i = FLOOR(10+RAND()*500); 
      RETURN i;
  	END $$
  #创建一个存储过程， 可以添加雇员
  CREATE PROCEDURE insert_emp(IN START INT(10),IN max_num INT(10)) 
  	BEGIN
      DECLARE i INT DEFAULT 0;
      #set autocommit =0 把 autocommit 设置成 0 #autocommit = 0 含义:  不要自动提交 SET autocommit = 0; #默认不提交 sql 语句REPEAT
      SET i = i + 1;
      #通过前面写的函数随机产生字符串和部门编号，然后加入到 emp 表
      INSERT INTO emp VALUES ((START+i),rand_string(6),'SALESMAN',0001,CURDATE(),2000,400,rand_num());
      UNTIL i = max_num END REPEAT;
      #commit 整体提交所有 sql 语句，提高效率
      COMMIT;`
      END $$
  
  
  #添加 8000000 数据
  CALL insert_emp(100001,8000000)$$
  
  
  #命令结束符，再重新设置为; 
  DELIMITER ;
  
  SELECT COUNT(*) FROM emp;
  
  
  -- 在没有创建索引时，我们的查询一条记录
  SELECT *
  FROM emp
  WHERE empno = 1234567
  -- 使用索引来优化一下， 体验索引的牛
  
  
  -- 在没有创建索引前 , emp.ibd  文件大小 是 524m
  -- 创建索引后 emp.ibd  文件大小 是 655m [索引本身也会占用空间.]
  -- 创建 ename 列索引,emp.ibd  文件大小 是 827m
  
  
  -- empno_index 索引名称
  -- ON emp (empno) :  表示在 emp 表的 empno 列创建索引
  CREATE INDEX empno_index ON emp (empno)
  
  
  -- 创建索引后， 查询的速度如何
  
  SELECT *
  FROM emp
  WHERE empno = 1234578 -- 0.003s  原来是 4.5s
  
  
  -- 创建索引后，只对创建了索引的列有效
  SELECT *
  FROM emp
  WHERE ename = 'PjDlwy' -- 没有在 ename 创建索引时，时间 4.7s
  
  CREATE INDEX ename_index ON emp (ename) -- 在 ename 上创建索引
  ```

- 索引的原理

  ![image-20211014111247000](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014111247000.png)

- 索引的类型

  ![image-20211014111443976](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014111443976.png)

- 索引使用

  ![img](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\wps15.png)

  ```mysql
  -- 演示 mysql 的索引的使用
  -- 创建索引
  CREATE TABLE t25 (
  id INT ,
  `name` VARCHAR(32));
  
  -- 查询表是否有索引
  SHOW INDEXES FROM t25;
  
  -- 添加索引
  -- 添加唯一索引
  CREATE UNIQUE INDEX id_index ON t25 (id);
  -- 添加普通索引方式 1
  CREATE INDEX id_index ON t25 (id);
  
  -- 如何选择
  -- 1.  如果某列的值，是不会重复的，则优先考虑使用 unique 索引,  否则使用普通索引
  
  -- 添加普通索引方式 2
  ALTER TABLE t25 ADD INDEX id_index (id)
  
  
  -- 添加主键索引
  CREATE TABLE t26 (
  id INT ,
  `name` VARCHAR(32));
  
  ALTER TABLE t26 ADD PRIMARY KEY (id)
  
  SHOW INDEX FROM t25
  
  
  -- 删除索引
  DROP INDEX id_index ON t25
  -- 删除主键索引
  ALTER TABLE t26 DROP PRIMARY KEY
  
  
  -- 修改索引 ， 先删除，在添加新的索引
  
  -- 查询索引
  -- 1. 方式
  SHOW INDEX FROM t25
  -- 2. 方式
  SHOW INDEXES FROM t25
  -- 3. 方式
  SHOW KEYS FROM t25
  -- 4 方式
  DESC t25
  ```

- 小结: 哪些列上适合使用索引

  ![image-20211014113115861](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014113115861.png)

  

### 10. 事务

##### 1. 什么是事务

- ![image-20211014160230396](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014160230396.png)

- ![image-20211014160233665](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014160233665.png)

- 事务和锁

  ![image-20211014160301747](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014160301747.png)

  ```mysql
  -- 事务的一个重要的概念和具体操作
  -- 看一个图[看示意图]
  -- 演示
  -- 1. 创建一张测试表
  CREATE TABLE t27 ( 
      id INT,
  	`name` VARCHAR(32));
  -- 2. 开始事务
  START TRANSACTION
  -- 3. 设置保存点
  SAVEPOINT a
  -- 执行 dml  操作
  INSERT INTO t27 VALUES(100, 'tom'); 
  SELECT * FROM t27;
  
  SAVEPOINT b
  -- 执行 dml 操作
  INSERT INTO t27 VALUES(200, 'jack');
  
  -- 回 退 到 b 
  ROLLBACK TO b
  -- 继 续 回 退 a 
  ROLLBACK TO a
  -- 如果这样,  表示直接回退到事务开始的状态. 
  ROLLBACK
  
  COMMIT
  ```

- 回退事务

  ![image-20211014160610694](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014160610694.png)

- 提交事务

  ![image-20211014160623991](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014160623991.png)

- 细节

  ![image-20211014160708807](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014160708807.png)

  ```mysql
  -- 1.  如果不开始事务，默认情况下，dml 操作是自动提交的，不能回滚
  INSERT INTO t27 VALUES(300, 'milan'); -- 自动提交 commit
  
  
  SELECT * FROM t27
  
  
  -- 2.  如果开始一个事务，你没有创建保存点.  你可以执行 rollback，
  -- 默认就是回退到你事务开始的状态
  START TRANSACTION
  INSERT INTO t27 VALUES(400, 'king'); 
  INSERT INTO t27 VALUES(500, 'scott');
  ROLLBACK -- 表示直接回退到事务开始的的状态
  COMMIT;
  
  -- 3. 你也可以在这个事务中(还没有提交时),  创建多个保存点.比如: savepoint	aaa;
  -- 执行 dml , 
  savepoint	bbb
  
  -- 4. 你可以在事务没有提交前，选择回退到哪个保存点
  -- 5. InnoDB 存储引擎支持事务 , MyISAM  不支持
  -- 6. 开始一个事务 start	transaction,	set autocommit=off;
  ```

  

##### 2. 事务隔离级别

- 介绍

  ![image-20211014161650635](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014161650635.png)

- 查看事务隔离级别

  ![image-20211014161744564](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014161744564.png)

- 事务隔离级别

  ![image-20211014161818235](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014161818235.png)

- mysql 的事务隔离级--案例

  ![image-20211014161950238](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014161950238.png)

  ```mysql
  -- 1.  开了两个 mysql 的控制台
  -- 2.  查看当前 mysql 的隔离级别
  SELECT @@tx_isolation;
  
  -- mysql> SELECT @@tx_isolation;
  -- +-----------------+
  -- | @@tx_isolation	|
  -- +-----------------+
  -- | REPEATABLE-READ |
  -- +-----------------+
  
  
  -- 3.把其中一个控制台的隔离级别设置 Read uncommitted
  
  SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED
  
  -- 4. 创建表
  CREATE TABLE `account`( 
      id INT,
  	`name` VARCHAR(32), 
      money INT);
  
  -- 查看当前会话隔离级别
  SELECT @@tx_isolation
  -- 查看系统当前隔离级别
  SELECT @@global.tx_isolation
  -- 设置当前会话隔离级别
  SET SESSION TRANSACTION ISOLATION LEVEL READ UNCOMMITTED
  -- 设置系统当前隔离级别
  SET GLOBAL TRANSACTION ISOLATION LEVEL [你设置的级别]
  ```

- 设置事务隔离级别

  ![image-20211014162157155](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014162157155.png)

  ![image-20211014162204144](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014162204144.png)

  

##### 3. mysql 事务 ACID

- 事务的acid 特性

  ![image-20211014162430063](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014162430063.png)

  

##### 4. mysql 表类型和存储引擎

- 基本介绍

  ![image-20211014162539043](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014162539043.png)

- 主要的存储引擎/表类型特点

  ![image-20211014162600459](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014162600459.png)

- 细节

  ![image-20211014162822779](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014162822779.png)

  ```mysql
  -- 表类型和存储引擎
  
  
  -- 查看所有的存储引擎
  SHOW ENGINES
  -- innodb 存储引擎，是前面使用过.
  -- 1. 支持事务 2.  支持外键 3.  支持行级锁
  
  
  -- myisam 存储引擎
  CREATE TABLE t28 (
  id INT,
  `name` VARCHAR(32)) ENGINE MYISAM
  -- 1. 添加速度快 2.  不支持外键和事务 3.  支持表级锁
  
  START TRANSACTION; 
  SAVEPOINT t1
  INSERT INTO t28 VALUES(1, 'jack'); 
  SELECT * FROM t28;
  ROLLBACK TO t1
  
  
  -- memory  存储引擎
  -- 1.  数据存储在内存中[关闭了 Mysql 服务，数据丢失,  但是表结构还在]
  -- 2.  执行速度很快(没有 IO 读写) 
  -- 3.  默认支持索引(hash 表)
  
  
  CREATE TABLE t29 (
  id INT,
  `name` VARCHAR(32)) ENGINE MEMORY 
  DESC t29
  INSERT INTO t29
  VALUES(1,'tom'), (2,'jack'), (3, 'hsp'); 
  SELECT * FROM t29
  
  -- 指令修改存储引擎
  ALTER TABLE `t29` ENGINE = INNODB
  ```

- 如何选择表的存储引擎

  ![image-20211014163038184](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014163038184.png)

- 修改存储引擎

  ![image-20211014163109702](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014163109702.png)

  

### 11.视图

1. 基本概念

   ![image-20211014191857650](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014191857650.png)

   ![image-20211014191905604](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014191905604.png)

2. 视图的基本使用

   ![image-20211014191933621](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014191933621.png)

3. 练习

   ```mysql
   -- 视图的使用
   -- 创建一个视图 emp_view01，只能查询 emp 表的(empno、ename, job 和 deptno ) 信息
   
   
   -- 创建视图
   CREATE VIEW emp_view01 AS
   SELECT empno, ename, job, deptno FROM emp;
   
   -- 查看视图
   DESC emp_view01
   
   SELECT * FROM emp_view01;
   SELECT empno, job	FROM emp_view01;
   
   
   -- 查看创建视图的指令
   SHOW CREATE VIEW emp_view01
   -- 删除视图
   DROP VIEW emp_view01;
   
   
   
   -- 视图的细节
   
   -- 1.  创建视图后，到数据库去看，对应视图只有一个视图结构文件(形式:  视图名.frm)
   -- 2.  视图的数据变化会影响到基表，基表的数据变化也会影响到视图[insert update delete ]
   
   
   -- 修改视图 会影响到基表
   UPDATE  emp_view01 SET job = 'MANAGER'
   WHERE empno = 7369
   
   SELECT * FROM emp; -- 查询基表
   
   SELECT * FROM emp_view01
   
   
   -- 修改基本表， 会影响到视图
   UPDATE emp
   SET job = 'SALESMAN'
   WHERE empno = 7369
   
   
   -- 3.  视图中可以再使用视图 ,  比如从 emp_view01 视图中，选出 empno,和 ename 做出新视图
   DESC emp_view01
   
   CREATE VIEW emp_view02 AS
   SELECT empno, ename FROM emp_view01
   
   SELECT * FROM emp_view02
   ```

4. 细节

   ![image-20211014192342478](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014192342478.png)

5. 视图最佳实践

   ![image-20211014192413945](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014192413945.png)

   

### 12. MySQL管理

- Mysql 用户

  ![image-20211014192544638](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014192544638.png)

  - ![image-20211014192719662](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014192719662.png)

- mysql 中的权限

  ![image-20211014192749861](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014192749861.png)

- 给用户授权

  ![image-20211014192926715](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014192926715.png)

- ![image-20211014193055312](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014193055312.png)

- 练习

  ```mysql
  -- 演示 用户权限的管理
  
  -- 创建用户 shunping	密码 123 , 从本地登录
  CREATE USER 'shunping'@'localhost' IDENTIFIED BY '123'
  
  
  -- 使用 root 用户创建 testdb	, 表 news
  CREATE DATABASE testdb
  CREATE TABLE news (
  id INT ,
  content VARCHAR(32));
  -- 添加一条测试数据
  INSERT INTO news VALUES(100, '北京新闻');
  SELECT * FROM news;
  
  
  -- 给 shunping  分配查看 news 表和 添加 news 的权限
  GRANT SELECT , INSERT
  ON testdb.news
  TO 'shunping'@'localhost'
  
  
  -- 可以增加 update 权限
  GRANT UPDATE
  ON testdb.news
  TO 'shunping'@'localhost'
  
  
  -- 修改 shunping 的密码为 abc
  SET PASSWORD FOR 'shunping'@'localhost' = PASSWORD('abc');
  
  
  -- 回收 shunping  用户在 testdb.news  表的所有权限
  REVOKE SELECT , UPDATE, INSERT ON testdb.news FROM 'shunping'@'localhost'
  REVOKE ALL ON testdb.news FROM 'shunping'@'localhost'
  
  -- 删除 shunping
  DROP USER 'shunping'@'localhost'
  ```

- 细节

  ![image-20211014193409405](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211014193409405.png)

  ```mysql
  -- 说明 用户管理的细节
  -- 在创建用户的时候，如果不指定 Host,  则为% , %表示表示所有 IP 都有连接权限
  -- create user	xxx;
  CREATE USER jack
  
  SELECT `host`, `user` FROM mysql.user
  
  
  -- 你也可以这样指定
  -- create user	'xxx'@'192.168.1.%'	表示 xxx 用户在 192.168.1.*的 ip 可以登录 mysql
  
  
  CREATE USER 'smith'@'192.168.1.%'
  
  
  -- 在删除用户的时候，如果 host  不是 %,  需要明确指定	'用户'@'host 值'
  DROP USER jack -- 默认就是 DROP USER 'jack'@'%'
  DROP USER 'smith'@'192.168.1.%'
  ```

  

## 第二十二章  JDBC 和数据库连接池

### 1. JDBC概述

#### 1. JDBC原理

- 基本介绍

  ![image-20211015193224916](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211015193224916.png)

  ![image-20211015193340126](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211015193340126-16342976217411.png)

- 模拟JDBC

```mysql
public interface JdbcInterface {
    //连接
    public Object getConnection() ;
    //crud
    public void crud();
    //关闭连接
    public void close();
}
===========
package com.hspedu.jdbc.myjdbc;

/**
*@author 韩顺平
*@version 1.0
*mysql 数据库实现了 jdbc 接口 [模拟] 【mysql 厂商开发】
*/
public class MysqlJdbcImpl implements	JdbcInterface{ @Override
    public Object getConnection() {
        System.out.println("得到 mysql 的连接"); return null;
        }


        @Override
        public void crud() {
        System.out.println("完成 mysql  增删改查");
        }


        @Override
        public void close() {
        System.out.println("关闭 mysql  的连接");
    }
}
=======================
package com.hspedu.jdbc.myjdbc;


/**
*@author 韩顺平
*@version 1.0
*模拟 oracle 数据库实现 jdbc
*/
public class OracleJdbcImpl implements	JdbcInterface { @Override
    public Object getConnection() {
        System.out.println("得到 oracle 的连接 升级"); return null;
        }


        @Override
        public void crud() {
        System.out.println("完成 对 oracle 的增删改查");
        }


        @Override
        public    void     close()     { System.out.println("关闭 oracle 的连接");
    }
}
========================
package com.hspedu.jdbc.myjdbc;


import org.junit.jupiter.api.Test;


import java.io.FileInputStream; 
import java.sql.Connection;
import java.sql.DriverManager; 
import java.sql.ResultSet; 
import java.sql.Statement; 
import java.util.Properties; 
import java.util.Scanner;

/**
* @author 韩顺平
* @version 1.0
*/
public class TestJDBC {
    public static void main(String[] args) throws Exception {
        //完成对 mysql 的操作
        JdbcInterface jdbcInterface = new MysqlJdbcImpl(); 
        jdbcInterface.getConnection(); //通过接口来调用实现类[动态绑定] 
        jdbcInterface.crud();
        jdbcInterface.close();

        //完成对 oracle 的操作
        System.out.println("==============================");
        jdbcInterface = new OracleJdbcImpl(); 
        jdbcInterface.getConnection(); //通过接口来调用实现类[动态绑定] 
        jdbcInterface.crud();
        jdbcInterface.close();
    }
}
```

#### 2. JDBC带来的好处

- ![image-20211015213051909](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211015213051909.png)

  ![image-20211015213102491](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211015213102491.png)



#### 3. JDBC快速入门

- JDBC 程序编写步骤

  ![image-20211015213604073](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211015213604073.png)

- JDBC 第一个程序

  ```java
  package com.hspedu.jdbc;
  
  import com.mysql.jdbc.Driver;
  
  import java.sql.Connection; 
  import java.sql.SQLException; 
  import java.sql.Statement; 
  import java.util.Properties;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *这是第一个 Jdbc 程序，完成简单的操作
  */
  public class Jdbc01 {
      public static void main(String[] args) throws SQLException {
          //前置工作： 在项目下创建一个文件夹比如 libs
          // 将 mysql.jar 拷贝到该目录下，点击 add to project ..加入到项目中
          //1. 注册驱动
          Driver driver = new Driver(); //创建 driver 对象
  
          //2. 得到连接
          // 老师解读
          //(1) jdbc:mysql:// 规定好表示协议，通过 jdbc 的方式连接 mysql
          //(2) localhost  主机，可以是 ip 地址
          //(3) 3306  表示 mysql 监听的端口
          //(4) hsp_db02  连接到 mysql dbms  的哪个数据库
          //(5) mysql 的连接本质就是前面学过的 socket 连接
          String url = "jdbc:mysql://localhost:3306/hsp_db02";
          //将 用户名和密码放入到 Properties 对象
          Properties properties = new Properties();
          //说明 user  和 password 是规定好，后面的值根据实际情况写
          properties.setProperty("user", "root");//  用户
          properties.setProperty("password", "hsp"); //密码
          Connection connect = driver.connect(url, properties);
  
          //3. 执行 sql
          //String sql = "insert into actor values(null, '刘德华', '男', '1970-11-11', '110')";
          //String sql = "update actor set name='周星驰' where id = 1"; 
          String sql = "delete from actor where id = 1";
          //statement 用于执行静态 SQL 语句并返回其生成的结果的对象
          Statement statement = connect.createStatement();
          int rows = statement.executeUpdate(sql); // 如果是 dml 语句，返回的就是影响行数
          System.out.println(rows > 0 ? "成功" : "失败");
  
          //4. 关闭连接资源
          statement.close(); 
          connect.close();
      }
  }
  ```



#### 4. 获取数据库连接 5 种方式

- 方式 4

  ![image-20211015214927686](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211015214927686.png)

- 方式 5

  ![image-20211015214934805](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211015214934805.png)

```java
package com.hspedu.jdbc;

import com.mysql.jdbc.Driver; 
import org.junit.jupiter.api.Test;
import java.io.FileInputStream;
import java.io.FileNotFoundException; 
import java.io.IOException;
import java.sql.Connection; 
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.Properties;

/**
*@author 韩顺平
*@version 1.0
*分析 java 连接 mysql 的 5 中方式
*/
public class JdbcConn {

    //方式 1 
    @Test
    public void connect01() throws SQLException {
        Driver driver = new Driver(); //创建 driver 对象
        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        //将 用户名和密码放入到 Properties 对象
        Properties properties = new Properties();
        //说明 user  和 password 是规定好，后面的值根据实际情况写
        properties.setProperty("user", "root");//  用户
        properties.setProperty("password", "hsp"); //密码
        Connection connect = driver.connect(url, properties); 
        System.out.println(connect);
    }


    //方式 2
    @Test
    public	void	connect02()	throws	ClassNotFoundException,	IllegalAccessException,	InstantiationException, SQLException {
        //使用反射加载 Driver 类 ,  动态加载，更加的灵活，减少依赖性
        Class<?> aClass = Class.forName("com.mysql.jdbc.Driver");
        Driver driver = (Driver)aClass.newInstance();

        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        //将 用户名和密码放入到 Properties 对象
        Properties properties = new Properties();
        //说明 user  和 password 是规定好，后面的值根据实际情况写
        properties.setProperty("user", "root");//  用户
        properties.setProperty("password", "hsp"); //密码

        Connection connect = driver.connect(url, properties);
        System.out.println("方式 2=" + connect)

    }


    //方式 3  使用 DriverManager 替代 driver 进行统一管理
    @Test
    public	void	connect03()	throws	IllegalAccessException,	InstantiationException,	ClassNotFoundException, SQLException {

        //使用反射加载 Driver
        Class<?> aClass = Class.forName("com.mysql.jdbc.Driver");
        Driver driver = (Driver) aClass.newInstance();

        //创建 url  和 user 和 password
        String url = "jdbc:mysql://localhost:3306/hsp_db02"; 
        String user = "root";
        String password = "hsp";
        DriverManager.registerDriver(driver);//注册 Driver 驱动

        Connection connection = DriverManager.getConnection(url, user, password);
        System.out.println("第三种方式=" + connection);
    }


    //方式 4:  使用 Class.forName 自动完成注册驱动，简化代码
    //这种方式获取连接是使用的最多，推荐使用
    @Test
    public void connect04() throws ClassNotFoundException, SQLException {
        //使用反射加载了 Driver 类
        //在加载 Driver 类时，完成注册
        /*
        源码: 1. 静态代码块，在类加载时，会执行一次.
        	2.DriverManager.registerDriver(new Driver());
        	3.因此注册 driver 的工作已经完成
        static {
            try {
            	DriverManager.registerDriver(new Driver());
            } catch (SQLException var1) {
            	throw new RuntimeException("Can't register driver!");
            }
        }
        */
        Class.forName("com.mysql.jdbc.Driver");

        //创建 url  和 user 和 password
        String url = "jdbc:mysql://localhost:3306/hsp_db02";
        String user = "root";
        String password = "hsp";
        Connection connection = DriverManager.getConnection(url, user, password);
        System.out.println("第 4 种方式~ " + connection);

    }


    //方式 5 ,  在方式 4 的基础上改进，增加配置文件，让连接 mysql 更加灵活
    @Test
    public void connect05() throws IOException, ClassNotFoundException, SQLException {

        //通过 Properties 对象获取配置文件的信息
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //获取相关的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password");
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");

        Class.forName(driver);//建议写上

        Connection connection = DriverManager.getConnection(url, user, password);

        System.out.println("方式 5 " + connection);
    }
}
```



####  5. ResultSet（结果集）

- 基本介绍

  ![image-20211016141630098](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016141630098.png)

- 应用实例

  ![image-20211016141915442](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016141915442.png)

  ```java
  package com.hspedu.jdbc.resultset_;
  
  import java.io.FileInputStream;
  import java.io.FileNotFoundException;
  import java.io.IOException; 
  import java.sql.*;
  import java.util.Properties;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 select  语句返回 ResultSet ,并取出结果
  */ @SuppressWarnings({"all"}) 
  public class ResultSet_ {
      public static void main(String[] args) throws Exception {
  
          //通过 Properties 对象获取配置文件的信息
          Properties properties = new Properties();
          properties.load(new FileInputStream("src\\mysql.properties"));
          //获取相关的值
          String user = properties.getProperty("user");
          String password = properties.getProperty("password"); 
          String driver = properties.getProperty("driver");
          String url = properties.getProperty("url");
  
  
          //1. 注册驱动
          Class.forName(driver);//建议写上
  
          //2. 得到连接
          Connection connection = DriverManager.getConnection(url, user, password);
  
          //3. 得到 Statement
          Statement statement = connection.createStatement();
          
          //4. 组织 SqL
          String sql = "select id, name , sex, borndate from actor";
          //执行给定的 SQL 语句，该语句返回单个 ResultSet 对象（实现了ResultSet接口的类的对象）
          /*
          +----+-----------+-----+---------------------+
          | id | name	| sex | borndate	|
          +----+-----------+-----+---------------------+-------+
          |	4 | 刘德华	| 男	| 1970-12-12 00:00:00 |
          |	5 | jack	| 男	| 1990-11-11 00:00:00 |
          +----+-----------+-----+---------------------+-------+
          */
          /*
          老韩阅读 debug  代码 resultSet  对象的结构
  
          */
          ResultSet resultSet = statement.executeQuery(sql);
  
          //5. 使用 while 取出数据
          while (resultSet.next()) { //  让光标向后移动，如果没有更多行，则返回 false
              int id	= resultSet.getInt(1); //获取该行的第 1 列
          	//int id1 = resultSet.getInt("id"); 通过列名来获取值, 推荐
              String name = resultSet.getString(2);//获取该行的第 2 列
              String sex = resultSet.getString(3);
              Date date = resultSet.getDate(4);
          	System.out.println(id + "\t" + name + "\t" + sex + "\t" + date);
          }
          //6. 关闭连接
          resultSet.close(); 
          statement.close(); 
          connection.close();
      }
  }
  ```

  

#### 6. Statement

##### 1. 基本介绍

![image-20211016144436094](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016144436094.png)

##### 2. 演示statement  的SQL注入问题

```mysql
-- 演示 sql  注入
-- 创建一张表
CREATE TABLE admin ( -- 管理员表
NAME VARCHAR(32) NOT NULL UNIQUE,
pwd VARCHAR(32) NOT NULL DEFAULT '') 
CHARACTER SET utf8;


-- 添加数据
INSERT INTO admin VALUES('tom', '123');


-- 查找某个管理是否存在


SELECT *
FROM admin
WHERE NAME = 'tom' AND pwd = '123'
-- SQL
-- 输入用户名 为	1' or
-- 输入万能密码 为 or '1'= '1 
SELECT *
FROM admin
WHERE NAME = '1' OR' AND pwd = 'OR '1'= '1'
SELECT * FROM admin    
```

```java
package com.hspedu.jdbc.statement_;


import java.io.FileInputStream;
import java.io.FileNotFoundException; 
import java.sql.*;
import java.util.Properties;
import java.util.Scanner;

/**
*@author 韩顺平
*@version 1.0
*演示 statement  的注入问题
*/ @SuppressWarnings({"all"})
public class Statement_ {
    public static void main(String[] args) throws Exception {
        Scanner scanner = new Scanner(System.in);

        //让用户输入管理员名和密码
        System.out.print("请输入管理员的名字: ");	//next():  当接收到 空格或者 '就是表示结束
        String admin_name = scanner.nextLine(); // 老师说明，如果希望看到 SQL 注入，这里需要用 nextLine
        System.out.print("请输入管理员的密码: "); 
        String admin_pwd = scanner.nextLine();

        //通过 Properties 对象获取配置文件的信息
        Properties properties = new Properties();
        properties.load(new FileInputStream("src\\mysql.properties"));
        //获取相关的值
        String user = properties.getProperty("user");
        String password = properties.getProperty("password"); 
        String driver = properties.getProperty("driver");
        String url = properties.getProperty("url");


        //1. 注册驱动
        Class.forName(driver);//建议写上


        //2. 得到连接
        Connection connection = DriverManager.getConnection(url, user, password);

        //3. 得到 Statement
        Statement statement = connection.createStatement();
        //4. 组织 SqL
        String sql = "select name , pwd	from admin where name ='"
        + admin_name + "' and pwd = '" + admin_pwd + "'"; 
        ResultSet resultSet = statement.executeQuery(sql);
        if (resultSet.next()) { //如果查询到一条记录，则说明该管理存在
        	System.out.println("恭喜， 登录成功");
        } else {
        	System.out.println("对不起，登录失败");
        }

        //关闭连接
        resultSet.close(); 
        statement.close();
        connection.close();
    }
}
```



##### 3. PreparedStatement

- 基本介绍

  ![image-20211016152129798](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016152129798.png)

- 预处理的好处

  ![image-20211016152219703](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016152219703.png)

  (3. preparedstatement会预编译，mysql就不需要再编译！)

- 应用案例

  ```java
  package com.hspedu.jdbc.preparedstatement_;
  
  import java.io.FileInputStream;
  import java.io.FileNotFoundException;
  import java.sql.*;
  import java.util.Properties;
  import java.util.Scanner;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 PreparedStatement 使用
  */ @SuppressWarnings({"all"})
  public class PreparedStatement_ {
      public static void main(String[] args) throws Exception {
  
          //看 PreparedStatement 类图
  
          Scanner scanner = new Scanner(System.in);
  
  
          //让用户输入管理员名和密码
          System.out.print("请输入管理员的名字: ");	//next():  当接收到 空格或者 '就是表示结束
          String admin_name = scanner.nextLine(); // 老师说明，如果希望看到 SQL 注入，这里需要用 nextLine
          System.out.print("请输入管理员的密码: "); 
          String admin_pwd = scanner.nextLine();
  
          //通过 Properties 对象获取配置文件的信息
          Properties properties = new Properties();
          properties.load(new FileInputStream("src\\mysql.properties"));
          //获取相关的值
          String user = properties.getProperty("user");
          String password = properties.getProperty("password"); 
          String driver = properties.getProperty("driver");
          String url = properties.getProperty("url");
  
  
          //1. 注册驱动
          Class.forName(driver);//建议写上
  
  
          //2. 得到连接
          Connection connection = DriverManager.getConnection(url, user, password);
  
  
          //3. 得到 PreparedStatement
          //3.1 组织 SqL , Sql 语句的 ? 就相当于占位符
          //添加记录
  		//String sql = "insert into admin values(?, ?)";
  		//String sql = "update admin set pwd = ? where name = ?"; 
          //String sql = "delete from	admin where name = ?";
          
          String sql = "select name , pwd	from admin where name =? and pwd = ?";
          //3.2 preparedStatement 对象实现了 PreparedStatement 接口的实现类的对象
          PreparedStatement preparedStatement = connection.prepareStatement(sql);
          //3.3 给 ? 赋值
          preparedStatement.setString(1, admin_name); 
          preparedStatement.setString(2, admin_pwd);
  
          //4. 执行 select  语句使用	executeQuery
          //	如果执行的是 dml(update, insert ,delete) executeUpdate()
          // int rows = preparedStatement.executeUpdate(); 
          //	这里执行 executeQuery ,不要在写 sql 
          ResultSet resultSet = preparedStatement.executeQuery();
          if (resultSet.next()) { //如果查询到一条记录，则说明该管理存在
          	System.out.println("恭喜， 登录成功");
          } else {
          	System.out.println("对不起，登录失败");
          }
          //关闭连接
          resultSet.close(); 
          preparedStatement.close(); 
          connection.close();
      }
  }
  ```

  

### 2. JDBC API (应用程序接口)	

![image-20211016160758856](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016160758856.png)

![image-20211016160804862](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016160804862.png)



### 3. JDBCUtils

- 说明

  ![image-20211016162836752](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016162836752.png)

- 代码实现

  ```java
  package com.hspedu.jdbc.utils;
  
  
  import java.io.FileInputStream; 
  import java.io.IOException; 
  import java.sql.*;
  import java.util.Properties;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *这是一个工具类，完成 mysql 的连接和关闭资源
  */
  public class JDBCUtils {
      //定义相关的属性(4 个), 因为只需要一份，因此，我们做出 
      static private static String user; //用户名
      private static String password; //密码
      private static String url; //url
      private static String driver; //驱动名
  
  
      //在 static 代码块去初始化
      static {
  
          try {
              Properties properties = new Properties();
              properties.load(new FileInputStream("src\\mysql.properties"));
              //读取相关的属性值
              user = properties.getProperty("user");
              password = properties.getProperty("password"); 
              url = properties.getProperty("url");
              driver = properties.getProperty("driver");
          } catch (IOException e) {
              //在实际开发中，我们可以这样处理
              //1. 将编译异常转成 运行异常
              //2. 调用者，可以选择捕获该异常，也可以选择默认处理该异常，比较方便. 
              throw new RuntimeException(e);
  
      }
  }
  
  
      //连接数据库, 返回 Connection
      public static Connection getConnection() {
          try {
          	return DriverManager.getConnection(url, user, password);
          } catch (SQLException e) {
              //1. 将编译异常转成 运行异常
              //2. 调用者，可以选择捕获该异常，也可以选择默认处理该异常，比较方便. 
              throw new RuntimeException(e);
          }
      }
  
  
      //关闭相关资源
      /*
      1.ResultSet 结果集
      2.Statement 或者 PreparedStatement
      3.Connection
      4.如果需要关闭资源，就传入对象，否则传入 null
      */
      public static void close(ResultSet set, Statement statement, Connection connection) {
  
  
          //判断是否为 null try {
          if (set != null) {    
              set.close();
          }
          if (statement != null) { 
              statement.close();
          }
          if (connection != null) {
              connection.close();
          }
          } catch (SQLException e) {
              //将编译异常转成运行异常抛出
              throw new RuntimeException(e);
          }
  	}
  
  }
  =================================================
  package com.hspedu.jdbc.utils;
  
  
  import org.junit.jupiter.api.Test;
  
  
  import java.sql.*;
  
  
  /**
  *@author 韩顺平
  *@version 1.0
  * 该类演示如何使用 JDBCUtils 工具类，完成 dml 和 select
  */
  public class JDBCUtils_Use {
  
  
  
      @Test
      public void testSelect() {
          //1. 得到连接
          Connection connection = null;
          //2. 组织一个 sql
          String sql = "select * from actor where id = ?"; 
          PreparedStatement preparedStatement = null; 
          ResultSet set = null;
          //3. 创建 PreparedStatement 对象
          try {
          	connection = JDBCUtils.getConnection();
              System.out.println(connection.getClass()); //com.mysql.jdbc.JDBC4Connection 
              preparedStatement = connection.prepareStatement(sql); 
              preparedStatement.setInt(1, 5);//给?号赋值
              //执行, 得到结果集
              set = preparedStatement.executeQuery();
          //遍历该结果集
              while (set.next()) {
                  int id = set.getInt("id");
                  String name = set.getString("name"); 
                  String sex = set.getString("sex");
                  Date borndate = set.getDate("borndate"); 
                  String phone = set.getString("phone");
                  System.out.println(id + "\t" + name + "\t" + sex + "\t" + borndate + "\t" + phone);
          	}
          } catch (SQLException e) {
              e.printStackTrace();
          } finally {
              //关闭资源
              JDBCUtils.close(set, preparedStatement, connection);
          }
      }
  
  
      @Test
      public void testDML() {//insert , update, delete
  
  
          //1. 得到连接
          Connection connection = null;
          //2. 组织一个 sql
          String sql = "update actor set name = ? where id = ?";
          // 测 试 delete 和 insert , 自 己 玩 .
          PreparedStatement preparedStatement = null;
          //3. 创建 PreparedStatement 对象
          try {
              connection = JDBCUtils.getConnection();
              preparedStatement = connection.prepareStatement(sql);
              //给占位符赋值
              preparedStatement.setString(1, "周星驰");
              preparedStatement.setInt(2, 4);
              //执行
              preparedStatement.executeUpdate();
          } catch (SQLException e) { 
              e.printStackTrace();
          } finally {
              //关闭资源
              JDBCUtils.close(null, preparedStatement, connection);
          }
      }
  }
  ```

  

### 4. 事务

- 基本介绍（默认情况下Connection对象创建时自动提交事务！）

  ![image-20211016174805641](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016174805641.png)

- 案例（模拟经典的转账业务）

  - 不使用事务可能出现的问题模拟-模拟经典的转账业务
  - 使用事务解决上述问题-模拟经典的转账业务

  ```java
  package com.hspedu.jdbc.transaction_;
  
  
  import com.hspedu.jdbc.utils.JDBCUtils; 
  import org.junit.jupiter.api.Test;
  import java.sql.Connection;
  import java.sql.PreparedStatement; 
  import java.sql.SQLException;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 jdbc 中如何使用事务
  */
  public class Transaction_ {
      //没有使用事务.
      @Test
      public void noTransaction() {
  
          //操作转账的业务
          //1. 得到连接
          Connection connection = null;
          //2. 组织一个 sql
          String sql = "update account set balance = balance - 100 where id = 1"; 
          String sql2 = "update account set balance = balance + 100 where id = 2"; 
          PreparedStatement preparedStatement = null;
          //3. 创建 PreparedStatement 对象
          try {
          	connection = JDBCUtils.getConnection(); // 在默认情况下，connection 是默认自动提交
              preparedStatement = connection.prepareStatement(sql);
              preparedStatement.executeUpdate(); // 执行第 1 条 sql
  
              int i = 1 / 0; //抛出异常
              preparedStatement = connection.prepareStatement(sql2);
              preparedStatement.executeUpdate(); // 执行第 2 条 sql
  
          } catch (SQLException e) { 
              e.printStackTrace();
          } finally {
          	//关闭资源
              JDBCUtils.close(null, preparedStatement, connection);
      }
  }
  
  
      //事务来解决
      @Test
      public void useTransaction() {
  
          //操作转账的业务
          //1. 得到连接
          Connection connection = null;
          //2. 组织一个 sql
          String sql = "update account set balance = balance - 100 where id = 1"; 
          String sql2 = "update account set balance = balance + 100 where id = 2"; 
          PreparedStatement preparedStatement = null;
          //3. 创建 PreparedStatement 对象
          try {
          	connection = JDBCUtils.getConnection(); //  在默认情况下，connection 是默认自动提交
          	//将 connection  设置为不自动提交
              connection.setAutoCommit(false); //开启了事务
              preparedStatement = connection.prepareStatement(sql); 
              preparedStatement.executeUpdate(); // 执行第 1 条 sql
  
              int i = 1 / 0; //抛出异常
              preparedStatement = connection.prepareStatement(sql2);
              preparedStatement.executeUpdate(); // 执行第 2 条 sql
  
          	//这里提交事务
              connection.commit();
  
          } catch (SQLException e) {
              //这里我们可以进行回滚，即撤销执行的 SQL
              //默认回滚到事务开始的状态.
              System.out.println("执行发生了异常，撤销执行的 sql"); 
              try {
              	connection.rollback();
          	} catch (SQLException throwables) { 
                  throwables.printStackTrace();
          }
          	e.printStackTrace();
          } finally {
              //关闭资源
              JDBCUtils.close(null, preparedStatement, connection);
          }
      }
  }
  ```
  
  

### 5. 批处理

- 基本介绍

  ![image-20211016203144657](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016203144657-16343875055631.png)

- 案例

  <img src="E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016203341991.png" alt="image-20211016203341991" style="zoom:150%;" />

  ```java
  package com.hspedu.jdbc.batch_;
  
  
  import com.hspedu.jdbc.utils.JDBCUtils; 
  import org.junit.jupiter.api.Test;
  import java.sql.Connection;
  import java.sql.PreparedStatement;
  import java.sql.SQLException;
  
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 java 的批处理
  */
  public class Batch_ {
  
  
      //传统方法，添加 5000 条数据到 admin2
      @Test
      public void noBatch() throws Exception {
  
          Connection connection = JDBCUtils.getConnection(); 
          String sql = "insert into admin2 values(null, ?, ?)";
          PreparedStatement preparedStatement = connection.prepareStatement(sql);
          System.out.println("开始执行");
          long start = System.currentTimeMillis();//开始时间
          for (int i = 0; i < 5000; i++) {//5000 执行
          	preparedStatement.setString(1, "jack" + i); 
              preparedStatement.setString(2, "666");
              preparedStatement.executeUpdate();
          }
          long end = System.currentTimeMillis();
          System.out.println("传统的方式 耗时=" + (end - start));//传统的方式 耗时=10702
          //关闭连接
          JDBCUtils.close(null, preparedStatement, connection);
      }
  
  
      //使用批量方式添加数据
      @Test
      public void batch() throws Exception {
  
          Connection connection = JDBCUtils.getConnection();
          String sql = "insert into admin2 values(null, ?, ?)";
          PreparedStatement preparedStatement = connection.prepareStatement(sql);
          System.out.println("开始执行");
          long start = System.currentTimeMillis();//开始时间
          for (int i = 0; i < 5000; i++) {//5000 执行
          	preparedStatement.setString(1, "jack" + i); 
              preparedStatement.setString(2, "666");
              
              //将 sql  语句加入到批处理包中 -> 看源码
              /*
              //1. //第一就创建 ArrayList - elementData => Object[]
              //2. elementData => Object[] 就会存放我们预处理的 sql 语句
              //3. 当 elementData 满后,就按照 1.5 扩容
              //4. 当添加到指定的值后，就 executeBatch
              //5. 批量处理会减少我们发送 sql 语句的网络开销，而且减少编译次数，因此效率提高
              public void addBatch() throws SQLException { 				
                  synchronized(this.checkClosed().getConnectionMutex()) {
                      if (this.batchedArgs == null) { 
                      	this.batchedArgs = new ArrayList();
                      }
  
                      for(int i = 0; i < this.parameterValues.length; ++i) { 
                      	this.checkAllParametersSet(this.parameterValues[i], this.parameterStreams[i], i);
                      }
  
                      this.batchedArgs.add(new PreparedStatement.BatchParams(this.parameterValues, this.parameterStreams, this.isStream, this.streamLengths, this.isNull));
                  }
              }
              */ 
              preparedStatement.addBatch();
              //当ArrayList有 1000 条记录时，在批量执行
              if((i + 1) % 1000 == 0) {//满 1000 条 sql 
                  preparedStatement.executeBatch();
              	//清空一把
                  preparedStatement.clearBatch();
              }
          }
          long end = System.currentTimeMillis();
          System.out.println("批量方式 耗时=" + (end - start));//批量方式 耗时=108
          //关闭连接
          JDBCUtils.close(null, preparedStatement, connection);
      }
  }
  ```

  



### 6. 连接池

- 5k 次连接数据库问题

  ![image-20211016204245464](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016204245464.png)

  ```java
  package com.hspedu.jdbc.datasource;
  
  
  import com.hspedu.jdbc.utils.JDBCUtils; 
  import org.junit.jupiter.api.Test;
  import java.sql.Connection;
  
  
  /**
  *@author 韩顺平
  *@version 1.0
  */
  public class ConQuestion {
  
      //代码 连接 mysql 5000 次
      @Test
      public void testCon() {
  
          //看看连接-关闭 connection  会耗用多久
          long start = System.currentTimeMillis();
          System.out.println("开始连接	");
          for (int i = 0; i < 5000; i++) {
              //使用传统的 jdbc 方式，得到连接
              Connection connection = JDBCUtils.getConnection();
              //做一些工作，比如得到 PreparedStatement ，发送 sql
              //..........
              //关闭
              JDBCUtils.close(null, null, connection);
          }
          long end = System.currentTimeMillis();
          System.out.println("传统方式 5000 次 耗时=" + (end - start));//传统方式 5000 次 耗时=7099
      }
  }    
  ```

- 传统获取Connection 问题分析

  ![image-20211016204435171](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016204435171.png)

- 数据库连接池种类

  ![image-20211016204527905](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016204527905.png)

  ![image-20211016213251175](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016213251175.png)

- C3P0 应用实例

  ```java
  import com.mchange.v2.c3p0.ComboPooledDataSource; 
  import org.junit.jupiter.api.Test;
  import java.io.FileInputStream;
  import java.sql.Connection; 
  import java.sql.SQLException;
  import java.util.Properties;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 c3p0 的使用
  */
  public class C3P0_ {
  
      //方式 1： 相关参数，在程序中指定 user, url , password 等
      @Test
      public void testC3P0_01() throws Exception {
  
          //1. 创建一个数据源对象
          ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource();
          //2. 通过配置文件 mysql.properties  获取相关连接的信息
          Properties properties = new Properties();
          properties.load(new FileInputStream("src\\mysql.properties"));
          //读取相关的属性值
          String user = properties.getProperty("user");
          String password = properties.getProperty("password");
          String url = properties.getProperty("url");
          String driver = properties.getProperty("driver");
  
          //给数据源 comboPooledDataSource 设置相关的参数
          //注意：连接管理是由 comboPooledDataSource 来管理
          comboPooledDataSource.setDriverClass(driver); 
          comboPooledDataSource.setJdbcUrl(url);
          comboPooledDataSource.setUser(user); 
          comboPooledDataSource.setPassword(password);
  
          //设置初始化连接数
          comboPooledDataSource.setInitialPoolSize(10);
          //最大连接数
          comboPooledDataSource.setMaxPoolSize(50);
          //测试连接池的效率, 测试对 mysql 5000 次操作
          long start = System.currentTimeMillis(); 
          for (int i = 0; i < 5000; i++) {
          	Connection connection = comboPooledDataSource.getConnection(); //这个方法就是从 DataSource 接口实现的
          	//System.out.println("连接 OK"); 
              connection.close();
          }
          long end = System.currentTimeMillis();
          //c3p0 5000 连接 mysql 耗时=391
          System.out.println("c3p0 5000 连接 mysql  耗时=" + (end - start));
      }
  
  
      //第二种方式 使用配置文件模板来完成
  
      //1. 将 c3p0  提供的 c3p0.config.xml  拷贝到 src 目录下
      //2. 该文件指定了连接数据库和连接池的相关参数
      @Test
      public void testC3P0_02() throws SQLException {
  
          ComboPooledDataSource comboPooledDataSource = new ComboPooledDataSource("hsp_edu");
  
          //测试 5000 次连接 mysql
          long start = System.currentTimeMillis();
          System.out.println("开始执行	");
          for (int i = 0; i < 500000; i++) {
          	Connection connection = comboPooledDataSource.getConnection();
          	//System.out.println("连接 OK~"); 
              connection.close();
          }
          long end = System.currentTimeMillis();
          //c3p0 的第二种方式 耗时=413
          System.out.println("c3p0 的第二种方式(500000) 耗时=" + (end - start));//1917
      }
  }    
  ```

- Druid(德鲁伊)应用实例

  ```java
  package com.hspedu.jdbc.datasource;
  
  import com.alibaba.druid.pool.DruidDataSourceFactory; import org.junit.jupiter.api.Test;
  import javax.sql.DataSource; 
  import java.io.FileInputStream;
  import java.io.FileNotFoundException;
  import java.io.IOException;
  import java.sql.Connection; 
  import java.util.Properties;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *测试 druid 的使用
  */
  public class Druid_ {
  
      @Test
      public void testDruid() throws Exception {
          //1. 加入 Druid jar 包
          //2. 加入 配置文件 druid.properties ,  将该文件拷贝项目的 src 目录
          //3. 创建 Properties 对象,  读取配置文件
          Properties properties = new Properties();
          properties.load(new FileInputStream("src\\druid.properties"));
  
          //4. 创建一个指定参数的数据库连接池, Druid 连接池
          DataSource dataSource = DruidDataSourceFactory.createDataSource(properties);
  
  
          long start = System.currentTimeMillis(); 
          for (int i = 0; i < 500000; i++) {
          	Connection connection = dataSource.getConnection(); 		
              System.out.println(connection.getClass());
          	connection.close();
          }
          long end = System.currentTimeMillis();
          //druid 连接池 操作 5000  耗时=412
          System.out.println("druid 连接池 操作 500000 耗时=" + (end - start));//539
      }
  }    
  ```

- 将JDBCUtils 工具类改成Druid(德鲁伊)实现

  ```java
  package com.hspedu.jdbc.datasource;
  
  import com.alibaba.druid.pool.DruidDataSourceFactory;
  import javax.sql.DataSource; 
  import java.io.FileInputStream;
  import java.io.IOException; 
  import java.sql.Connection; 
  import java.sql.ResultSet; 
  import java.sql.SQLException;
  import java.sql.Statement;
  import java.util.Properties;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *基于 druid 数据库连接池的工具类
  */
  public class JDBCUtilsByDruid {
     
      private static DataSource ds;
  
  
      //在静态代码块完成 ds 初始化
      static {
          Properties properties = new Properties(); 
          try {
          	properties.load(new FileInputStream("src\\druid.properties")); 
              ds = DruidDataSourceFactory.createDataSource(properties);
          } catch (Exception e) { 
              e.printStackTrace();
          }
  
      }
  
  
      //编写 getConnection 方法
      public static Connection getConnection() throws SQLException { 
          return ds.getConnection();
      }
  
  
      //关闭连接, 老师再次强调： 在数据库连接池技术中，close 不是真的断掉连接
      //而是把使用的 Connection 对象放回连接池
      public static void close(ResultSet resultSet, Statement statement, Connection connection) {
  
          try {
          if (resultSet != null) {
             resultSet.close();
          }
          if (statement != null) { 
              statement.close();
          }
          if (connection != null) { 
              connection.close();
          }
          } catch (SQLException e) {
          	throw new RuntimeException(e);
          }
  	}
  } 
  ```

  

### 7. Apache-DBUtils

- 先分析一个问题

  ![image-20211016223948088](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016223948088.png)

  ![image-20211016223952662](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016223952662.png)

- 用自己的土方法来解决

  ```java
  //使用老师的土方法来解决 ResultSet =封装=> Arraylist
  
  @Test
  public ArrayList<Actor> testSelectToArrayList() {
  
  
      System.out.println("使用 druid 方式完成");
      //1. 得到连接
      Connection connection = null;
      //2. 组织一个 sql
      String sql = "select * from actor where id >= ?"; 
      PreparedStatement preparedStatement = null; 
      ResultSet set = null;
      ArrayList<Actor> list = new ArrayList<>();//创建 ArrayList 对象,存放 actor 对象
      //3. 创建 PreparedStatement 对象
      try {
      	connection = JDBCUtilsByDruid.getConnection();
      	System.out.println(connection.getClass());//运行类型 
          com.alibaba.druid.pool.DruidPooledConnection preparedStatement = connection.prepareStatement(sql);
      	preparedStatement.setInt(1, 1);//给?号赋值
      	//执行, 得到结果集
      	set = preparedStatement.executeQuery();
  
          //遍历该结果集
          while (set.next()) {
              int id = set.getInt("id");
              String name = set.getString("name");//getName() 
              String sex = set.getString("sex");//getSex()
              Date borndate = set.getDate("borndate"); 
              String phone = set.getString("phone");
              //把得到的 resultset 的记录，封装到 Actor 对象，放入到 list 集合
              list.add(new Actor(id, name, sex, borndate, phone));
          }
  
          System.out.println("list 集合数据=" + list); 
          for(Actor actor : list) {
          	System.out.println("id=" + actor.getId() + "\t" + actor.getName());
      	}
  
  
      } catch (SQLException e) { 
          e.printStackTrace();
      } finally {
      	//关闭资源
      	JDBCUtilsByDruid.close(set, preparedStatement, connection);
      }
      //因为 ArrayList 和 connection 没有任何关联，所以该集合可以复用. 
      return	list;
  }   
  ```

  

- Apache-DBUtils基本介绍

  ![image-20211016224608417](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016224608417.png)

- 应用实例

  ![image-20211016224739726](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016224739726.png)

  ```java
  package com.hspedu.jdbc.datasource;
  
  import org.apache.commons.dbutils.QueryRunner;
  import org.apache.commons.dbutils.handlers.BeanHandler;
  import org.apache.commons.dbutils.handlers.BeanListHandler;
  import org.apache.commons.dbutils.handlers.ScalarHandler; 
  import org.junit.jupiter.api.Test;
  import java.sql.*;
  import java.util.ArrayList; 
  import java.util.List;
  
  /**
  *@author 韩顺平
  *@version 1.0
  */ @SuppressWarnings({"all"}) 
  public class DBUtils_USE {
  
      //使用 apache-DBUtils  工具类 + druid  完成对表的 crud 操作
      @Test
      public void testQueryMany() throws SQLException { //返回结果是多行的情况
  
  
          //1. 得到 连接 (druid)
          Connection connection = JDBCUtilsByDruid.getConnection();
          //2. 使用 DBUtils  类和接口 ,  先引入 DBUtils  相关的 jar ,  加入到本 Project
          //3. 创建 QueryRunner
          QueryRunner queryRunner = new QueryRunner();
          //4. 就可以执行相关的方法，返回 ArrayList  结果集
          //String sql = "select * from actor where id >= ?";
          //	注意: sql 语句也可以查询部分列
          String sql = "select id, name from actor where id >= ?";
          // 老韩解读
          //(1) query  方法就是执行 sql 语句，得到 resultset ---封装到 --> ArrayList 集合中
              //(2) 返回集合
          //(3) connection: 连接
          //(4) sql : 执行的 sql 语句
          //(5) new BeanListHandler<>(Actor.class): 在将 resultset -> Actor 对象 -> 封装到 ArrayList
          //	底层使用反射机制 去获取 Actor 类的属性，然后进行封装
          //(6) 1  就是给 sql  语句中的? 赋值，可以有多个值，因为是可变参数 Object... params
          //(7) 底层得到的 resultset ,会在 query 关闭, 关闭 PreparedStatment
          /**
          *分析 queryRunner.query 方法:
          *public <T> T query(Connection conn, String sql, ResultSetHandler<T> rsh, Object... params) throws SQLException {
              *PreparedStatement stmt = null;//定义 PreparedStatement
              *ResultSet rs = null;//接收返回的 ResultSet
              *Object result = null;//返回 ArrayList
              *
              *try {
              *	stmt = this.prepareStatement(conn, sql);//创建 PreparedStatement
              *	this.fillStatement(stmt, params);//对 sql  进行 ? 赋值
              *	rs = this.wrap(stmt.executeQuery());//执行 sql,返回 resultset
              *	result = rsh.handle(rs);//返回的 resultset --> arrayList[result] [使用到反射，对传入 class 对象处理]
              *} catch (SQLException var33) {
              *	this.rethrow(var33, sql, params);
              *} finally {
              *	try {
              *		this.close(rs);//关闭 resultset
              *	} finally {
              *		this.close((Statement)stmt);//关闭 preparedstatement 对象
              *	}
              *}
              *
              *return result;
          *	}
          */
          List<Actor> list =
          	queryRunner.query(connection, sql, new BeanListHandler<>(Actor.class), 1);
          System.out.println("输出集合的信息"); 
          for (Actor actor : list) {
          	System.out.print(actor);
          }
  
          //释放资源
          JDBCUtilsByDruid.close(null, null, connection);
  
  
      }
  
  
      //演示 apache-dbutils + druid 完成 返回的结果是单行记录(单个对象) 
      @Test
      public void testQuerySingle() throws SQLException {
  
  
          //1. 得到 连接 (druid)
          Connection connection = JDBCUtilsByDruid.getConnection();
          //2. 使用 DBUtils  类和接口 ,  先引入 DBUtils  相关的 jar ,  加入到本 Project
          //3. 创建 QueryRunner
          QueryRunner queryRunner = new QueryRunner();
          //4. 就可以执行相关的方法，返回单个对象
          String sql = "select * from actor where id = ?";
          // 老韩解读
          // 因为我们返回的单行记录<--->单个对象 ,  使用的 Hander 是 BeanHandler
          Actor actor = queryRunner.query(connection, sql, new BeanHandler<>(Actor.class), 10); 
          System.out.println(actor);
  
          // 释放资源
          JDBCUtilsByDruid.close(null, null, connection);
      }
  
  
      //演示 apache-dbutils + druid 完成查询结果是单行单列-返回的就是 object
      @Test
      public void testScalar() throws SQLException {
  
  
          //1. 得到 连接 (druid)
          Connection connection = JDBCUtilsByDruid.getConnection();
          //2. 使用 DBUtils  类和接口 ,  先引入 DBUtils  相关的 jar ,  加入到本 Project
          //3. 创建 QueryRunner
          QueryRunner queryRunner = new QueryRunner();
          //4. 就可以执行相关的方法，返回单行单列 , 返回的就是 Object
          String sql = "select name from actor where id = ?";
          //老师解读： 因为返回的是一个对象, 使用的 handler 就是 ScalarHandler 
          Object obj = queryRunner.query(connection, sql, new ScalarHandler(), 4); 
          System.out.println(obj);
  
          // 释放资源
          JDBCUtilsByDruid.close(null, null, connection);
      }
  
  
      //演示 apache-dbutils + druid 完成 dml (update, insert ,delete) 
      @Test
      public void testDML() throws SQLException {
  
  
          //1. 得到 连接 (druid)
          Connection connection = JDBCUtilsByDruid.getConnection();
          //2. 使用 DBUtils  类和接口 ,  先引入 DBUtils  相关的 jar ,  加入到本 Project
          //3. 创建 QueryRunner
          QueryRunner queryRunner = new QueryRunner();
  
  
          //4. 这里组织 sql  完成 update, insert delete
          //String sql = "update actor set name = ? where id = ?";
          //String sql = "insert into actor values(null, ?, ?, ?, ?)"; 
          String sql = "delete from actor where id = ?";
  
          //老韩解读
          //(1) 执行 dml 操作是 queryRunner.update()
          //(2) 返回的值是受影响的行数 (affected:  受影响)
          //int affectedRow = queryRunner.update(connection, sql, "林青霞", "女", "1966-10-10", "116"); 
          int affectedRow = queryRunner.update(connection, sql, 1000 );
          System.out.println(affectedRow > 0 ? "执行成功" : "执行没有影响到表");
  
  
          // 释放资源
          JDBCUtilsByDruid.close(null, null, connection);
      }
  }
  ```

- 表和JavaBean 的类型映射关系

  ![image-20211016224905479](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211016224905479.png)





### 8. DAO增删改查

- 先分析一个问题

  ![image-20211017224546817](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211017224546817.png)

  ![image-20211017224555627](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211017224555627.png)

  ![image-20211017224601121](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211017224601121.png)

- 基本说明

  ![image-20211017224633559](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211017224633559.png)

- BasicDAO 应用实例

  ![image-20211017224733536](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211017224733536.png)

  ```java
  package com.hspedu.dao_.domain;
  
  import java.util.Date;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *Actor 对象和 actor 表的记录对应
  *
  */
  public class Actor { //Javabean, POJO, Domain 对象
  
      private Integer id;
      private String name; 
      private String sex; 
      private Date borndate; 
      private String phone;
  
      public Actor() { //一定要给一个无参构造器[反射需要]
      }
  
  
      public Actor(Integer id, String name, String sex, Date borndate, String phone) { 
          this.id = id;
      	this.name = name;
          this.sex = sex; 
          this.borndate = borndate;
          this.phone = phone;
      }
  
  
      public Integer getId() { 
          return id;
      }
  
  
      public void setId(Integer id) {
          this.id = id;
      }
  
      public String getName() {
          return name;
      }
  
  
      public void setName(String name) {
          this.name = name;
      }
  
  
      public String getSex() {
          return sex;
      }
  
  
      public void setSex(String sex) {
          this.sex = sex;
      }
  
  
      public Date getBorndate() {
          return borndate;
      }
  
  
      public void setBorndate(Date borndate) { 
          this.borndate = borndate;
      }
  
  
      public String getPhone() {
          return phone;
      }  
          public void setPhone(String phone) { 
              this.phone = phone;
      }
  
  
      @Override
      public String toString() { 
          return "\nActor{" +
              "id=" + id +
              ", name='" + name + '\'' +
              ", sex='" + sex + '\'' +
              ", borndate=" + borndate + ", phone='" + phone + '\'' + '}';
      }
  }
  
  =======================
  package com.hspedu.jdbc.datasource;
  
  import com.alibaba.druid.pool.DruidDataSourceFactory;
  import javax.sql.DataSource; 
  import java.io.FileInputStream;
  import java.io.IOException; 
  import java.sql.Connection; 
  import java.sql.ResultSet; 
  import java.sql.SQLException;
  import java.sql.Statement;
  import java.util.Properties;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *基于 druid 数据库连接池的工具类
  */
  public class JDBCUtilsByDruid {
     
      private static DataSource ds;
  
  
      //在静态代码块完成 ds 初始化
      static {
          Properties properties = new Properties(); 
          try {
          	properties.load(new FileInputStream("src\\druid.properties")); 
              ds = DruidDataSourceFactory.createDataSource(properties);
          } catch (Exception e) { 
              e.printStackTrace();
          }
  
      }
  
  
      //编写 getConnection 方法
      public static Connection getConnection() throws SQLException { 
          return ds.getConnection();
      }
  
  
      //关闭连接, 老师再次强调： 在数据库连接池技术中，close 不是真的断掉连接
      //而是把使用的 Connection 对象放回连接池
      public static void close(ResultSet resultSet, Statement statement, Connection connection) {
  
          try {
          if (resultSet != null) {
             resultSet.close();
          }
          if (statement != null) { 
              statement.close();
          }
          if (connection != null) { 
              connection.close();
          }
          } catch (SQLException e) {
          	throw new RuntimeException(e);
          }
  	}
  } 
  ===============================
  package com.hspedu.dao_.dao;
  
  import com.hspedu.dao_.utils.JDBCUtilsByDruid;
  import org.apache.commons.dbutils.QueryRunner;
  import org.apache.commons.dbutils.handlers.BeanHandler; import org.apache.commons.dbutils.handlers.BeanListHandler; import org.apache.commons.dbutils.handlers.ScalarHandler;
  import java.sql.Connection; 
  import java.sql.SQLException; 
  import java.util.List;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *开发 BasicDAO ,  是其他 DAO 的父类,  使用到 apache-dbutils
  */
  public class BasicDAO<T> { //泛型指定具体类型
  
      private QueryRunner qr = new QueryRunner();
  
  
      //开发通用的 dml 方法,  针对任意的表
      public int update(String sql, Object... parameters) {
  
  
          Connection connection = null;
  
  
          try {
          	connection = JDBCUtilsByDruid.getConnection(); 
              int update = qr.update(connection, sql, parameters);
              return update;
             } catch (SQLException e) {
          throw	new RuntimeException(e); //将编译异常->运行异常 ,抛出
          } finally {
          JDBCUtilsByDruid.close(null, null, connection);
          }
  
  
      }
  
  
      //返回多个对象(即查询的结果是多行), 针对任意表
  
  
      /**
      *
      *@param sql sql  语句，可以有 ?
      *@param clazz 传入一个类的 Class 对象 比如 Actor.class
      *@param parameters 传入 ? 的具体的值，可以是多个
      *@return 根据 Actor.class 返回对应的 ArrayList 集合
      */
      public List<T> queryMulti(String sql, Class<T> clazz, Object... parameters) {
  
  
          Connection connection = null; try {
          connection = JDBCUtilsByDruid.getConnection();
          return qr.query(connection, sql, new BeanListHandler<T>(clazz), parameters);
  
  
          } catch (SQLException e) {
          throw	new RuntimeException(e); //将编译异常->运行异常 ,抛出
            } finally {
          JDBCUtilsByDruid.close(null, null, connection);
          }
  
  
      }
  
  
      //查询单行结果 的通用方法
      public T querySingle(String sql, Class<T> clazz, Object... parameters) {
  
  
          Connection connection = null; try {
          connection = JDBCUtilsByDruid.getConnection();
          return	qr.query(connection, sql, new BeanHandler<T>(clazz), parameters);
  
  
          } catch (SQLException e) {
          throw	new RuntimeException(e); //将编译异常->运行异常 ,抛出
          } finally {
          JDBCUtilsByDruid.close(null, null, connection);
          }
      }
  
  
      //查询单行单列的方法,即返回单值的方法
  
  
      public Object queryScalar(String sql, Object... parameters) {
  
  
          Connection connection = null;
          try {
          connection = JDBCUtilsByDruid.getConnection();
          return	qr.query(connection, sql, new ScalarHandler(), parameters);
  
  
          } catch (SQLException e) {
          throw	new RuntimeException(e); //将编译异常->运行异常 ,抛出
          } finally {
          JDBCUtilsByDruid.close(null, null, connection);
          }
      }
  
  
  }
  ==========================
  package com.hspedu.dao_.dao;
  
  
  import com.hspedu.dao_.domain.Actor;
  
  
  /**
  *@author 韩顺平
  *@version 1.0
  */
  public class ActorDAO extends BasicDAO<Actor> {
  //1. 就有 BasicDAO 的方法
  //2. 根据业务需求，可以编写特有的方法.
  }
  ==================================================
  package com.hspedu.dao_.test;
  
  import com.hspedu.dao_.dao.ActorDAO; 
  import com.hspedu.dao_.domain.Actor;
  import org.junit.jupiter.api.Test;
  
  import java.util.List;
  
  
  /**
  *@author 韩顺平
  *@version 1.0
  */
  public class TestDAO {
  
      //测试 ActorDAO 对 actor 表 crud 操作
      @Test
      public void testActorDAO() {
  
          ActorDAO actorDAO = new ActorDAO();
          //1. 查询
          List<Actor> actors = actorDAO.queryMulti("select * from actor where id >= ?", Actor.class, 1);
          System.out.println("===查询结果===");
          for (Actor actor : actors) {
          	System.out.println(actor);
          }
           //2. 查询单行记录
          Actor actor = actorDAO.querySingle("select * from actor where id = ?", Actor.class, 6);
          System.out.println("====查询单行结果===="); 
          System.out.println(actor);
  
          //3. 查询单行单列
          Object o = actorDAO.queryScalar("select name from actor where id = ?", 6);
          System.out.println("====查询单行单列值==="); 
          System.out.println(o);
  
          //4. dml 操作	insert ,update, delete
          int update = actorDAO.update("insert into actor values(null, ?, ?, ?, ?)", "张无忌", "男", "2000-11-11", "999");
          System.out.println(update > 0 ? "执行成功" : "执行没有影响表");
      }
  }
  ```
  
  

## 第二十三章  正则表达式

### 1. 基本介绍

- 介绍

  ![image-20211020200101070](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020200101070.png)

  

### 2. 正则表达式底层实现

- 实例分析

  为让大家对正则表达式底层实现有一个直观的映象，给大家举个实例给你一段字符串(文本),请找出所有四个数字连在一起的子串， 比如:
  应该找到	1998	1999 3443 9889	===>	分析底层实现

  ```java
  package com.hspedu.regexp;
  
  import java.util.regex.Matcher;
  import java.util.regex.Pattern;
  /**
  *@author 韩顺平
  *@version 1.0
  * 分析 java 的正则表达式的底层实现(重要.)
  */
  
  public class RegTheory {
      public static void main(String[] args) {
  
          String content = "1998 年 12 月 8 日，第二代 Java 平台的企业版 J2EE 发布。1999 年 6 月，Sun 公司发布了"
          +
          "第二代 Java 平台（简称为 Java2）的 3 个版本：J2ME（Java2 Micro Edition，Java2 平台的微型" +
          "版），应用于移动、无线及有限资源的环境；J2SE（Java 2 Standard Edition，Java 2 平台的" +
          "标准版），应用于桌面环境；J2EE（Java 2Enterprise Edition，Java 2 平台的企业版），应" +
          "用 3443 于基于 Java 的应用服务器。Java 2 平台的发布，是 Java 发展过程中最重要的一个" +
          "里程碑，标志着 Java 的应用开始普及 9889 ";
          
          //目标：匹配所有四个数字
          //说明
          //1. \\d 表示一个任意的数字
          String regStr = "(\\d\\d)(\\d\\d)";
          //2. 创建模式对象[即正则表达式对象] 
          Pattern pattern = Pattern.compile(regStr);
          //3. 创建匹配器
          //说明：创建匹配器 matcher， 按照 正则表达式的规则 去匹配 content 字符串
          Matcher matcher = pattern.matcher(content);
  
          //4.开始匹配
          /**
          *
          * matcher.find() 完成的任务 （考虑分组）
          *什么是分组，比如	(\d\d)(\d\d) ,正则表达式中用()  表示分组,第 1 个()表示第 1 组,第 2 个()表示第 2 组...
          *1. 根据指定的规则 ,定位满足规则的子字符串(比如(19)(98))
          *2. 找到后，将 子字符串的开始的索引记录到 matcher 对象的属性 int[] groups;
          *2.1 groups[0] = 0 ,  把该子字符串的结束的索引+1 的值记录到 groups[1] = 4
          *2.2 记录 1 组()匹配到的字符串 groups[2] = 0	groups[3] = 2
          *2.3 记录 2 组()匹配到的字符串 groups[4] = 2	groups[5] = 4
          *	2.4.如果有更多的分组.....
          *3. 同时记录 oldLast 的值为 子字符串的结束的 索引+1 的值即 4,  即下次执行 find 时，就从 4 开始匹
          配
          *
          *matcher.group(0) 分析
          *
          *源码:
          *public String group(int group) {
              *if (first < 0)
              *	throw new IllegalStateException("No match found");
              *if (group < 0 || group > groupCount())
              *	throw new IndexOutOfBoundsException("No group " + group);
              *	if ((groups[group*2] == -1) || (groups[group*2+1] == -1))
              *		return null;
              *return getSubSequence(groups[group * 2], groups[group * 2 + 1]).toString();
          *	}
          *1. 根据 groups[0]=0 和 groups[1]=4 的记录的位置，从 content 开始截取子字符串返回
          *就是 [0,4) 包含 0 但是不包含索引为 4 的位置
          *
          *如果再次指向 find 方法.仍然安上面分析来执行
          */
          while (matcher.find()) {
              //小结
              //1. 如果正则表达式有()  即分组
              //2. 取出匹配的字符串规则如下
              //3. group(0) 表示匹配到的子字符串
              //4. group(1) 表示匹配到的子字符串的第一组字串
              //5. group(2)  表示匹配到的子字符串的第 2 组字串
              //6	但是分组的数不能越界.
              System.out.println("找到: " + matcher.group(0));
              System.out.println("第 1 组()匹配到的值=" + matcher.group(1));
              System.out.println("第 2 组()匹配到的值=" + matcher.group(2));
          }
      }
  }
  ```

- ![image-20211020202451821](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020202451821.png)



### 3. 正则表达式语法

- 基本介绍

  ![image-20211020210329770](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020210329770.png)

#### 1. 元字符(Metacharacter)-转义号 \\\

![image-20211020210522921](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020210522921.png)

![image-20211020210813848](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020210813848.png)

```java
package com.hspedu.regexp;


import java.util.regex.Matcher; 
import java.util.regex.Pattern;

/**
*@author 韩顺平
*@version 1.0
*演示转义字符的使用
*/
public class RegExp02 {
    public static void main(String[] args) { 
        String content = "abc$(a.bc(123( )";
        //匹配( => \\(
        //匹配. => \\.
        //String regStr = "\\.";
        //String regStr = "\\d\\d\\d"; 
        String regStr = "\\d{3}";
        Pattern pattern = Pattern.compile(regStr); 
        Matcher matcher = pattern.matcher(content);

        while (matcher.find()) {
            System.out.println("找到 " + matcher.group(0));
        }
    }
}
```

#### 2.元字符-字符匹配符

![image-20211020210850924](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020210850924.png)

![image-20211020210900169](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020210900169.png)

```java
package com.hspedu.regexp;

import java.util.regex.Matcher; 
import java.util.regex.Pattern;

/**
*@author 韩顺平
*@version 1.0
*演示字符匹配符 的使用
*/
public class RegExp03 {
    public static void main(String[] args) {

        String content = "a11c8abc _ABCy @";
        //String regStr = "[a-z]";//匹配 a-z 之间任意一个字符
        //String regStr = "[A-Z]";//匹配 A-Z 之间任意一个字符
        //String regStr = "abc";//匹配 abc 字符串[默认区分大小写]
        //String regStr = "(?i)abc";//匹配 abc 字符串[不区分大小写]
        //String regStr = "[0-9]";//匹配 0-9 之间任意一个字符
        //String regStr = "[^a-z]";//匹配 不在 a-z 之间任意一个字符
        //String regStr = "[^0-9]";//匹配 不在 0-9 之间任意一个字符
        //String regStr = "[abcd]";//匹配 在 abcd 中任意一个字符
        //String regStr = "\\D";//匹配 不在 0-9 的任意一个字符
        //String regStr = "\\w";//匹配 大小写英文字母,  数字，下划线
        //String regStr = "\\W";//匹配 等价于 [^a-zA-Z0-9_]
        //\\s 匹配任何空白字符(空格,制表符等)
        //String regStr = "\\s";
        //\\S 匹配任何非空白字符 ,和\\s 刚好相反
        //String regStr = "\\S";
        //.	匹配除 \n 之外的所有字符,如果要匹配.本身则需要使用 \\. 
        String regStr = ".";

        //说明
        //1. 当创建 Pattern 对象时，指定 Pattern.CASE_INSENSITIVE, 表示匹配是不区分字母大小写. 
        Pattern pattern = Pattern.compile(regStr/*, Pattern.CASE_INSENSITIVE*/);
        Matcher matcher = pattern.matcher(content);

        while (matcher.find()) {
        	System.out.println("找到 " + matcher.group(0));
        }
    }
}    
```



#### 3.元字符-选择匹配符

![image-20211020211112985](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020211112985-16347354738692.png)

```java
package com.hspedu.regexp;


import java.util.regex.Matcher;
import java.util.regex.Pattern;

/**
*@author 韩顺平
*@version 1.0
*选择匹配符
*/
public class RegExp04 {
    public static void main(String[] args) {


        String content = "hanshunping 韩 寒冷"; 
        String regStr = "han|韩|寒";

        Pattern pattern = Pattern.compile(regStr/*, Pattern.CASE_INSENSITIVE*/); 
        Matcher matcher = pattern.matcher(content);
        while (matcher.find()) {
            System.out.println("找到 " + matcher.group(0));
        }
    }
}
```

#### 4. 元字符-限定符  (注意：java 匹配默认贪婪匹配)

- 在其他限定符后加？，匹配模式就是“非贪心的”！！

- 用于指定其前面的字符和组合项连续出现多少次

![image-20211020211242292](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020211242292.png)

```java
package com.hspedu.regexp;


import java.util.regex.Matcher; 
import java.util.regex.Pattern;

/**
*@author 韩顺平
*@version 1.0
*演示限定符的使用
*/
public class RegExp05 {
    public static void main(String[] args) { 
        String content = "a211111aaaaaahello";

        //a{3},1{4},\\d{2}
        //String regStr = "a{3}";//  表示匹配 aaa
        //String regStr = "1{4}";//  表示匹配 1111
        //String regStr = "\\d{2}";//  表示匹配 两位的任意数字字符

        //a{3,4},1{4,5},\\d{2,5}

        //细节：java 匹配默认贪婪匹配，即尽可能匹配多的
        //String regStr = "a{3,4}"; //表示匹配 aaa 或者 aaaa
        //String regStr = "1{4,5}"; //表示匹配 1111 或者 11111
        //String regStr = "\\d{2,5}"; //匹配 2 位数或者 3,4,5


        //1+
        //String regStr = "1+"; //匹配一个 1 或者多个 1
        //String regStr = "\\d+"; //匹配一个数字或者多个数字

        //1*
                                                	
        //String regStr = "1*"; //匹配 0 个 1 或者多个 1

        //演示?的使用, 遵守贪婪匹配
        String regStr = "a1?"; //匹配 a 或者 a1
        Pattern pattern = Pattern.compile(regStr/*, Pattern.CASE_INSENSITIVE*/); 
        Matcher matcher = pattern.matcher(content);

        while (matcher.find()) {
        	System.out.println("找到 " + matcher.group(0));
    	}
    }
}
```



#### 5. 元字符-定位符

- 定位符, 规定要匹配的字符串出现的位置，比如在字符串的开始还是在结束的位置，这个也是相当有用的，必须掌握！！

![image-20211020211525914](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020211525914.png)

```java
import java.util.regex.Matcher; 
import java.util.regex.Pattern;

/**
*@author 韩顺平
*@version 1.0
*演示定位符的使用
*/
public class RegExp06 {
    public static void main(String[] args) {

        String content = "hanshunping sphan nnhan";
        //String content = "123-abc";
        //以至少 1 个数字开头，后接任意个小写字母的字符串
        //String regStr = "^[0-9]+[a-z]*";
        //以至少 1 个数字开头,  必须以至少一个小写字母结束
        //String regStr = "^[0-9]+\\-[a-z]+$";

        //表示匹配边界的 han[这里的边界是指：被匹配的字符串最后,
        // 也可以是空格的子字符串的后面]
        //String regStr = "han\\b";

        //和\\b 的含义刚刚相反
        String regStr = "han\\B"; 
        Pattern pattern = Pattern.compile(regStr); 
        Matcher matcher = pattern.matcher(content);
        while (matcher.find()) {
        	System.out.println("找到=" + matcher.group(0));
        }
    }
}   
```



#### 6. 分组

![image-20211020230753720](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020230753720.png)

![image-20211020230816376](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020230816376.png)

```java
package com.hspedu.regexp;


import java.util.regex.Matcher; import java.util.regex.Pattern;

/**
*@author 韩顺平
*@version 1.0
*分组:
*/
public class RegExp07 {
    public static void main(String[] args) {
        String content = "hanshunping s7789 nn1189han";

        //下面就是非命名分组
        //说明
        // 1. matcher.group(0) 得到匹配到的字符串
        // 2. matcher.group(1) 得到匹配到的字符串的第 1 个分组内容
        // 3. matcher.group(2) 得到匹配到的字符串的第 2 个分组内容

        //String regStr = "(\\d\\d)(\\d\\d)";//匹配 4 个数字的字符串

        //命名分组： 即可以给分组取名
        String regStr = "(?<g1>\\d\\d)(?<g2>\\d\\d)";//匹配 4 个数字的字符串

        Pattern pattern = Pattern.compile(regStr); 
        Matcher matcher = pattern.matcher(content);

        while (matcher.find()) {
            System.out.println("找到=" + matcher.group(0));
            System.out.println("第 1 个分组内容=" + matcher.group(1));
            System.out.println("第 1 个分组内容[通过组名]=" + matcher.group("g1"));
            System.out.println("第 2 个分组内容=" + matcher.group(2));
            System.out.println("第 2 个分组内容[通过组名]=" + matcher.group("g2"));


        }
    }
}    
```

```java
import java.util.regex.Pattern;

/**
*@author 韩顺平
*@version 1.0
*演示非捕获分组, 语法比较奇怪
*/
public class RegExp08 {
    public static void main(String[] args) {


        String content = "hello 韩顺平教育 jack 韩顺平老师 韩顺平同学 hello 韩顺平学生";


        //	找到 韩顺平教育 、韩顺平老师、韩顺平同学 子字符串
        //String regStr = "韩顺平教育|韩顺平老师|韩顺平同学";
        //上面的写法可以等价非捕获分组, 注意：不能 matcher.group(1)
        //String regStr = "韩顺平(?:教育|老师|同学)";


        //找到 韩顺平 这个关键字,但是要求只是查找韩顺平教育和 韩顺平老师 中包含有的韩顺平
        //下面也是非捕获分组，不能使用 matcher.group(1)
        //String regStr = "韩顺平(?=教育|老师)";


        //找到 韩顺平 这个关键字,但是要求只是查找 不是 (韩顺平教育 和 韩顺平老师) 中包含有的韩顺平
        //下面也是非捕获分组，不能使用 matcher.group(1) String regStr = "韩顺平(?!教育|老师)";

        Pattern pattern = Pattern.compile(regStr);
        Matcher matcher = pattern.matcher(content); 
        while (matcher.find()) {
        	System.out.println("找到: " + matcher.group(0));
        }
    }
}    
```



#### 7.应用案例

- 对字符串进行如下验证

  ![image-20211020232700829](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020232700829.png)

  ```java
  package com.hspedu.regexp;
  
  
  import java.util.regex.Matcher;
  import java.util.regex.Pattern;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *正则表达式的应用实例
  */
  public class RegExp10 {
      public static void main(String[] args) { 
          String content = "13588889999";
          // 汉字
          //String regStr = "^[\u0391-\uffe5]+$";
          // 邮政编码
          // 要求：1.是 1-9 开头的一个六位数.	比如：123890
          //	2.
          //	3.
          //String regStr = "^[1-9]\\d{5}$";
          // QQ 号码
          // 要求:	是 1-9 开头的一个(5 位数-10 位数)	比如:	12389 , 1345687 , 187698765
          //String regStr = "^[1-9]\\d{4,9}$";
  
  
          // 手机号码
          // 要求: 必须以 13,14,15,18 开头的 11 位数 , 比如 13588889999 
          String regStr = "^1[3|4|5|8]\\d{9}$";
  
          Pattern pattern = Pattern.compile(regStr); 
          Matcher matcher = pattern.matcher(content); 
          if(matcher.find()) {
          	System.out.println("满足格式");
          } else {
          	System.out.println("不满足格式");
          }
      }
  }                                        
  ```

  ```java
  package com.hspedu.regexp;
  
  
  import java.util.regex.Matcher; 
  import java.util.regex.Pattern;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示正则表达式的使用
  */
  public class RegExp11 {
      public static void main(String[] args) {
  
  
          //String content = "https://www.bilibili.com/video/BV1fh411y7R8?from=search&seid=1831060912083761326"; 
          String	content	=        "http://edu.3dsmax.tech/yg/bilibili/my6652/pc/qg/05-51/index.html#201211-1?track_id=jMc0jn-hm-yHrNfVad37YdhOUh41XY mjlss9zocM26gspY5ArwWuxb4wYWpmh2Q7GzR7doU0wLkViEhUlO1qNtukyAgake2jG1bTd23lR57XzV83E9bAXWkStcAh 4j9Dz7a87ThGlqgdCZ2zpQy33a0SVNMfmJLSNnDzJ71TU68Rc-3PKE7VA3kYzjk4RrKU";
  
          /**
          *思路
          * 1. 先确定 url  的开始部分 https:// | http://
          * 2.然后通过 ([\w-]+\.)+[\w-]+ 匹配 www.bilibili.com
          * 3. /video/BV1fh411y7R8?from=sear 匹配(\/[\w-?=&/%.#]*)?
          */
          //多写多练，多总结
          String regStr = "^((http|https)://)?([\\w-]+\\.)+[\\w-]+(\\/[\\w-?=&/%.#]*)?$";//注意：[. ? *]表示匹配就是.本身
  
  
          Pattern pattern = Pattern.compile(regStr); 
          Matcher matcher = pattern.matcher(content); 
          if(matcher.find()) {
          	System.out.println("满足格式");
          } else {
          	System.out.println("不满足格式");
          }
  
  
          //这里如果使用 Pattern 的 matches  整体匹配 比较简洁
          System.out.println(Pattern.matches(regStr, content));//
  
  
      }
  }
  ```

  







### 4. 三个常用类

- 正则表达式三个常用类

  ![image-20211020235455420](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211020235455420-16347452969184.png)

  ![image-20211021000039115](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211021000039115.png)

  ![image-20211021000216728](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211021000216728.png)

  ```java
  package com.hspedu.regexp;
  
  import java.util.regex.Pattern;
  
  
  /**
  *@author 韩顺平
  *@version 1.0
  *演示 matches 方法，用于整体匹配,  在验证输入的字符串是否满足条件使用
  */
  public class PatternMethod {
  
      public static void main(String[] args) {
          String content = "hello abc hello,  韩顺平教育";
          //String regStr = "hello"; 
          String regStr = "hello.*";
  
          boolean matches = Pattern.matches(regStr, content);
          System.out.println("整体匹配= " + matches);
      }
  }    
  ```

  ```java
  package com.hspedu.regexp;
  
  
  import java.util.regex.Matcher; 
  import java.util.regex.Pattern;
  
  /**
  *@author 韩顺平
  *@version 1.0
  *Matcher 类的常用方法
  */
  public class MatcherMethod {
      public static void main(String[] args) {
          String content = "hello edu jack hspedutom hello smith hello hspedu hspedu"; 
          String regStr = "hello";
  
          Pattern pattern = Pattern.compile(regStr); 
          Matcher matcher = pattern.matcher(content); 
          while (matcher.find()) {
          	System.out.println("=================");
              System.out.println(matcher.start()); 
              System.out.println(matcher.end());      
              System.out.println("找到: " +                          content.substring(matcher.start(), matcher.end()));
          }
  
          //整体匹配方法，常用于，去校验某个字符串是否满足某个规则
          System.out.println("整体匹配=" + matcher.matches());
  
  
          //完成如果 content  有 hspedu 替换成 韩顺平教育
          regStr = "hspedu";
          pattern = Pattern.compile(regStr); 
          matcher = pattern.matcher(content);
          //注意：返回的字符串才是替换后的字符串 原来的 content  不变化
          String newContent = matcher.replaceAll("韩顺平教育"); 
          System.out.println("newContent=" + newContent); 
          System.out.println("content=" + content);
  
      }
  }    
  ```

  

### 5. 分组、捕获、反向引用

- 介绍

  ![image-20211021002823503](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211021002823503.png)

- 案例

  ![image-20211021002841731](E:\Java_Notes\notebook\Java基础\Java_Notes.assets\image-20211021002841731.png)

- 经典的结巴程序

  把 类似	: "我....我要....学学学学	编程 java!";
  通过正则表达式 修改成	"我要学编程 java"

  ```java
  import java.util.regex.Pattern;
  
  /**
  *@author 韩顺平
  *@version 1.0
  */
  public class RegExp13 {
      public static void main(String[] args) {
          String content = "我....我要....学学学学	编程 java!";
  
          //1. 去掉所有的.
          Pattern pattern = Pattern.compile("\\."); 
          Matcher matcher = pattern.matcher(content); 
          content = matcher.replaceAll("");
  
          //	System.out.println("content=" + content);
  
          //2. 去掉重复的字	我我要学学学学编程 java!
          // 思路
          //(1) 使用 (.)\\1+
          //(2) 使用 反向引用$1  来替换匹配到的内容      
          // 注意：因为正则表达式变化，所以需要重置 matcher
          //	pattern = Pattern.compile("(.)\\1+");//分组的捕获内容记录到$1
          //	matcher = pattern.matcher(content);
          //	while (matcher.find()) {
           //		System.out.println("找到=" + matcher.group(0));
          //	}
          //
          //	//使用 反向引用$1 来替换匹配到的内容
          //	content = matcher.replaceAll("$1");
          //	System.out.println("content=" + content);
  
  
          //3. 使用一条语句 去掉重复的字	我我要学学学学编程 java! 
          content = Pattern.compile("(.)\\1+").matcher(content).replaceAll("$1");
  
          System.out.println("content=" + content);
      }
  }   
  ```

  

### 6. String 类中使用正则表达式

- 替换功能

  String 类	public String replaceAll(String regex,String replacement)

- 判断功能

  String 类	public boolean matches(String regex){} //使用 Pattern  和 Matcher 类

- 分割功能

  String 类	public String[] split(String regex)

  ```java
  public class StringReg {
      public static void main(String[] args) {
          String content = "2000 年 5 月，JDK1.3、JDK1.4 和 J2SE1.3 相继发布，几周后其" +
          "获得了 Apple 公司 Mac OS X 的工业标准的支持。2001 年 9 月 24 日，J2EE1.3 发" +
          "布。" +
          "2002 年 2 月 26 日，J2SE1.4 发布。自此 Java 的计算能力有了大幅提升";
  
  
          //使用正则表达式方式，将 JDK1.3 和 JDK1.4 替换成 JDK 
          content = content.replaceAll("JDK1\\.3|JDK1\\.4", "JDK");
          System.out.println(content);
  
          //要求 验证一个 手机号， 要求必须是以 138 139  开头的
          content = "13888889999";
          if (content.matches("1(38|39)\\d{8}")) {  //整体匹配
          	System.out.println("验证成功");
          } else {
          	System.out.println("验证失败");
          }
              //要求按照 #  或者 - 或者 ~ 或者 数字 来分割
          System.out.println("===================");
          content = "hello#abc-jack12smith~北京";
          String[] split = content.split("#|-|~|\\d+");
          for (String s : split) {
          	System.out.println(s);
          }
      }
  }
  ```

  

