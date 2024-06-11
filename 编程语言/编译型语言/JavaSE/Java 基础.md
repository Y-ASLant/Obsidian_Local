>[!info] Java 基础教程
>
## Java简介    

Java 是由 Sun Microsystems 公司于 1995 年 5 月推出的 Java 程序设计语言（以下简称 Java 语言）和 Java 平台的总称。Java 语言是一种面向对象的编程语言。虽然 Java 仅仅只产生了短短 20 年，但是它的发展是非常迅速的。在 2009 年 4 月 20 号，ORACLE 收购了 Sun 公司，也就是说 Java 这门语言现在归属于 ORACLE 这家公司门下。    

  

![[ASLant_Images/b8d0e8af4e6f62bb201a35b94b8d5a45_MD5.jpg]]  

  

在 Java 这门语言体系当中，最基础的部分就是 Java SE 部分，Java 的标准版本。它包括 Java 最基础的一些结构，包括面向对象的一些特性等等，同时它也是 Java 技术基础和核心。在 Java SE 的基础之上，又分为了 Java EE（Java 的企业版），应用于大型企业级应用的开发。Java ME 主要用于嵌入式开发。初学的时候我们都是从 Java SE 开始的。    

  

<div align=center><img src="https://image.baidu.com/search/down?url=https://tvax1.sinaimg.cn/large/006TZ18hly1hdp07ht5f7j30ev0bf40b.jpg"></div>    

  

JVM 叫 Java 虚拟机，它也是整个 Java 技术的核心。Java 语言的跨平台就多亏了 JVM。

  

JDK 叫 Java 开发工具包，没有 JDK 就没有办法进行 Java 程序的开发。  

  

JRE 叫 Java 运行环境，如果我们需要运行一个 Java 程序，就得安装 JRE。    

  

JDK、JRE 和 JVM 之间的关系：

  

<div align=center><img src="https://image.baidu.com/search/down?url=https://tvax1.sinaimg.cn/large/006TZ18hly1hdp05zi9h0j30720730sv.jpg "></div>    

  

> # 基础语法  

  

## 变量    

---

  

变量可以指在计算机存储器里存在值的被命名的存储空间。

  

变量通常是可被修改的，即可以用来表示可变的状态。这是 Java 的基本概念之一。

  

程序通过改变变量的值来改变整个程序的状态。为了方便使用变量，所以变量都需要命名，叫做**变量名**。

  

在 Java 中，变量需要先声明 (declare) 才能使用。在声明中，说明变量的类型，赋予变量以特别名字，以便在后面的程序中调用它。你可以在程序中的任意位置声明变量，语法格式如下：

  

```txt

数据类型 变量名称;

```

  

例如：

  

```java

int a = 1;

```

  

在该语法格式中，数据类型可以是 Java 语言中任意的类型，如 `int`。变量名称是该变量的标识符，需要符合标识符的命名规则，数据类型和变量名称之间使用空格进行间隔，使用 `;` 作为结束。

  

## 常量  

  

---

  

常量代表程序运行过程中不能改变的值。我们也可以把它们理解为特殊的变量，只是它们在程序的运行过程中是不允许改变的。**常量的值是不能被修改的**。    

  

Java 中的 `final` 关键字可以用于声明属性（常量），方法和类。当 `final` 修饰属性时，代表该属性一旦被分配内存空间就必须初始化，它的含义是“这是无法改变的”或者“终态的”。在变量前面添加关键字 `final` 即可声明一个常量。在 Java 编码规范中，要求常量名必须大写。    

  

语法格式：

  

```txt

final 数据类型 常量名 = 值;

```

  

例如：  

  

```java

final double PI = 3.14;

```

  

常量也可以先声明，再进行赋值，但只能赋值一次，比如：    

  

```java

final int FINAL_VARIABLE;

FINAL_VARIABLE = 100;

```

  

## 数据类型

  

---

  

Java 中一共八种基本数据类型，下表列出了基本数据类型的数据范围、存储格式、默认值和包装类型等。

  

| 数据类型 | 默认值         | 存储格式 | 数据范围                                                     | 包装类型  |

| -------- | -------------- | -------- | ------------------------------------------------------------ | --------- |

| short    | 0              | 2 个字节 | -32,768 到 32,767                                            | Short     |

| int      | 0              | 4 个字节 | -2,147,483,648 到 2,147,483,647                              | Integer   |

| byte     | 0              | 1 个字节 | -128 到 127                                                  | Byte      |

| char     | 空             | 2 个字节 | Unicode 的字符范围：`\u0000`（即为 0）到 `\uffff`（即为 65,535） | Character |

| long     | 0L 或 0l       | 8 个字节 | -9,223,372,036,854,775,808 到 9,223,372,036,854,775,807      | Long      |

| float    | 0.0F 或 0.0f   | 4 个字节 | 32 位 IEEEE-754 单精度范围                                   | Float     |

| double   | 0.0 或 0.0D(d) | 8 个字节 | 64 位 IEEE-754 双精度范围                                    | Double    |

| boolean  | false          | 1 位     | true 或 false                                                | Boolean   |

  

#### 整数

  

`byte`、`short`、`int`、`long` 四种基本数据类型表示整数，需要注意的是 `long` 类型，使用 `long` 修饰的变量需要在数值后面加上 L 或者 l，比如 `long num = 1L;`，一般使用大写 `L`，为了避免小写 `l` 与数值 `1` 混淆。

  

#### 浮点数

  

----

  

`float` 和 `double` 类型表示浮点数，即可以表示小数部分。需要注意的是 `float` 类型的数值后面需要加上 `F` 或者 `f`，否则会被当成 `double` 类型处理。`double` 类型的数值可以加上 `D` 或 `d`，也可以不加。

  

#### char 类型

  

char 类型用于表示单个字符。需要将字符用单引号括起来`char a = 'a'`，char 可以和整数互相转换，如果字符 `a` 也可以写成`char a = 97`。也可以用十六进制表示`char a = '\u0061'`。

  

#### boolean 类型

  

`boolean` 类型（布尔类型）用于表示真值 `true`或者假值 `false`，Java 中布尔值不能和整数类型或者其它类型互相转换。    

  

## String  

  

---

  

Java 中使用 `String` 类来定义一个字符串，字符串是**常量**，它们的值在创建之后不能更改。字符串缓冲区支持可变的字符串。  

  

`String` 对象的初始化格式有如下两种：  

  

```java

String s0 = "abc";

  

String s1 = new String("abd");

```

  

String 类具有丰富的方法，比如计算字符串的长度、连接字符串、比较字符串、提取字符串等等。

  

#### 计算字符串长度

  

`length()` 方法：  

  

```java

//方法原型

public int length(){

}

```

  

调用方法：`字符串标识符.length();` 返回一个 `int` 类型的整数（字符串中字符数，中文字符也是一个字符）。例如：    

  

```java

String s1 = "abc";

String s2 = "Java语言";

int len1 = s1.length();

int len2 = s2.length();

```

  

则变量 `len1` 的值是 3，变量 `len2` 的值是 6。  

  

#### 字符串比较

  

`equals()` 方法，该方法的作用是判断两个字符串对象的内容是否相同。如果相同则返回 `true`，否则返回 `false`。  

  

`equals()` 方法比较是从第一字符开始，一个字符一个字符依次比较。

`equals比较原理:`  

<div align=center><img src="https://image.baidu.com/search/down?url=https://tvax3.sinaimg.cn/large/006TZ18hly1hdozvr7i8yj30b4051gmn.jpg"></div>

  

如果想忽略掉大小写关系，比如：java 和 Java 是一样的，那怎么办呢？可以调用 `equalsIgnoreCase()` 方法，其用法与 `equals()` 一致，不过它会忽视大小写。    

  

比如：  

  

```java

public class StringTest {

    public static void main(String[] args){

        String s = new String("Java");

        String m = "java";

        System.out.println("用equals()比较，java和Java结果为"+s.equals(m));

        System.out.println("用equalsIgnoreCase()比较，java和Java结果为"+s.equalsIgnoreCase(m));

    }

}

```

  

编译运行：  

  

```bash

$ javac StringTest.java

$ java StringTest

用equals()比较，java和Java结果为false

用equalsIgnoreCase()比较，java和Java结果为true

```

  

而使用 `"=="` 比较的是两个对象在内存中存储的地址是否一样。例如：    

  

```java

         String s1 = "abc";

         String s2 = new String("abc");

         boolean b = (s1 == s2);

```

  

则变量 `b` 的值是 `false`，因为 `s1` 对象对应的地址是 `"abc"` 的地址，而 `s2` 使用 `new` 关键字申请新的内存，所以内存地址和 `s1` 的 `"abc"` 的地址不一样，所以获得的值是 `false`。  

  

#### 字符串连接

  

字符串连接有两种方法：  

  

1. 使用 `+`，比如 `String s = "Hello " + "World!"`。

2. 使用 `String` 类的 `concat()` 方法。

  

代码示例：  

  

```java

String s0 = new String("Hello ");

String s1 = "World" + "!";   //+号连接

String s2 = s0.concat(s1); //concat()方法连接

System.out.println(s2);

```

  

而且使用 `+` 进行连接，不仅可以连接字符串，也可以连接其他类型。但是要求进行连接时至少有一个参与连接的内容是字符串类型。

  

#### charAt() 方法

  

`charAt()` 方法的作用是按照索引值（规定字符串中第一个字符的索引值是 0，第二个字符的索引值是 1，依次类推），获得字符串中的指定字符。例如：  

  

```java

String s = "abc";

char c = s.charAt(1);

```

  

则变量 `c` 的值是 `'b'`。  

  

#### 字符串常用提取方法

  

| 方法                                    | 返回值 | 功能描述                                     |

| --------------------------------------- | ------ | -------------------------------------------- |

| indexOf(char ch)                        | int    | 搜索字符 ch 第一次出现的索引                 |

| indexOf(String value)                   | int    | 搜索字符串 value 第一次出现的索引            |

| lastIndexOf(char ch)                    | int    | 搜索字符 ch 最后一次出现的索引               |

| lastIndexOf(String value)               | int    | 搜索字符串 value 最后一次出现的索引          |

| substring(int index)                    | String | 提取从位置索引开始到结束的字符串             |

| substring(int beginindex, int endindex) | String | 提取 beginindex 和 endindex 之间的字符串部分 |

| trim()                                  | String | 返回一个前后不含任何空格的调用字符串的副本   |

  

> 说明：在字符串中，第一个字符的索引为 0，子字符串包含 `beginindex` 的字符，但不包含 `endindex` 的字符。    

  

