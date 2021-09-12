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

