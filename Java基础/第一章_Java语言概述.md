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
  
  
  public class A extends Base{
  //4 个属性
  //public int n1 = 100; protected int n2 = 200; int n3 = 300;
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
  
  
  //编写测试方法public void test() {
  //super 的访问不限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用 super 去访问爷爷类的成员；
  // 如果多个基类(上级类)中都有同名的成员，使用 super 访问遵循就近原则。A->B->C
  
  
  System.out.println("super.n1=" + super.n1); super.cal();
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
  
  
  //找 cal 方法(super.call()) 的顺序是直接查找父类，其他的规则一样
  //super.cal();
  
  
  //演示访问属性的规则
  //n1 和 this.n1 查找的规则是
  //(1) 先找本类，如果有，则调用
  //(2) 如果没有，则找父类(如果有，并可以调用，则调用)
  //(3) 如果父类没有，则继续找父类的父类,整个规则，就是一样的,直到 Object 类
  // 提示：如果查找属性的过程中，找到了，但是不能访问， 则报错, cannot access
  //	如果查找属性的过程中，没有找到，则提示属性不存在
  System.out.println(n1); System.out.println(this.n1);
  
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
  ```

- super 和 this 的比较

  ![image-20210917215050035](E:\Java_Notes\notebook\Java基础\第一章_Java语言概述.assets\image-20210917215050035.png)

### 7. overwrite

### 8. 多态

### 9. Object类详解

### 10. 断点调试