##### 实例：  

  

```java

public class StringTest {

    public static void main(String[] args) {

         String s = "abcdefabc";

         System.out.println("字符a第一次出现的位置为"+s.indexOf('a'));

         System.out.println("字符串bc第一次出现的位置为"+s.indexOf("bc"));

         System.out.println("字符a最后一次出现的位置为"+s.lastIndexOf('a'));

         System.out.println("从位置3开始到结束的字符串"+s.substring(3));

         System.out.println("从位置3开始到6之间的字符串"+s.substring(3,6));

    }

}

```

  

编译运行：    

  

```bash

$ javac StringTest.java

$ java StringTest

字符a第一次出现的位置为0

字符串bc第一次出现的位置为1

字符a最后一次出现的位置为6

从位置3开始到结束的字符串defabc

从位置3开始到6之间的字符串def

```

String 是无法被修改的，对 String 的修改，其实是新建了一个 String 对象。

如果需要修改字符串的内容，可以使用 StringBuilder。它相当于一个存储字符的容器。  

  

初始化格式有以下三种：  

  

```java

# 构造一个不包含任何字符且初始容量为 16 的 StringBuilder

StringBuilder a = new StringBuilder();

  

# 构造一个不包含任何字符且容量为 cap 的 StringBuilder

StringBuilder b = new StringBuilder(int cap);

# 构造一个 StringBuilder，内容初始化为 str

StringBuilder  c = new StringBuilder(String str);

```

  

##### 实例：    

  

```java

public class StringBuilderTest {

    public static void main(String[] args){

        StringBuilder s1 = new StringBuilder();

        s1.append("java");

        StringBuilder s2 = new StringBuilder(5);

        StringBuilder s3 = new StringBuilder("shiyanlou");

        System.out.println("s1:" + s1.toString() + "\tcap:" + s1.capacity());

        System.out.println("s2:" + s2.toString() + "\tcap:" + s2.capacity());

        System.out.println("s3:" + s3.toString() + "\tcap:" + s3.capacity());

    }

}

```

  

编译运行：  

  

```bash

$ javac StringBuilderTest.java

$ java StringBuilderTest

s1:java cap:16

s2:     cap:5

s3:shiyanlou    cap:25

```

  

其中 s3 的 capacity 为 25 是因为初始容量 16 + `shiyanlou` 的长度 9。    

  

StringBuilder 常用方法：    

  

| 方法                    | 返回值        | 功能描述                               |

| ----------------------- | ------------- | -------------------------------------- |

| deleteCharAt(int index) | StringBuilder | 删除 StringBuilder 中指定位置的 char   |

| indexOf()               | int           | 返回子字符串首次出现在该字符串中的索引 |

| capacity()              | int           | 返回当前容量                           |

| charAt(int index)       | char          | 返回序列中指定索引的 char 值           |

| toString()              | String        | 返回序列数据的 string 格式             |    

  

## 位运算符

  

---

  

Java 定义了位运算符，应用于整数类型 (`int`)，长整型 (`long`)，短整型 (`short`)，字符型 (`char`)，和字节型 (`byte`) 等类型。位运算时先转换为二进制，再按位运算。

  

表格中的例子中，变量 `a` 的值为 60（二进制：`00111100`），变量 `b` 的值为 13（二进制：`00001101`）：

  

| 位运算符 | 名称         | 描述                                                         | 举例                              |

| -------- | ------------ | ------------------------------------------------------------ | --------------------------------- |

| &        | 按位与       | 如果相对应位都是 1，则结果为 1，否则为 0                     | （a＆b），得到 12，即 0000 1100   |

| 丨       | 按位或       | 如果相对应位都是 0，则结果为 0，否则为 1                     | （ a 丨 b ）得到 61，即 0011 1101 |

| ^        | 按位异或     | 如果相对应位值相同，则结果为 0，否则为 1                     | （a^b）得到 49，即 0011 0001      |

| ~        | 按位补       | 翻转操作数的每一位，即 0 变成 1，1 变成 0                    | （~a）得到 -61，即 1100 0011      |

| <<       | 按位左移     | 左操作数按位左移右操作数指定的位数                           | a<<2 得到 240，即 1111 0000       |

| >>       | 按位右移     | 左操作数按位右移右操作数指定的位数                           | a>>2 得到 15 即 1111              |

| >>>      | 按位右移补零 | 左操作数的值按右操作数指定的位数右移，移动得到的空位以零填充 | a>>>2 得到 15 即 0000 1111        |

  

在 `/home/project` 目录下新建一个源代码文件 `BitOperation.java`：

  

```java

public class BitOperation {

    public static void main(String args[]) {

        int a = 60;

        int b = 13;

        System.out.println("a & b = " + (a & b));

        System.out.println("a | b = " + (a | b));

        System.out.println("a ^ b = " + (a ^ b));

        System.out.println("~a = " + (~a));

        System.out.println("a << 2 = " + (a << 2));

        System.out.println("a >> 2 = " + (a >> 2));

        System.out.println("a >>> 2 = " + (a >>> 2));

    }

}

```

  

编译运行：

  

```bash

$ javac BitOperation.java

$ java BitOperation

a & b = 12

a | b = 61

a ^ b = 49

~a = -61

a << 2 = 240

a >> 2 = 15

a >>> 2 = 15

```

  

## 逻辑运算符    

  

---

  

逻辑运算符是通过运算符将操作数或等式进行逻辑判断的语句。

  

表格中的例子中，假设布尔变量 `a` 为真（`true`），变量 `b` 为假（`false`）：

  

| 逻辑运算符 | 名称 | 描述                                                         | 类型       | 举例                         |

| ---------- | ---- | ------------------------------------------------------------ | ---------- | ---------------------------- |

| && 或 &    | 与   | 当且仅当两个操作数都为真，条件才为真                         | 双目运算符 | (a && b) 或 (a & b) 为假     |

| \|\| 或 \| | 或   | 两个操作数任何一个为真，条件为真                             | 双目运算符 | （a \|\| b) 或 (a \| b) 为真 |

| !          | 非   | 用来反转操作数的逻辑状态。如果条件为真，则逻辑非运算符将得到假 | 单目运算符 | （!a）为假                   |

| ^          | 异或 | 如果两个操作数逻辑相同，则结果为假，否则为真                 | 双目运算符 | (a ^ b) 为真                 |

  

`&&` 与 `||` 是具有短路性质，当按优先级顺序计算到当前表达式时，表达式的结果可以确定整个表达式的结果时，便不会继续向后进行判断和计算，而直接返回结果。

  

例如：当使用 `&&` 逻辑运算符时，在两个操作数都为 `true` 时，结果才为 `true`，但是当得到第一个操作为 `false` 时，其结果就必定是 `false`，这时候就不会再判断第二个操作了。在计算表达式 `(a & b) && (a | b)` 时，首先计算 `a & b` 得到了 `false`，因为之后是 `&&`，任何值与 `false` 进行与操作都是 `false`，所以可以不用再计算下去，而直接返回 `a & b` 的结果 `false`。

  

在`/home/project`目录下新建一个`LogicOperation.java`。

  

```java

public class LogicOperation {

    public static void main(String args[]) {

        boolean a = true;

        boolean b = false;

        System.out.println("a && b = " + (a && b));

        System.out.println("a || b = " + (a || b));

        System.out.println("!a = " + (!a));

        System.out.println("a ^ b = " + (a ^ b));

    }

}

```

  

编译运行：

  

```bash

$ javac LogicOperation.java

$ java LogicOperation

a && b = false

a || b = true

!a = false

a ^ b = true

```

  

## 关系运算符    

  

----

  

关系运算符生成的是一个 `boolean`（布尔）结果，它们计算的是操作数的值之间的关系。如果关系是真实的，结果为 `true`（真），否则，结果为 `false`（假）。

  

表格中的例子中，假设变量 `a` 为 3，变量 `b` 为 5：

  

| 比较运算符 | 名称     | 描述                                                         | 举例               |

| ---------- | -------- | ------------------------------------------------------------ | ------------------ |

| ==         | 等于     | 判断两个操作数的值是否相等，如果相等则条件为真               | (a == b） 为 false |

| !=         | 不等于   | 判断两个操作数的值是否相等，如果值不相等则条件为真           | (a != b) 为 true   |

| >          | 大于     | 判断左操作数的值是否大于右操作数的值，如果是那么条件为真     | (a > b) 为 false   |

| <          | 小于     | 判断左操作数的值是否小于右操作数的值，如果是那么条件为真     | (a < b) 为 true    |

| >=         | 大于等于 | 判断左操作数的值是否大于或等于右操作数的值，如果是那么条件为真 | (a >= b) 为 false  |

| <=         | 小于等于 | 判断左操作数的值是否小于或等于右操作数的值，如果是那么条件为真 | (a <= b) 为 true   |

  

除了上表列出的二元运算符，Java 还有唯一的一个三目运算符 `?:` 。

  

语法格式：

  

```txt

布尔表达式 ？表达式 1 : 表达式 2;

```

  

运算过程：如果布尔表达式的值为 `true`，则返回**表达式 1**的值，否则返回**表达式 2**的值。

  

在 `/home/project` 目录下新建一个源代码文件 `RelationalOperation.java`：

  

```java

public class RelationalOperation {

    public static void main(String args[]) {

        int a = 3;

        int b = 5;

        System.out.println("a == b = " + (a == b));

        System.out.println("a != b = " + (a != b));

        System.out.println("a > b = " + (a > b));

        System.out.println("a < b = " + (a < b));

        System.out.println("a >= b = " + (a >= b));

        System.out.println("a <= b = " + (a <= b));

        System.out.println("a > b ? a : b = " + (a > b ? a : b));

    }

}

```

  

编译运行：

  

```bash

$ javac RelationalOperation.java

$ java RelationalOperation

a == b = false

a != b = true

a > b = false

a < b = true

a >= b = false

a <= b = true

a > b ? a : b = 5

```

  

**强调**：

  

- `==` 和 `!=` 适用于所有的基本数据类型，其他关系运算符不适用于 `boolean`，因为 `boolean` 值只有 `true` 和 `false`，比较没有任何意义。

- `==` 和 `!=` 也适用于所有对象，可以比较对象的**引用**是否相同。

  

**引用：Java 中一切都是对象，但操作的标识符实际是对象的一个引用。**

  

#### 练习1:计算数字和

获取控制台输入的两个整型参数,

输出两个整型参数和。

比如输入` 3 `和` 4 `对应输出` 7 `。

  

示例：

  

输入：

```

    3

    4

```

输出：

```

    7

```

` 提示 `Scanner 类可以获取控制台输入的内容，但是需要先导入否则无法使用。    

##### Scanner中的nextInt和nextLine的区别  

  

```java

nextInt();   // 读取结果为一个int类型数据，返回int值

nextFloat(); // 读取结果为float类型，返回float值

next();      // 读取结果为String类型,返回string类型

nextLine();  // 读取结果为String类型,返回string类型

```

  

```java

import java.util.Scanner;

```

然后就可以获取输入的值了。

```java

Scanner in =new Scanner(System.in);

//获取int值

int x1=in.nextInt();

int x2=in.nextInt();

```

  

#### `Answer`

```java

import java.util.Scanner;

  

public class ExerCise_1 {

    public static void main(String[] args) {

        Scanner in = new Scanner(System.in);

        System.out.println(("请输入两组数字:"));

        int num_1 = in.nextInt();

        int num_2 = in.nextInt();

        System.out.println("和为:" + (num_1 + num_2));

    }

}

  

```

<div align=center><img src="https://image.baidu.com/search/down?url=https://tvax3.sinaimg.cn/large/006TZ18hly1hdoz67emqlg30tp08ljro.jpg"></div>    

## 关键字  

  

----

  

Java 的关键字对 Java 的编译器有特殊的意义，他们用来表示一种数据类型，或者表示程序的结构等，关键字不能用作变量名、方法名、类名、包名。

Java 关键字有如下表所列，目前共有 50 个 Java 关键字，其中，`const` 和 `goto` 这两个关键字在 Java 语言中并没有具体含义。    

  

<div align=center><img src="https://image.baidu.com/search/down?url=https://tvax4.sinaimg.cn/large/006TZ18hly1hdoyujby6sj30ns0aadlc.jpg"></div>

  

## 方法  

  

----

  

Java 中的方法，可以将其看成一个功能的集合，它们是为了解决特定问题的代码组合。  

  

方法的定义语法：

  

```java

访问修饰符 返回值类型 方法名(参数列表) {

    方法体

}

```

  

比如：

  

```java

public void functionName(Object arg) {

  System.out.println("Hello World.");

}

```

  

在上面的语法说明中：    

  

**访问修饰符**：代表方法允许被访问的权限范围， 可以是 `public`、`protected`、`private` 或者省略`default` ，其中 `public` 表示该方法可以被其他任何代码调用。  

**返回值类型**：方法返回值的类型，如果方法不返回任何值，则返回值类型指定为 `void` （代表无类型）；如果方法具有返回值，则需要指定返回值的类型，并且在方法体中使用 `return` 语句返回值。  

**方法名**：是方法的名字，必须使用合法的标识符。    

**参数列表**：是传递给方法的参数列表，参数可以有多个，多个参数间以逗号隔开，每个参数由参数类型和参数名组成，以空格隔开。当方法被调用时，传递值给参数。这个值被称为实参或变量。参数列表是指方法的参数类型、顺序和参数的个数。参数是可选的，方法可以不包含任何参数。  

**方法体**：方法体包含具体的语句，定义该方法的功能。    

  
  

#### 访问权限修饰符  

Java中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。Java 支持 4 种不同的访问权限    

- `default` (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法

- `private` : 在同一类内可见。使用对象：变量、方法。 注意：不能修饰类（外部类）  

- `public` : 对所有类可见。使用对象：类、接口、变量、方法    

- `protected` : 对同一包内的类和所有子类可见。使用对象：变量、方法。 注意：不能修饰类（外部类）  

  

|   修饰符    | 当前类 | 同一包内 | 子孙类(同一包) |                        子孙类(不同包)                        | 其他包 |

| :---------: | :----: | :------: | :------------: | :----------------------------------------------------------: | :----: |

|  `public`   |   Y    |    Y     |       Y        |                              Y                               |   Y    |

| `protected` |   Y    |    Y     |       Y        | Y/N（[说明](https://www.runoob.com/java/java-modifier-types.html#protected-desc)） |   N    |

|  `default`  |   Y    |    Y     |       Y        |                              N                               |   N    |

|  `private`  |   Y    |    N     |       N        |                              N                               |   N    |    

  
  

根据方法是否带参、是否带返回值，可将方法分为四类：  

  

- 无参无返回值方法  

- 无参带返回值方法  

- 带参无返回值方法  

- 带参带返回值方法  

  

当方法定义好之后，需要调用才可以生效，我们可以通过 `main` 方法（`main` 方法是 Java 程序的入口，所以需要用它来调用）来调用它。  

  

#### 练习2:方法的创建

  

新建文件 MethodTest.java，在其中新建一个方法 methodDemo，运行该方法，在控制台输出 Hello World。

  

```java

public class MethodTest {

    private static void methodDemo() {

        System.out.println("Hello World");

    }

  

    public static void main(String[] args) {

        methodDemo();

    }

}

```

  

## 流程控制

  

---

  

流程控制对任何一门编程语言都是至关重要的，它为我们提供了控制程序步骤的基本手段。常见对主要分为，条件语句、循环语句、跳转语句。  

  

#### if...else

`if` 语句是一种判断语句。  

  

语法：

  

```java

if(条件){  

    条件成立时执行的代码  

}  

```

  
  
  

`if...else` 语句当条件成立时，则执行 `if` 部分的代码块； 条件不成立时，则进入 `else` 部分。例如，如果一个月天数大于 30 天，则为大月，否则为小月。  

  

语法：  

  

```java

if(条件){  

    代码块1  

}  

else{  

    代码块2  

}  

```

  

![[ASLant_Images/316236cfb541953ab7e3557dfbbb879d_MD5.jpg]]    

  

#### if...elseif...

  

多重 `if` 语句，在条件 1 不满足的情况下，才会进行条件 2 的判断，以此向下；当前面的条件均不成立时，最终执行 `else` 块内的代码。  

  

语法：  

  

```java

if(条件1){  

    代码块1  

}  

else if(条件2){  

    代码块2  

}  

...  

else {  

    代码块n  

}  

```

  

#### if...else嵌套  

  

![[ASLant_Images/4653ddaa14877159be49012acb98512e_MD5.jpg]]

  

> 注意：如果 `if`（或 `else if`，或 `else`) 条件成立时的执行语句只有一条，是可以省略大括号的！但如果执行语句有多条，那么大括号就是不可或缺的。  

  

比如：  

  

```java

int days = 31;  

if(days > 30)  

    System.out.println("本月是大月");  

else  

    System.out.println("本月是小月");  

```

  

if 语句是可以在内层进行嵌套的。嵌套 if 语句，只有当外层 if 的条件成立时，才会判断内层 if 的条件。  

  

语法：  

  

```java

if(条件1){  

    if(条件2){  

        代码块1  

    }  

    else{  

        代码块2  

    }  

}  

else{  

    代码块3  

}  

```

  

![[ASLant_Images/0db429cafb41775203b7537985cd361a_MD5.jpg]]

  

`if` 语句练习：小明考了 78 分，60 分以上及格，80 分以上为良好，90 分以上为优秀，60 分以下要重考，编写源代码 `ScoreJudge.java`，输出小明的情况。

  

参考代码如下：  

  

```java

public class ScoreJudge {

    public static void main(String[] args) {

        int score = 78;

        if (score >= 60) {

            if (score >= 80) {

                if (score >= 90) {

                    System.out.println("成绩优秀");

                } else {

                    System.out.println("成绩良好");

                }

            } else {

                System.out.println("成绩及格");

            }

        } else {

            System.out.println("需要补考");

        }

    }

}

```

  

> **注**：所有的条件语句都是利用条件表达式的真或假来决定执行路径，Java 里不允许将一个数字作为布尔值使用，虽然这在 C 和 C++ 是允许的，如果要在布尔测试里使用一个非布尔值，需要先用一个条件表达式将其转换成布尔值，其他控制语句同理。    

  

编译执行：

  

```bash

$ javac ScoreJudge.java  

$ Java ScoreJudge  

成绩及格  

```

  

#### Switch

当需要对选项进行等值判断时，使用 `switch` 语句更加简洁明了。比如：摇号摇到 1 的得一等奖，摇到 2 的得二等奖，摇到 3 的得三等奖，摇到其他的没有奖。  

  

语法：  

  

```java

switch(表达式){  

    case 值1:  

        代码块1  

        break;  

    case 值2:  

        代码块2  

        break;  

    ...  

    default:  

        默认执行的代码块  

}  

```

  

当 `switch` 后表达式的值和 `case` 语句后的值相同时，从该位置开始向下执行，直到遇到 `break` 语句或者 `switch` 语句块结束；如果没有匹配的 `case` 语句则执行 `default` 块的代码。  

  

- `defualt` 块不是必须的，默认为空。    

  

##### 实例：  

  

```java

public class Draw {

    public static void main(String[] args) {

        int num = 2;

        switch (num) {

        case 1:

            System.out.println("恭喜你，获得了一等奖");

            break;

        case 2:

            System.out.println("恭喜你，获得了二等奖");

            break;

        case 3:

            System.out.println("恭喜你，获得了三等奖");

            break;

        default:

            System.out.println("很遗憾，下次再来");

        }

    }

}

```

  

编译运行：

  

```bash

$ javac Draw.java  

$ java Draw  

恭喜你，获得了二等奖  

```

#### while循环  

  

`while`语法：

  

```java

while(条件){  

    代码块  

}  

```

  

`while` 的执行过程是先判断，再执行。

  

1. 判断 `while` 后面的条件是否成立 ( `true` or `false` )

2. 当条件成立时，执行循环内的代码。

  

然后重复执行 `1`、`2`， 直到循环条件不成立为止。

  

![[ASLant_Images/1e6ba2beeaac439e672c0ed1341e6a92_MD5.jpg]]  

  

#### do...while循环

`do-while` 语法：  

  

```java

do{  

    代码块  

}while(条件);  

```

  

`do-while` 的执行过程是先执行一次，再循环判断（所以循环内的代码至少会执行一次）。  

  

1. 先执行一遍循环操作，然后判断循环条件是否成立。  

2. 如果条件成立，继续执行`1`、`2`，直到循环条件不成立为止。

  

![[ASLant_Images/3170c79362db610d022020cb954982f7_MD5.jpg]]    

  

#### for循环    

`for` 语法：    

  

```java

for(循环变量初始化①; 循环条件②; 循环变量值操作③){  

    循环操作④  

}  

```

  

`for` 相比 `while` 和 `do-while` 语句结构更加简洁易读，它的执行顺序：  

  

1. 执行循环变量初始化部分（1），设置循环的初始状态，此部分在**整个循环中只执行一次**。  

2. 进行循环条件的判断（2），如果条件为 `true`，则执行循环体内代码（4）；如果为 `false` ，则直接退出循环。  

3. 执行循环变量值操作部分（3），对循环变量的值进行修改，然后进行下一次循环条件判断（2）。  

  

整个循环的流程可以简化为：  

  

```txt

(1) -> [(2)->(4)->(3)] -> [(2)->(4)->(3)] -> ... => (2) 结果为 false, 退出循环。  

```

  

![[ASLant_Images/1e6ba2beeaac439e672c0ed1341e6a92_MD5.jpg]]    

  

##### 实例：    

```java

public class SumOfEven {

    public static void main(String[] args) {

        int sum = 0;

        for (int i = 1; i <= 1000; i++) {

            if (0 == i % 2) {

                sum += i;

            }

        }

        System.out.println("用for，1到1000中，所有偶数和为：" + sum);

    }

}

```

  

编译运行：  

  

```bash

$ javac SumOfEven.java  

$ java SumOfEven  

用for，1到1000中，所有偶数和为：250500  

```

#### 练习3：去除字符串空格

目录下新建文件 `StringUtil.java`，你需要实现以下需求：  

  

- 从控制台输入一行字符串    

- 去除字符串中的所有空格    

- 打印去除空格后的字符串    

  

示例：  

  

```java

输入：  

    shi ya n  lou  

输出：  

    shiyanlou  

```

  

提示：`java.util.Scanner` 可以获取控制台输入。  

  

#### `Answer`  

```java

import java.util.Scanner;

public class ExerCise_2 {

    public static void main(String[] args) {

        Scanner in =new Scanner(System.in);

        //获取String值

        String a=in.nextLine();

        StringBuilder stringBuilder = new StringBuilder(a);

        for (int i = 0; i < stringBuilder.length(); i++) {

            if (stringBuilder.charAt(i)==' ') {

                stringBuilder.deleteCharAt(i);

                i--;

            }

        }

        System.out.println(stringBuilder.toString());

    }

}

```

#### 练习4：打印星期（Switch）  

需要实现当输入 1-7 的数字时返回对应的星期：

  

- 从控制台获取一个整型参数  

- 当输入数字 1 时输出`今天是星期一`

- 当输入数字 2 时输出`今天是星期二`

  

以此类推    

  

示例：  

  

```java

输入：  

    1  

输出：  

    今天是星期一  

```

  

提示：`java.util.Scanner`可以获取控制台输入。  

  

```java

Scanner in =new Scanner(System.in);  

//获取int值  

int x=in.nextInt();  

```

  

#### `Answer`  

```java

import java.util.Scanner;  

  

public class PrintWeek {  

    public static void main(String[] args) {  

        Scanner in = new Scanner(System.in);  

        //获取int值  

        int x = in.nextInt();  

        switch (x) {  

            case 1:  

                System.out.println("今天是星期一");  

                break;  

            case 2:  

                System.out.println("今天是星期二");  

                break;  

            case 3:  

                System.out.println("今天是星期三");  

                break;  

            case 4:  

                System.out.println("今天是星期四");  

                break;  

            case 5:  

                System.out.println("今天是星期五");  

                break;  

            case 6:  

                System.out.println("今天是星期六");  

                break;  

            case 7:  

                System.out.println("今天是星期天");  

                break;  

        }  

    }  

}  

```

## 数组

  

---

  

所谓数组，是有序的元素序列。若将有限个类型相同的变量的集合命名，那么这个名称为数组名。组成数组的各个变量称为数组的分量，也称为数组的元素，有时也称为下标变量。用于区分数组的各个元素的数字编号称为下标。数组是在程序设计中，为了处理方便，把具有相同类型的若干元素按无序的形式组织起来的一种形式。这些无序排列的同类数据元素的集合称为数组。数组是用于储存多个相同类型数据的集合。-- From 百度百科

  

简单来说，数组就是相同数据类型的元素按一定顺序排列的集合。可以把它看成一个大的盒子，里面按顺序存放了多个数据类型相同的数据。    

  

![[ASLant_Images/f58eb68cb55298a92cd1067a5be62036_MD5.jpg]]  

  

数组中的元素都可以通过下标来访问，**下标从 0 开始，到数组长度 -1 结束**。例如，可以通过 `ages[0]` 获取数组中的第一个元素 18 ，`ages[3]` 就可以取到第四个元素 10。  

  

**注意**：  

  

使用数组前要声明数组。  

  

语法：  

  

```java

数据类型[ ] 数组名;   //或者: 数据类型 数组名[ ];  

```

  

数组名为任意合法的变量名，如：  

  

```java

int ages[];      //存放年龄的数组，类型为整型  

char symbol[];   //存放符号的数组，类型为字符型  

String [] name;  //存放名称的数组，类型为字符串型  

```

  

声明数组后，需要为数组分配空间，也就是定义多大的数组。  

  

语法：

  

```java

数组名 = new  数据类型 [ 数组长度 ];  

```

  

数组长度就是数组最多可存放元素的个数。可以在数组声明的时候初始化数组，或者在声明时就为它分配好空间，这样就不用再为数组分配空间。    

  

语法：

  

```java

int [] ages = {12,18,9,33,45,60}; //声明并初始化了一个整型数组，它有6个元素  

char [] symbol = new char[10] //声明并分配了一个长度为10的char型数组  

```

  

分配空间后就可以向数组中放数据了，数组中元素都是通过下标来访问的。  

如：

  

```java

ages[0]=12;  

```

  

Java 中可以将一个数组赋值给另一个数组，如：

  

```java

int [] a1 = {1,2,3};  

int [] a2;  

a2 = a1;  

```

  

这里只是复制了一个引用，即 a2 和 a1 是相同数组的不同名称。  

  

在`/home/project/`下新建一个`Test.java`测试一下。

  

```java

public class Test {

    public static void main(String[] args) {

        int[] a1 = { 1, 2, 3 };

        int[] a2;

        a2 = a1;

        for (int i = 0; i < a2.length; i++) {

            a2[i]++;

        }

        for (int i = 0; i < a1.length; i++) {

            System.out.println(a1[i]);

        }

    }

}

```

  

编译输出：  

  

```bash

$ javac Test.java  

$ java Test  

2  

3  

4  

```

  

可以看到，修改 a2 的值，a1 的值也跟着变化。

  

数组遍历：  

  

```java

int [] ages = {12, 18, 9, 33, 45, 60};  

for(int i = 0; i < ages.length; i++){ //ages.length是获取数组的长度  

    System.out.println("数组中第"+(i+1)+"个元素是 "+ages[i]); //数组下标是从零开始，一定要注意  

}  

```

  

**注意**：  

  

1. 数组下标从 0 开始。所以数组的下标范围是 0 至 数组长度 -1。  

2. 数组不能越界访问，否则会报错。  

  

for 语句在数组内可以使用特殊简化版本，在遍历数组、集合时，foreach 更简单便捷。从英文字面意思理解 foreach 也就是“ for 每一个”的意思。    

  

语法：

  

```java

for(元素类型 元素变量:遍历对象){  

    执行的代码  

}  

```

  

在`/home/project/`下新建`JudgePrime.java`

  

```java

public class JudgePrime {

    public static void main(String[] args) {

        int[] ages = { 12, 18, 9, 33, 45, 60 };

        int i = 1;

        for (int age : ages) {

            System.out.println("数组中第" + i + "个元素是" + age);

            i++;

        }

    }

}

```

  

编译运行：  

  

```bash

$ javac JudgePrime.java  

$ java JudgePrime  

数组中第1个元素是12  

数组中第2个元素是18  

数组中第3个元素是9  

数组中第4个元素是33  

数组中第5个元素是45  

数组中第6个元素是60  

```

## 二维数组

  

----

  

二维数组可以看成是一间有座位的教室，座位一般用第几排的第几个进行定位，每一个座位都有一个行和一个列的属性，一排的座位相当于一个一维数组，所以可以将二维数组简单的理解为是一种“特殊”的一维数组，它的每个数组空间中保存的是一个一维数组。  

  

`二维数组也需要声明和分配空间`    

  

语法：

  

```java

数据类型 [][] 数组名 = new 数据类型[行的个数][列的个数];  

  

//或者  

数据类型 [][] 数组名;  

数组名 = new 数据类型[行的个数][列的个数];  

  

//也可以  

数据类型 [][] 数组名 = {  

{第一行值1,第一行值2,...}  

{第二行值1,第二行值2,...}  

...  

}  

  

//二维数组的赋值和访问，跟一维数组类似，可以通过下标来逐个赋值和访问，注意索引从 0 开始  

数组名[行的索引][列的索引] = 值;    

```

  

在`/home/project/`下新建`ArrayTest.java`    

  

```java

public class ArrayTest {  

    public static void main(String[] args) {  

        String[][] name = {{"ZhaoYi", "QianEr", "SunSan"},  

                {"LiSi", "ZhouWu", "WuLiu"}};  

        for (int i = 0; i < 2; i++) {  

            for (int j = 0; j < 3; j++) {  

                System.out.println(name[i][j]);  

            }  

        }  

    }  

}  

```

  

编译运行：  

  

```bash

$ javac ArrayTest.java  

$ java ArrayTest  

ZhaoYi  

QianEr  

SunSan  

LiSi  

ZhouWu  

WuLiu  

```

  

#### 练习5：数组的应用  

有一份成绩单，上面有 10 位学生的成绩（61，57，95，85，75，65，44，66，90，32），请求出平均成绩并输出。  

  

在`/home/project/`目录下新建文件`AverageScore.java`，并在其中编写正确的代码。  

  

提示：  

  

- 将 10 位同学的成绩保存在数组中    

  

#### `Answer`  

```java

public class AverageScore {  

    public static void main(String[] args) {  

        int[] data = {61, 57, 95, 85, 75, 65, 44, 66, 90, 32};  

        int sum = 0;  

        for (int i = 0; i < data.length; i++) {  

            sum += data[i];  

        }  

        System.out.println("平均成绩：" + sum / data.length);  

    }  

}  

```

## 用户输入操作  

  

---

  

Java 可以使用 `java.util` 包下的`Scanner` 类来获取用户的输入。使用 `import java.util.Scanner;` 即可导入 Scanner，使用方法示例：

  

在 `/home/project` 目录下新建 `ScannerDemo.java` 类。  

  

```java

import java.util.Scanner;  

  

public class ScannerDemo {  

    public static void main(String[] args) {  

        Scanner in=new Scanner(System.in);  

        //获取用户输入的一行数据  返回为字符串  

        String s = in.nextLine();  

        System.out.println(s);  

        //循环读取String数据，当输入exit时退出循环  

        while (!in.hasNext("exit")) {  

            System.out.println(in.nextLine());  

        }  

        //关闭输入  

        in.close();  

    }  

}  

```

  

编译运行：  

  

```java

javac ScannerDemo.java  

java ScannerDemo  

```

  

运行结果示例：  

  

```bash

shiyanlou  

shiyanlou  

aa  

aa  

bbb  

bbb  

cc  

cc  

exit  

```

  

#### 练习6：用户输入    

你需要完成以下需求：    

  

- 获取用户的输入信息（字符串）。    

- 当用户输入 end 时，结束输入并打印用户之前输入的所有信息（输入的信息数量不超过 100 个）。  

  

示例：  

  

```bash

输入：  

    shi  

    yan  

    lou  

    end  

输出：  

    shi  

    yan  

    lou  

```

  

提示：  

  

- 使用数组保存元素。    

  

#### `Answer`  

```java

import java.util.Scanner;  

  

public class InputTest {  

    public static void main(String[] args) {  

        String[] data = new String[100];  

        Scanner in = new Scanner(System.in);  

        for (int i = 0; i < 100; i++) {  

            if ((data[i] = in.nextLine()).equals("end")) {  

                break;  

            }  

        }  

        for (String a : data) {  

            if (a.equals("end")) {  

                break;  

            }  

            System.out.println(a);  

        }  

    }  

}  

```

#### 练习7：求出最大值和最小值  

现给出一串数据（313, 89, 123, 323, 313, 15, 90, 56, 39）求出最大值和最小值并输出。      

  

#### `Answer`

> 方法一      

```java

  

public class MaxAndMin {  

    public static void main(String[] args) {  

        int[] data = {313, 89, 123, 323, 313, 15, 90, 56, 39};  

        //    方法1  

        int max = data[0];  

        int min = data[0];  

        for (int i = 0; i < data.length; i++) {  

            if (data[i] > max) {  

                max = data[i];  

            }  

            if (data[i] < min) {  

                min = data[i];  

            }  

        }  

        System.out.println(min);  

        System.out.println(max);  

    }  

}  

```

> 方法二    

  

```java

import java.util.Arrays;//导入Arrays类

  

public class ExerCise_3 {

    public static void main(String[] args) {

        int[] data = {313, 89, 123, 323, 313, 15, 90, 56, 39};

        Arrays.sort(data);//将数组从小到大排序

        System.out.println(data[0]);//最小值

        System.out.println(data[data.length - 1]);//最大值

    }

}

```

> 方法三    

```java

import java.util.Arrays;//导入Arrays类

  

public class ExerCise_3 {

    public static void main(String[] args) {

        int[] data = {313, 89, 123, 323, 313, 15, 90, 56, 39};

        System.out.println(Arrays.stream(data).min().getAsInt());//最小值

        System.out.println(Arrays.stream(data).max().getAsInt());//最大值

    }

}

```

> # 面向对象  

  

## 基本概念    

  

---

  

对象，从字面意思来看就是我们面对的物象。由此便可以知道，万事万物皆为对象。比如：一台电脑，一辆汽车，一部手机等等都是对象。  

  

面向对象，从字面意思来看就是我们人面对着一个对象。其实就是指我们从这个对象的整体出发去看它，它由哪些部件组成，它可以做到哪些事情。  

  

比如我们想要买一部手机，我们想要内存大一点的，最新款的，CPU 运算快一点的，能实现发短信和打电话功能的手机。那么这部手机是不是对象呢？它不是。当我们买了一部 iPhone 6 后，它满足我们上面的所有信息。于是我们拿在手上的这部 iPhone 6 就是我们的对象。于是我们知道，对象一定是一个具体的、确定的物体。  

  

而这部手机它的样式，颜色，大小，产地，编号等等，便是这部手机的“属性”，这部手机可以打电话、发短信，便是它的“行为”。  

  

面向对象的思想，体现的是人所关注对象的信息聚集在了一个具体的物体上。人们就是通过对象的属性和行为来了解对象。    

  

## 类  

  

---

  

对于一个具体的对象而言，比如一部 iPhone 6，世上还有许多跟这部手机有着同样属性或行为的对象，我们为了方便将它们归类起来，提取出他们相同的属性和行为，而我们把归类起来的这个抽象的概念，称之为类。

  

比如每个人就是一个对象，小张是一个对象，小明是一个对象。而每个人虽然不同，但却有许多相同的属性和行为，于是我们可以把他们抽象出来，变成一个类，比如人类。

  

类是封装对象的属性和行为的载体，反过来说具有相同属性和行为的一类实体被称为类。

  

由此可以总结出**类的定义**：    

  

> 1. 类是相同或相似对象的一种抽象，是对象的一个模板，它描述一类对象的行为和状态。  

> 2. 类是具有相同属性和方法（行为）的对象的集合    

  

我们在上面反复强调对象的属性和行为，什么是对象的属性呢？什么又是对象的行为呢？      

  

**属性**是对象具有的特征。每个对象的每个属性都拥有特定值。我们上面讲过对象是一个具体并且确定的事物，正是对象属性的值来区分不同的对象，比如我们可以通过一个人的外貌特征区分他。  

  

那什么是对象的**行为**呢？在计算机中我们通过方法去实现对象的行为，而对象的方法便是对象所具有的操作，比如人会走路、会哭泣、会学习等等都是人的行为，也就是人的方法。  

  

类和对象之间有什么关系吗？在上面的讲解中大家应该有些了解了。类就是对象的抽象（或者模板），对象就是类的具体（或者实例）。比如手机是一个抽象的概念，它代表着类。而一部 iPhone 6 便是手机具象化处理的实体，也就是一个对象。    

  

说了那么多，那我们如何在计算机中定义一个类，如何实现一个类呢？      

  

我们以前说过，Java 是面向对象的语言，而他的体现就在于 Java 程序都以 类 class 为组织单元。而一个类是对象的抽象，所以类由属性和方法两部分组成。  

  

**定义一个类**，主要有三个步骤：    

  

1、定义类名，用于区分不同的类。如下代码中 `public class` 后面跟的就是类名。`class`是声明类的关键字，类名后面跟上大括号，大括号里面就是类的一些信息。`public` 为权限修饰符。

  

```java

public class 类名 {

    //定义属性部分（成员变量）

    属性1的类型 属性1;

    属性2的类型 属性2;

    ...

    //定义方法部分

    方法1

    方法2

    ...

}

```

  

2、编写类的属性。对象有什么，需要通过属性来表示。属性的定义是写在类名后面的大括号里，在定义属性时，要明确属性的类型。在一个类当中可以写一个或多个属性。当然也可以不定义属性。  

  

3、编写类的方法。方法也是写在大括号里面。可以定义一个方法或多个方法，当然也可以不定义方法。

  

##### 实例：    

  

```java

public class People {

//属性（成员变量） 有什么

    double height;  //身高

    int age;     //年龄

    int sex;    //性别，0为男性，非0为女性

  

//方法 干什么

    void cry(){

        System.out.println("我在哭！");

    }

    void laugh(){

        System.out.println("我在笑！");

    }

    void printBaseMes(){

        System.out.println("我的身高是"+height+"cm");

        System.out.println("我的年龄是"+age+"岁");

        if(this.sex==0)

            System.out.println("我是男性！");

        else

            System.out.println("我是女性！");

  

    }

}

```

  

一个类可以包含以下**类型变量**：    

  

> - 局部变量：在方法、构造方法或者语句块中定义的变量被称为局部变量。变量声明和初始化都是在方法中，方法结束后，变量就会自动销毁。

> - 成员变量：成员变量是定义在类中，方法体之外的变量。这种变量在创建对象的时候实例化。成员变量可以被类中方法、构造方法和特定类的语句块访问。

> - 类变量：也叫静态变量，类变量也声明在类中，方法体之外，但必须声明为 `static` 类型。    

  

## 对象

  

---

  

创建对象的语法如下：    

  

```java

类名 对象名 = new 类名();

```

  

比如对 `People`这个类，我想实例化`LiLei`这个人。`LiLei` 的数据类型便是 `People` 这个类型。（类可以看成是我们自己定义的数据类型）    

  

```java

People LiLei = new People();

```

  

定义类的时候不会为类开辟内存空间，但是一旦创建了对象，系统就会在内存中为对象开辟一块空间，用来存放对象的属性值和方法。新建一个 NewObject.java 文件。    

  

```java

public class NewObject {

    public static void main(String[] args) {

        People LiLei = new People(); //创建一个People对象LiLei

  

        LiLei.height =170;

        LiLei.age = 20;

        LiLei.sex = 1;

  

        LiLei.printBaseMes();

    }

}

```

  

编译运行：      

  

```bash

$ javac NewObject.java People.java

$ java NewObject

我的身高是170.0cm

我的年龄是20岁

我是女性！

```

  

![[ASLant_Images/d8695c60505f5bf5a8ee5e325a4e33ea_MD5.jpg]]  

  

创建对象后，我们就要使用对象了，使用对象无非就是对属性和方法进行操作和调用。语法如下    

  

```java

//引用对象属性

对象名.属性

  

//引用对象方法

对象名.方法

```

  

例如对 LiLei 的身高（`length`）赋值，并调用 `cry` 这个方法

  

```java

LiLei.height = 170;

LiLei.cry();

```

  

刚刚我们引入了成员变量这个概念，那什么是成员变量呢？成员变量就是指的对象的属性，是在类中定义，来描述对象的特性。还有一种变量叫局部变量，它是由类的方法定义，在方法中临时保存数据。

  

![[ASLant_Images/200cd66f6766c45a158fd5f99b2874dd_MD5.jpg]]

  

在使用时注意，成员变量可以被本类的所有方法所使用，同时可以被与本类有关的其他类所使用。而局部变量只能在当前的方法中使用。

  

- 在这里我们要讲到一个关于作用域的知识了。作用域可以简单地理解为变量的生存期或者作用范围，也就是变量从定义开始到什么时候消亡。  

  

> 1. 局部变量的作用域仅限于定义它的方法内。而成员变量的作用域在整个类内部都是可见的。

> 2. 同时在相同的方法中，不能有同名的局部变量；在不同的方法中，可以有同名的局部变量。

> 3. 成员变量和局部变量同名时，局部变量具有更高的优先级。 大家可以编写代码验证一下。    

  

## 构造方法    

  

---

  

在面向对象中有一个非常重要的知识点，就是构造方法。每个类都有构造方法，在创建该类的对象的时候他们将被调用，如果没有定义构造方法，Java 编译器会提供一个默认构造方法。 创建一个对象的时候，至少调用一个构造方法。比如在新建一个对象 `new Object()`，括号中没有任何参数，代表调用一个无参构造方法（默认构造方法就是一个无参构造方法）。构造方法的名称必须与类名相同，一个类可以定义多个构造方法。  

  

构造方法的具体内容：    

  

1、构造方法的名称与类名相同，且没有返回值。它的语法格式如下：  

  

```java

//与类同名，可以指定参数，没有返回值

public 构造方法名(){

//初始化代码

}

```

  

下面是一个构造方法的例子：  

  

```java

public class People{

    //无参构造方法

    public People(){

  

    }

    //有一个参数的构造方法

    public People(int age){

  

    }

}

```

  

又例如具体的构造方法：  

  

```java

public class People {

//属性（成员变量）有什么

    double height;     //身高

    int age;           //年龄

    int sex;       //性别，0为男性，非0为女性

  

    //构造方法，初始化了所有属性

    public People(double h, int a, int s){

        height = h;

        age = a;

        sex = s;

    }

}

//创建对象，调用我们自己定义的有参构造方法

People XiaoMing = new People(168, 21, 1);

```

  

上面的例子中通过 `new` 关键字将类实例化成对象，而 `new` 后面跟的就是构造方法。于是可以知道 `new + 构造方法` 可以创建一个新的对象。  

  

2、如果在定义类的时候没有写构造方法，系统会默认生成一个无参构造方法，这个构造方法什么也不会做。

  

3、当有指定的构造方法时，系统都不会再添加无参构造方法了。  

  

4、构造方法的重载：方法名相同，但参数不同的多个方法，调用时会自动根据不同的参数选择相应的方法。

  

## 引用与对象实例  

  

---

  

在新建对象实例时，需要为对象实例设置一个对象名，就像这样

  

```java

Object object=new Object();

```

  

那么变量 `object` 就真的是 Object 对象么，这里其实只是创建了一个 `object` 对象的引用。如果同学们学过 C 语言，这里就和指针一样，变量 `object` 保存的其实 Object 对象的引用，指向了 Object 对象。

  

```java

 ----------           ----------

 | object |---------> | Object |

 ----------           ----------

 |        |           |        |

 ----------           ----------

 |        |           |        |

 ----------           ----------

 |        |           |        |

 ----------           ----------

 |        |           |        |

 ----------           ----------

```

  

再看下面的例子：

  

```java

Object object1 = new Object();

Object object2 = object1;

System.out.println(object1 == object2);

```

  

运行得到的结果为 `true`，说明 `object1` 和 `object2` 的内存地址相同 (`==` 会比较两个对象的内存地址是否相同），它们实际上是引用同一对象，如果改变 `object1` 对象内部的属性，那么 `object2` 的属性同样会改变，同学们可以下来验证这一点。

  

## Static  

  

---

  

#### 静态成员

  

Java 中被 `static` 修饰的成员称为静态成员或类成员。它属于整个类所有，而不是某个对象所有，即被类的所有对象所共享。静态成员可以使用类名直接访问，也可以使用对象名进行访问。

  

如：

  

```java

public class StaticTest{

    public static String string="shiyanlou";

    public static void main(String[] args){

        //静态成员不需要实例化 直接就可以访问

        System.out.println(StaticTest.string);

        //如果不加static关键字 需要这样访问

        StaticTest staticTest=new StaticTest();

        System.out.println(staticTest.string);

        //如果加上static关键字，上面的两种方法都可以使用

    }

}

```

  

#### 静态方法

  

被 `static` 修饰的方法是静态方法，静态方法不依赖于对象，不需要将类实例化便可以调用，由于不实例化也可以调用，所以不能有 `this`，也不能访问非静态成员变量和非静态方法。但是非静态成员变量和非静态方法可以访问静态方法。

  

## Final    

  

----

  

`final` 关键字可以修饰类、方法、属性和变量

  

1. `final` 修饰类，则该类不允许被继承，为最终类

2. `final` 修饰方法，则该方法不允许被覆盖（重写）

3. `final` 修饰属性：则该类的属性不会进行隐式的初始化（类的初始化属性必须有值）或在构造方法中赋值（但只能选其一）

4. final 修饰变量，则该变量的值只能赋一次值，即常量

  

如：

  

```java

//静态常量

public final static String SHI_YAN_LOU="shiyanlou";

```

  

## 访问权限修饰符

  

---

  

Java中，可以使用访问控制符来保护对类、变量、方法和构造方法的访问。Java 支持 4 种不同的访问权限

  

- `default` (即默认，什么也不写）: 在同一包内可见，不使用任何修饰符。使用对象：类、接口、变量、方法

- `private` : 在同一类内可见。使用对象：变量、方法。 注意：不能修饰类（外部类）

- `public` : 对所有类可见。使用对象：类、接口、变量、方法

- `protected` : 对同一包内的类和所有子类可见。使用对象：变量、方法。 注意：不能修饰类（外部类）

  

|   修饰符    | 当前类 | 同一包内 | 子孙类(同一包) |                        子孙类(不同包)                        | 其他包 |

| :---------: | :----: | :------: | :------------: | :----------------------------------------------------------: | :----: |

|  `public`   |   Y    |    Y     |       Y        |                              Y                               |   Y    |

| `protected` |   Y    |    Y     |       Y        | Y/N（[说明](https://www.runoob.com/java/java-modifier-types.html#protected-desc)） |   N    |

|  `default`  |   Y    |    Y     |       Y        |                              N                               |   N    |

|  `private`  |   Y    |    N     |       N        |                              N                               |   N    |

  

## 封装  

  

---

  

> 封装，即隐藏对象的属性和实现细节，仅对外公开接口，控制在程序中属性的读和修改的访问级别

  

这样做有什么好处？

  

1. 只能通过规定的方法访问数据。

2. 隐藏类的实例细节，方便修改和实现。

  

我们在开汽车的时候，只用去关注如何开车，我们并不在意车子是如何实现的，这就是封装。

  

如何去实现类的封装呢？

  

1. 修改属性的可见性，在属性的前面添加修饰符 (`private`)

2. 对每个值属性提供对外的公共方法访问，如创建 getter/setter（取值和赋值）方法，用于对私有属性的访问

3. 在 getter/setter 方法里加入属性的控制语句，例如我们可以加一个判断语句，对于非法输入给予否定。

  

![[ASLant_Images/3a66152d1ff7bda82032837e8a4f6593_MD5.jpg]]

  

如果我们没有在属性前面添加任何修饰符，我们通过对象就可以直接对属性值进行修改，没有体现封装的特性。这在许多程序设计中都是不安全的，所以我们需要利用封装，来改进我们的代码。

  

首先在类里要将属性前添加 `private` 修饰符。然后定义 `getter` 和 `setter` 方法。修改 `People.java` 和 `NewObject.java` 的内容如下。

  

```java

public class People {

    //属性（成员变量）有什么，前面添加了访问修饰符private

    //变成了私有属性，必须通过方法调用

    private double height;     //身高

  

    //属性已经封装好了，如果用户需要调用属性

    //必须用getter和setter方法进行调用

    //getter和setter方法需要程序员自己定义

    public double getHeight(){

    //getter 方法命名是get关键字加属性名（属性名首字母大写）

    //getter 方法一般是为了得到属性值

      return height;

    }

  

    //同理设置我们的setter方法

    //setter 方法命名是set关键字加属性名（首字母大写）

    //setter 方法一般是给属性值赋值，所以有一个参数

    public void setHeight(double newHeight){

      height = newHeight;

    }

}

```

  

现在 `main` 函数里的对象，不能再直接调用属性了，只能通过 `getter` 和 `setter` 方法进行调用。

  

```java

public class NewObject {

  

    public static void main(String[] args) {

        People LiLei = new People();    //创建了一个People对象LiLei

  

        //利用setter方法为属性赋值

        LiLei.setHeight(170.0);

  

        //利用getter方法取属性值

        System.out.println("LiLei的身高是"+LiLei.getHeight());

    }

}

```

  

编译运行：

  

```bash

$ javac NewObject.java People.java

$ java NewObject

LiLei的身高是170.0

```

  

## This

  

----

  

`this` 关键字代表当前对象。使用 `this.属性` 操作当前对象的属性，`this.方法` 调用当前对象的方法。

  

用 `private` 修饰的属性，必须定义 getter 和 setter 方法才可以访问到 (Eclipse 和 IDEA 等 IDE 都有自动生成 getter 和 setter 方法的功能）。

  

如下：

  

```java

public void setAge(int age) {

  this.age = age;

}

public int getAge() {

  return age;

}

```

  

创建好了 getter 和 setter 方法后，我们发现方法中参数名和属性名一样。

  

当成员变量和局部变量之间发生冲突时，在属性名前面添加了 `this` 关键字。 此时就代表将一个参数的值赋给当前对象的属性。同理 `this` 关键字可以调用当前对象的方法，同学们自行验证一下吧。

  

## 继承  

  

继承可以看成是类与类之间的衍生关系。比如狗类是动物类，牧羊犬类又是狗类。于是我们可以说狗类继承了动物类，而牧羊犬类就继承了狗类。于是狗类就是动物类的子类（或派生类），动物类就是狗类的父类（或基类）。

  

所以继承需要符合的关系是：is-a，父类更通用，子类更具体。

  

语法：

  

```java

class 子类 extends 父类

```

  

例如我们定义了一个 Animal 类，再创建一个 Dog 类，我们需要它继承 Animal 类。

  

```java

class Dog extends Animal {

    ...

}

```

  

接下来我们就来练习一下吧！

  

我们先创建一个父类 `Animal.java`：

  

```java

public class Animal {

    public int legNum;     //动物四肢的数量

  

    //类方法

    public void bark() {

        System.out.println("动物叫！");

    }

}

```

  

接下来创建一个子类`Dog.java`

  

```java

public class Dog extends Animal {

}

```

  

Dog 类继承了父类 Animal，我们 Dog 类里什么都没有写，其实它继承了父类 Animal，所以 Dog 类拥有 Animal 类的全部方法和属性（除开 private 方法和属性）。我们创建一个测试类测试一下。

  

```java

public class Test{

    public static void main(String[] args) {

        Dog a = new Dog();

        a.legNum = 4;

        a.bark();

    }

}

```

  

编译运行：

  

```bash

$ javac Test.java Animal.java Dog.java

$ java Test

动物叫！

```

  

**为什么需要继承？**

  

如果有两个类相似，那么它们会有许多重复的代码，导致后果就是代码量大且臃肿，后期的维护性不高。通过继承就可以解决这个问题，将两段代码中相同的部分提取出来组成一个父类，实现代码的复用。

  

**继承的特点**：

  

- 子类拥有父类除 `private` 以外的所有属性和方法。

- 子类可以拥有自己的属性和方法。

- 子类可以重写实现父类的方法。

- Java 中的继承是单继承，一个类只有一个父类。

  

> 注：Java 实现多继承的一个办法是 `implements`（实现）接口，但接口不能有非静态的属性，这一点请注意。

  

## Super    

  

---

  

`super` 关键字在子类内部使用，代表父类对象。

  

1. 访问父类的属性 `super.属性名`。

  

2. 访问父类的方法 `super.bark()`。

  

3. 子类构造方法需要调用父类的构造方法时，在子类的构造方法体里**最前面**的位置：`super()`。    

  

## 方法重载与重写  

  

----

  

#### 方法重载

  

方法重载是指在一个类中定义多个同名的方法，但要求每个方法具有不同的参数的类型或参数的个数。方法重载一般用于创建一组任务相似但是参数不同的方法。

  

```java

public class Test {

    void f(int i) {

        System.out.println("i=" + i);

    }

  

    void f(float f) {

        System.out.println("f=" + f);

    }

  

    void f(String s) {

        System.out.println("s=" + s);

    }

  

    void f(String s1, String s2){

        System.out.println("s1+s2="+(s1+s2));

    }

  

    void f(String s, int i){

        System.out.println("s="+s+",i="+i);

    }

  

    public static void main(String[] args) {

        Test test = new Test();

        test.f(3456);

        test.f(34.56f);

        test.f("abc");

        test.f("abc","def");

        test.f("abc",3456);

    }

}

```

  

编译运行：

  

```bash

$ javac Test.java

$ java Test

i=3456

f=34.56

s=abc

s1+s2=abcdef

s=abc,i=3456

```

  

方法重载有以下几种规则：

  

- 方法中的参数列表必须不同。比如：参数个数不同或者参数类型不同。

- 重载的方法中允许抛出不同的异常

- 可以有不同的返回值类型，但是参数列表必须不同。

- 可以有不同的访问修饰符。

  

####  方法重写

  

子类可以继承父类的方法，但如果子类对父类的方法不满意，想在里面加入适合自己的一些操作时，就需要将方法进行重写。并且子类在调用方法中，优先调用子类的方法。

  

比如 `Animal` 类中有 `bark()` 这个方法代表了动物叫，但是不同的动物有不同的叫法，比如狗是汪汪汪，猫是喵喵喵。

  

当然在方法重写时要注意，重写的方法一定要与原父类的方法语法保持一致，比如返回值类型，参数类型及个数，和方法名都必须一致。

  

例如：

  

```java

public class Animal {

    //类方法

    public void bark() {

        System.out.println("动物叫！");

    }

}

public class Dog extends Animal {

       //重写父类的bark方法

        public void bark() {

        System.out.println("汪！汪！汪！");

    }

}

```

  

写个测试类来看看输出结果：

  

```java

public class Test {

    public static void main(String args[]) {

        Animal a = new Animal(); // Animal 对象

        Dog d = new Dog();   // Dog 对象

  

        Animal b = new Dog(); // Dog 对象,向上转型为Animal类型，具体会在后面的内容进行详解

  

        a.bark();// 执行 Animal 类的方法

        d.bark();//执行 Dog 类的方法

        b.bark();//执行 Dog 类的方法

    }

}

```

  

编译运行：

  

```bash

$ javac Test.java Dog.java Animal.java

$ java Test

动物叫！

汪！汪！汪！

汪！汪！汪！

```

  

## 多态  

  

---

  

多态是指允许不同类的对象对同一消息做出响应。即同一消息可以根据发送对象的不同而采用多种不同的行为方式。多态也称作动态绑定（dynamic binding），是指在执行期间判断所引用对象的实际类型，根据其实际的类型调用其相应的方法。

  

通俗地讲，只通过父类就能够引用不同的子类，这就是多态，我们只有在运行的时候才会知道引用变量所指向的具体实例对象。

  

#### 多态的实现条件

  

**Java 实现多态有三个必要条件：继承、重写和向上转型（即父类引用指向子类对象）。**

  

只有满足上述三个条件，才能够在同一个继承结构中使用统一的逻辑实现代码处理不同的对象，从而达到执行不同的行为。

  

#### 多态的实现方式

  

Java 中多态的实现方式：继承父类进行方法重写，抽象类和抽象方法，接口实现。

  

## 向上转型

  

---

  

理解多态必须要明白什么是"向上转型"，比如，一段代码如下，Dog 类是 Animal 类的子类：

  

```java

Animal a = new Animal();  //a是父类的引用指向的是本类的对象

  

Animal b = new Dog(); //b是父类的引用指向的是子类的对象

```

  

在这里，可以认为由于 Dog 继承于 Animal，所以 Dog 可以自动向上转型为 Animal，所以 `b` 是可以指向 Dog 实例对象的。

  

> 注：不能使用一个子类的引用去指向父类的对象，因为子类对象中可能会含有父类对象中所没有的属性和方法。

  

如果定义了一个指向子类对象的父类引用类型，那么它除了能够引用父类中定义的所有属性和方法外，还可以使用子类强大的功能。但是对于只存在于子类的方法和属性就不能获取。

  

新建一个 `Test.java`，例如：

  

```java

class Animal {

    //父类方法

    public void bark() {

        System.out.println("动物叫！");

    }

}

  

class Dog extends Animal {

  

    //子类重写父类的bark方法

    public void bark() {

        System.out.println("汪、汪、汪！");

    }

    //子类自己的方法

    public void dogType() {

        System.out.println("这是什么品种的狗？");

    }

}

  
  

public class Test {

  

    public static void main(String[] args) {

        Animal a = new Animal();

        Animal b = new Dog();

        Dog d = new Dog();

  

        a.bark();

        b.bark();

        //b.dogType();

        //b.dogType()编译不通过

        d.bark();

        d.dogType();

    }

  

}

```

  

编译运行：

  

```bash

$ javac Test.java

$ java Test

动物叫！

汪、汪、汪！

汪、汪、汪！

这是什么品种的狗？

```

  

在这里，由于 `b` 是父类的引用，指向子类的对象，因此不能获取子类的方法（`dogType()` 方法）, 同时当调用 `bark()` 方法时，由于子类重写了父类的 `bark()` 方法，所以调用子类中的 `bark()` 方法。

  

**因此，向上转型，在运行时，会遗忘子类对象中与父类对象中不同的方法，也会覆盖与父类中相同的方法——重写（方法名，参数都相同）。**  

  

## 抽象类  

  

---

  
  

在定义类时，前面加上 `abstract` 关键字修饰的类叫抽象类。

  

抽象类中有抽象方法，这种方法是不完整的，仅有声明而没有方法体。抽象方法声明语法如下：

  

```java

abstract void f();  //f()方法是抽象方法

```

  

那我们什么时候会用到抽象类呢？

  

1. 在某些情况下，某个父类只是知道其子类应该包含怎样的方法，但无法准确知道这些子类如何实现这些方法。也就是说抽象类是约束子类必须要实现哪些方法，而并不关注方法如何去实现。

2. 从多个具有相同特征的类中抽象出一个抽象类，以这个抽象类作为子类的模板，从而避免了子类设计的随意性。

  

所以由上可知，抽象类是限制规定子类必须实现某些方法，但不关注实现细节。

  

那抽象类如何用代码实现呢，它的规则如下：

  

1. 用 `abstract` 修饰符定义抽象类。

2. 用 `abstract` 修饰符定义抽象方法，只用声明，不需要实现。

3. 包含抽象方法的类就是抽象类。

4. 抽象类中可以包含普通的方法，也可以没有抽象方法。

5. 抽象类的对象不能直接创建，通常是定义引用变量指向子类对象。

  

我们来写一写代码吧！

  

1、在 `home/project/` 目录下创建一个抽象类 `TelePhone.java`。

  

2、填写需要子类实现的抽象方法。

  

```java

//抽象方法

public abstract class TelePhone {

    public abstract void call();  //抽象方法,打电话

    public abstract void message(); //抽象方法，发短信

}

```

  

3、构建子类，并实现抽象方法。新建一个 `CellPhone.java`。

  

```java

public class CellPhone extends TelePhone {

  

    @Override

    public void call() {

        System.out.println("我可以打电话！");

    }

  

    @Override

    public void message() {

        System.out.println("我可以发短信！");

    }

  

    public static void main(String[] args) {

        CellPhone cp = new CellPhone();

        cp.call();

        cp.message();

    }

  

}

```

  

在 CellPhone 类添加 `main` 方法测试运行结果。

  

编译运行：

  

```bash

$ javac CellPhone.java TelePhone.java

$ java CellPhone

  

我可以打电话！

我可以发短信！

```

  

## 接口  

  

---

  

接口用于描述类所具有的功能，而不提供功能的实现，功能的实现需要写在实现接口的类中，并且该类必须实现接口中所有的未实现方法。

  

接口的声明语法格式如下：

  

```java

修饰符 interface 接口名称 [extends 其他的接口名] {

        // 声明变量

        // 抽象方法

}

```

  

如声明一个 Animal 接口：

  

```java

// Animal.java

interface Animal {

        //int x;

        //编译错误,x需要初始化，因为是 static final 类型

        int y = 5;

        public void eat();

        public void travel();

}

```

  

**注意：**

  

在 Java8 中：

  

- 接口不能用于实例化对象。

- 接口中方法只能是抽象方法、`default` 方法、静态方法。

- 接口成员是 `static final` 类型。

- 接口支持多继承。

  

在 Java9 中，接口可以拥有私有方法和私有静态方法，但是只能被该接口中的 `default` 方法和静态方法使用。

  

多继承实现方式：

  

```java

修饰符 interface A extends 接口1，接口2{

  

}

  

修饰符 class A implements 接口1，接口2{

  

}

```

  

实现上面的接口：

  

```java

// Cat.java

public class Cat implements Animal{

  

     public void eat(){

         System.out.println("Cat eats");

     }

  

     public void travel(){

         System.out.println("Cat travels");

     }

     public static void main(String[] args) {

        Cat cat = new Cat();

        cat.eat();

        cat.travel();

    }

}

```

  

编译运行：

  

```bash

$ javac Cat.java Animal.java

$ java Cat

Cat eats

Cat travels

```

  

## 内部类  

  

---

  

将一个类的定义放在另一个类的定义内部，这就是内部类。而包含内部类的类被称为外部类。

  

内部类的主要作用如下：

  

1. 内部类提供了更好的封装，可以把内部类隐藏在外部类之内，不允许同一个包中的其他类访问该类

2. 内部类的方法可以直接访问外部类的所有数据，包括私有的数据

3. 内部类所实现的功能使用外部类同样可以实现，只是有时使用内部类更方便

4. 内部类允许继承多个非接口类型（具体将在以后的内容进行讲解）

  

> 注：内部类是一个编译时的概念，一旦编译成功，就会成为完全不同的两类。对于一个名为 outer 的外部类和其内部定义的名为 inner 的内部类。编译完成后出现 `outer.class` 和 `outer$inner.class` 两类。所以内部类的成员变量 / 方法名可以和外部类的相同。

  

我们通过代码来详细学习一下内部类吧！

  

## 成员内部类    

  

----

  

```java

// People.java

//外部类People

public class People {

    private String name = "LiLei";         //外部类的私有属性

    //内部类Student

    public class Student {

        String ID = "20151234";               //内部类的成员属性

        //内部类的方法

        public void stuInfo(){

            System.out.println("访问外部类中的name：" + name);

            System.out.println("访问内部类中的ID：" + ID);

        }

    }

  

    //测试成员内部类

    public static void main(String[] args) {

        People a = new People();     //创建外部类对象，对象名为a

        Student b = a.new Student(); //使用外部类对象创建内部类对象，对象名为b

        // 或者为 People.Student b = a.new Student();

        b.stuInfo();   //调用内部对象的stuInfo方法

    }

}

```

  

编译运行：

  

```bash

$ javac People.java

$ java People

访问外部类中的name：LiLei

访问内部类中的ID：20151234

```

  

成员内部类的使用方法：

  

1. Student 类相当于 People 类的一个成员变量，所以 Student 类可以使用任意访问修饰符。

2. Student 类在 People 类里，所以访问范围在类里的所有方法均可以访问 People 的属性（即内部类里可以直接访问外部类的方法和属性，反之不行）。

3. 定义成员内部类后，必须使用外部类对象来创建内部类对象，即 `内部类 对象名 = 外部类对象.new 内部类();`。

4. 如果外部类和内部类具有相同的成员变量或方法，内部类默认访问自己的成员变量或方法，如果要访问外部类的成员变量，可以使用 `this` 关键字。如上述代码中：`a.this`。

  

> 注：成员内部类不能含有 `static` 的变量和方法，因为成员内部类需要先创建了外部类，才能创建它自己的。    

  

## 静态内部类    

  

---

  

静态内部类通常被称为嵌套类。

  

```java

// People.java

//外部类People

public class People {

    private String name = "LiLei";         //外部类的私有属性

  

/*外部类的静态变量。

Java 中被 static 修饰的成员称为静态成员或类成员。它属于整个类所有，而不是某个对象所有，即被类的所有对象所共享。静态成员可以使用类名直接访问，也可以使用对象名进行访问。

*/

    static String ID = "510xxx199X0724XXXX";

  

    //静态内部类Student

    public static class Student {

        String ID = "20151234";               //内部类的成员属性

        //内部类的方法

        public void stuInfo(){

            System.out.println("访问外部类中的name：" + (new People().name));

            System.out.println("访问外部类中的ID：" + People.ID);

            System.out.println("访问内部类中的ID：" + ID);

        }

    }

  

    //测试成员内部类

    public static void main(String[] args) {

        Student b = new Student();   //直接创建内部类对象，对象名为b

        b.stuInfo();                 //调用内部对象的suInfo方法

    }

}

```

  

编译运行：

  

```bash

$ javac People.java

$ java People

访问外部类中的name：LiLei

访问外部类中的ID：510xxx199X0724XXXX

访问内部类中的ID：20151234

```

  

静态内部类是 `static` 修饰的内部类，这种内部类的特点是：

  

1. 静态内部类不能直接访问外部类的非静态成员，但可以通过 `new 外部类().成员` 的方式访问。

2. 如果外部类的静态成员与内部类的成员名称相同，可通过 `类名.静态成员` 访问外部类的静态成员；如果外部类的静态成员与内部类的成员名称不相同，则可通过 `成员名` 直接调用外部类的静态成员。

3. 创建静态内部类的对象时，不需要外部类的对象，可以直接创建 `内部类 对象名 = new 内部类();`

  

## 局部内部类    

  

---

  

> 局部内部类，是指内部类定义在方法和作用域内。

>

> 局部内部类访问外部类的成员步骤：直接访问

>

> 外部类访问局部类步骤：首先创建对象，再访问（PS：不能超出作用域范围）

  

例如：

  

```java

// People.java

//外部类People

public class People {

    //定义在外部类中的方法内：

    public void peopleInfo() {

        final String sex = "man";  //外部类方法中的常量

        class Student {

            String ID = "20151234"; //内部类中的常量

            public void print() {

                System.out.println("访问外部类的方法中的常量sex：" + sex);

                System.out.println("访问内部类中的变量ID:" + ID);

            }

        }

        Student a = new Student();  //创建方法内部类的对象

        a.print();//调用内部类的方法

    }

    //定义在外部类中的作用域内

    public void peopleInfo2(boolean b) {

        if(b){

            final String sex = "man";  //外部类方法中的常量

            class Student {

                String ID = "20151234"; //内部类中的常量

                public void print() {

                    System.out.println("访问外部类的方法中的常量sex：" + sex);

                    System.out.println("访问内部类中的变量ID:" + ID);

                }

            }

            Student a = new Student();  //创建方法内部类的对象

            a.print();//调用内部类的方法

        }

    }

    //测试方法内部类

    public static void main(String[] args) {

        People b = new People(); //创建外部类的对象

        System.out.println("定义在方法内：===========");

        b.peopleInfo();  //调用外部类的方法

        System.out.println("定义在作用域内：===========");

        b.peopleInfo2(true);

    }

}

```

  

编译运行：

  

```bash

$ javac People.java

$ java People

定义在方法内：===========

访问外部类的方法中的常量sex：man

访问内部类中的变量ID:20151234

定义在作用域内：===========

访问外部类的方法中的常量sex：man

访问内部类中的变量ID:20151234

```

  

局部内部类也像别的类一样进行编译，但只是作用域不同而已，只在该方法或条件的作用域内才能使用，退出这些作用域后无法引用的。    

  

## 匿名内部类    

  

---

  

匿名内部类，顾名思义，就是没有名字的内部类。正因为没有名字，所以匿名内部类只能使用一次，它通常用来简化代码编写。但使用匿名内部类还有个前提条件：必须继承一个父类或实现一个接口。

  

例如：

  

```java

// Outer.java

public class Outer {

  

    public Inner getInner(final String name, String city) {

        return new Inner() {

            private String nameStr = name;

            public String getName() {

                return nameStr;

            }

        };

    }

  

    public static void main(String[] args) {

        Outer outer = new Outer();

        Inner inner = outer.getInner("Inner", "NewYork");

        System.out.println(inner.getName());

    }

}

interface Inner {

    String getName();

}

```

  

运行结果：

  

```sh

Inner

```

  

再例如：

  

```java

//TODO 通过接口

public class ExamPle_06 {

    public static void main(String[] args) {

        IA Animal = new IA() {

  

            @Override

            public void Run() {

                System.out.println("我会跑....");

            }

        };

        Animal.Run();

    }

}

  

//TODO 声明一个接口

interface IA {

    void Run();

}

```

  

运行结果：

  

```java

我会跑....

```

  

匿名内部类是**不能加访问修饰符**的。要注意的是，new 匿名类，这个类是要先定义的, 如果不先定义，编译时会报错该类找不到。

  

同时，在上面的例子中，当所在的方法的形参需要在内部类里面使用时，该形参必须为 `final`。这里可以看到形参 `name` 已经定义为 `final` 了，而形参 `city` 没有被使用则不用定义为 `final`。

  

然而，因为匿名内部类没名字，是用默认的构造方法的，无参数的，如果需要该类有带参数的构造方法，示例如下：

  

```java

public Inner getInner(final String name, String city) {

  return new Inner(name, city) {

    private String nameStr = name;

  

    public String getName() {

      return nameStr;

    }

  };

}

```

  

注意这里的形参 `city`，由于它没有被匿名内部类直接使用，而是被抽象类 Inner 的构造方法所使用，所以不必定义为 `final`。

  

#### 练习

  

> 题目要求

  

![[ASLant_Images/51d9ae2b9163211345f9723fa3057566_MD5.jpg]]

  

且必须包含以下代码：

  

![[ASLant_Images/7551df82e727a3c11636b24831f173b2_MD5.jpg]]

  

> Answer

  

```java

public class Example {

    public static void main(String[] args) {

        PhoneClass Ph = new PhoneClass();

        Ph.Clock(new Bell() { //TODO 匿名内部类

            @Override

            public void Ring() {

                System.out.println("小伙伴上课了");

            }

        }); //注意分号！

    }

}

//TODO 定义一个Bell接口

interface Bell {

    void Ring();

}

  

class PhoneClass {

    public void Clock(Bell c) {

        c.Ring();

    }

}

```

  

## Package 包    

  

---

  

为了更好地组织类，Java 提供了包机制，用于区别类名的命名空间。

  

**包的作用**

  

- 把功能相似或相关的类或接口组织在同一个包中，方便类的查找和使用。

- 包采用了树形目录的存储方式。同一个包中的类名字是不同的，不同的包中的类的名字是可以相同的，当同时调用两个不同包中相同类名的类时，应该加上包名加以区别。

- 包也限定了访问权限，拥有包访问权限的类才能访问某个包中的类。

  

定义包语法：

  

```java

package 包名

//注意：必须放在源程序的第一行，包名可用"."号隔开

```

  

例如：

  

```java

//在定义文件夹的时候利用"/"来区分层次

//包中用"."来分层

package com.shiyanlou.java

```

  

不仅是我们这样利用包名来区分类，系统也是这样做的。

  

![[ASLant_Images/41fd2404dc1f62bc457b2d56cd923d99_MD5.jpg]]

  

**如何在不同包中使用另一个包中的类？**

  

使用 `import` 关键字。比如要导入包 `com.shiyanlou` 下 `People` 这个类，`import com.shiyanlou.People;`。同时如果 `import com.shiyanlou.*;` 这是将包下的所有文件都导入进来，`*` 是通配符。

  

**包的命名规范是全小写字母拼写**。