## 类的五大成员

> 属性

>

> 方法

>

> 构造器(构造方法)

>

> 代码块

>

> 内部类

  

## Arrays

  

> Arrays 类包含用于操作数组的各种方法（例如排序和搜索）。还包含一个静态工厂，允许将数组转为 List。

  

#### Arrays 常用方法

  

| 方法                                     | 描述                             |

| :--------------------------------------- | :------------------------------- |

| <T> List<T> asList(T... a)               | 返回由指定数组构造的 List        |

| void sort(Object[] a)                    | 对数组进行排序                   |

| void fill(Object[] a, Object val)        | 为数组的所有元素都赋上相同的值   |

| boolean equals(Object[] a, Object[] a2)  | 检查两个数组是否相等             |

| int binarySearch(Object[] a, Object key) | 对排序后的数组使用二分法查找数据 |

  

#### 实例

  

创建一个 `ArraysDemo.java`  

  

```java

import java.util.Arrays;

import java.util.Random;

  

public class ArraysDemo {

    public static void main(String[] args) {

        int[] arr = new int[10];

        //将数组元素都设为9

        Arrays.fill(arr, 9);

        System.out.println("fill:" + Arrays.toString(arr));

        Random random = new Random();

        for (int i = 0; i < arr.length; i++) {

            //使用100以内的随机数赋值数组

            arr[i] = random.nextInt(101);

        }

        //重新赋值后的数组

        System.out.println("重新赋值：" + Arrays.toString(arr));

        //将索引为5的元素设为50

        arr[5] = 50;

        //排序

        Arrays.sort(arr);

        //排序后的数组

        System.out.println("sort排序后：" + Arrays.toString(arr));

        //查找50的位置

        int i = Arrays.binarySearch(arr, 50);

        System.out.println("值为50的元素索引："+i);

        //复制一份新数组

        int[] newArr = Arrays.copyOf(arr, arr.length);

        //比较

        System.out.println("equals:"+Arrays.equals(arr, newArr));

    }

}
```
  

编译运行：

  

```bash

$ javac ArraysDemo.java

$ java ArraysDemo

fill:[9, 9, 9, 9, 9, 9, 9, 9, 9, 9]

重新赋值：[69, 83, 40, 58, 94, 42, 2, 53, 43, 83]

sort排序后：[2, 40, 43, 50, 53, 58, 69, 83, 83, 94]

值为50的元素索引：3

equals:true

```

  

#### 练习

  

你需要完成以下需求：

  

- 使用 Arrays 将数组 [6, 17, 92, 32, 58, 22, 84, 66, 36, 33] 进行排序。

- 找出排序后的 33 所在的位置。

- 测试一下如果不排序能否找到值 33？

  

#### Answer

  

```java

import java.util.Arrays;//导入Arrays包

  

public class ArraysTest {

    public static void main(String[] args) {

        int[] arr = {6, 17, 92, 32, 58, 22, 84, 66, 36, 33};

        Arrays.sort(arr);//从小到大进行排序

        System.out.println(Arrays.binarySearch(arr, 33));//二分搜索

    }

}

```

  

## StringBuilder

  

StringBuilder 类是可变的。它是 String 的对等类，它可以增加和编写字符的可变序列，并且能够将字符插入到字符串中间或附加到字符串末尾（当然是不用创建其他对象的）。

  

StringBuilder 的构造方法：

  

| 构造方法                        | 说明                                                         |

| ------------------------------- | ------------------------------------------------------------ |

| StringBuilder()                 | 构造一个其中不带字符的 StringBuilder，其初始容量为 16 个字符 |

| StringBuilder(CharSequence seq) | 构造一个 StringBuilder，它包含与指定的 CharSequence 相同的字符 |

| StringBuilder(int capacity)     | 构造一个具有指定初始容量的 StringBuilder                     |

| StringBuilder(String str)       | 并将其内容初始化为指定的字符串内容                           |

  

StringBuilder 类的常用方法：

  

| 方法                                    | 返回值        | 功能描述                                                     |

| --------------------------------------- | ------------- | ------------------------------------------------------------ |

| insert(int offsetm,Object obj)          | StringBuilder | 在 offsetm 的位置插入字符串 obj                              |

| append(Object obj)                      | StringBuilder | 在字符串末尾追加字符串 obj                                   |

| length()                                | int           | 确定 StringBuilder 对象的长度                                |

| setCharAt(int index,char ch)            | void          | 使用 ch 指定的新值设置 index 指定的位置上的字符              |

| toString()                              | String        | 转换为字符串形式                                             |

| reverse()                               | StringBuilder | 反转字符串                                                   |

| delete(int start, int end)              | StringBuilder | 删除调用对象中从 start 位置开始直到 end 指定的索引（end-1）位置的字符序列 |

| replace(int start, int end, String str) | StringBuilder | 使用一组字符替换另一组字符。将用替换字符串从 start 指定的位置开始替换，直到 end 指定的位置结束 |

  

上面的方法中我们选择几个，来写写代码吧：

  

在 `/home/project/` 目录下新建 `StringBuilderTest.java`。

  

```java

public class StringBuilderTest {

  

    public static void main(String[] args){

        //定义和初始化一个StringBuilder类的字串s

        StringBuilder s = new StringBuilder("I");

        //在s后面添加字串" java"

        s.append(" java");

        //在s[1]的位置插入字串

        s.insert(1, " love");

        String t = s.toString(); //转为字符串

        System.out.println(t);

    }

}

```

  

输出结果为： I love java。

  

在这里只介绍了 StringBuilder 类常用的方法，其他方法可参照 JDK 文档。    

  
  

## 向上转型、向下转型(强制转换)

  

```java

public class ExamPle_01 {

    public static void main(String[] args) {

        //TODO 向上转型  父类指向子类实例

        Animal c = new Cat();

        Animal d = new Dog();

        c.eat();

        d.eat();

        //c.run();//TODO 父类没有的方法 不能用

  

        //TODO 向下转型、强制转型

        Cat c1 = (Cat) c;

        Dog d1 = (Dog) d;

        c1.eat();

        d1.eat();

  

        //TODO instanceof

        if (d instanceof Cat) {

            System.out.println("可以转型");

        }

        else {

            System.out.println("不可以转型");

        }

    }

}

  

class Animal {

    void eat() {

  

    }

  

}

  

class Cat extends Animal {

    void eat() {

        System.out.println("猫要吃鱼~");

    }

  

    void run() {

        System.out.println("猫要跑~");

    }

}

  

class Dog extends Animal {

    void eat() {

        System.out.println("修狗也要吃鱼~");

    }

  

    void run() {

        System.out.println("修狗也要跑~");

    }

}

```

  

## Date

  

Date 类表示日期和时间，里面封装了操作日期和时间的方法。Date 类经常用来获取系统当前时间。

  

来看看类 Date 中定义的未过时的构造方法：

  

| 构造方法        | 说明                                                         |

| --------------- | ------------------------------------------------------------ |

| Date()          | 构造一个 Date 对象并对其进行初始化以反映当前时间             |

| Date(long date) | 构造一个 Date 对象，并根据相对于 GMT 1970 年 1 月 1 日 00:00:00 的毫秒数对其进行初始化 |

  

#### 实例

  

```java

import java.text.SimpleDateFormat;//格式化时间

import java.util.Date;

  

public class DateDemo {

    public static void main(String[] args) {

        String strDate, strTime;

        Date objDate = new Date();

        System.out.println("今天的日期是：" + objDate);

        long time = objDate.getTime();

        System.out.println("自1970年1月1日起以毫秒为单位的时间（GMT）：" + time);

        strDate = objDate.toString();

        //提取 GMT 时间

        strTime = strDate.substring(11, (strDate.length() - 4));

        //按小时、分钟和秒提取时间

        strTime = "时间：" + strTime.substring(0, 8);

        System.out.println(strTime);

        //格式化时间

        SimpleDateFormat formatter = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");

        System.out.println(formatter.format(objDate));

    }

}

```

  

编译运行：

  

```bash

$ javac DateDemo.java

$ java DateDemo

今天的日期是：Tue May 09 16:43:45 CST 2023

自1970年1月1日起以毫秒为单位的时间（GMT）：1683621825774

时间：16:43:45

2023-05-09 16:43:45

```

  

Date 类的很多方法自 JDK 1.1 开始就已经过时了。

  

## Math

  

`Math` 类在 `java.lang` 包中，包含用于执行基本数学运算的方法，如初等指数、对数、平方根和三角函数。

  

常见方法：

  

| 方法                    | 返回值                                         | 功能描述                                                     |

| :---------------------- | :--------------------------------------------- | :----------------------------------------------------------- |

| sin(double numvalue)    | double                                         | 计算角 numvalue 的正弦值                                     |

| cos(double numvalue)    | double                                         | 计算角 numvalue 的余弦值                                     |

| acos(double numvalue)   | double                                         | 计算 numvalue 的反余弦                                       |

| asin(double numvalue)   | double                                         | 计算 numvalue 的反正弦                                       |

| atan(double numvalue)   | double                                         | 计算 numvalue 的反正切                                       |

| pow(double a, double b) | double                                         | 计算 a 的 b 次方                                             |

| sqrt(double numvalue)   | double                                         | 计算给定值的正平方根                                         |

| abs(int numvalue)       | int                                            | 计算 int 类型值 numvalue 的绝对值，也接收 long、float 和 double 类型的参数 |

| ceil(double numvalue)   | double                                         | 返回大于等于 numvalue 的最小整数值                           |

| floor(double numvalue)  | double                                         | 返回小于等于 numvalue 的最大整数值                           |

| max(int a, int b)       | int                                            | 返回 int 型 a 和 b 中的较大值，也接收 long、float 和 double 类型的参数 |

| min(int a, int b)       | int                                            | 返回 a 和 b 中的较小值，也可接受 long、float 和 double 类型的参数 |

| rint(double numvalue)   | double                                         | 返回最接近 numvalue 的整数值                                 |

| round(T arg)            | arg 为 double 时返回 long，为 float 时返回 int | 返回最接近 arg 的整数值                                      |

| random()                | double                                         | 返回带正号的 double 值，该值大于等于 0.0 且小于 1.0          |

  

上面都是一些常用的方法，如果同学们还会用到极坐标、对数等，就去查一查手册吧。

  

#### 实例

  

```java

public class MathDemo {

    public static void main(String[] args) {

        System.out.println(Math.abs(-12.7));

        System.out.println(Math.ceil(12.7));

        System.out.println(Math.rint(12.4));

        System.out.println(Math.random());

        System.out.println("sin30 = " + Math.sin(Math.PI / 6));

        // 计算30°的正弦值，参数是用弧度表示的角，即π的六分之一

        System.out.println("cos30 = " + Math.cos(Math.PI / 6));

        // 计算30°的余弦值，这些计算三角函数的方法，其参数和返回值的类型都为double

        System.out.println("tan30 = " + Math.tan(Math.PI / 6));

        // 计算30°的正切值

    }

}

```

  

编译运行：

  

```bash

$ javac MathDemo.java

$ java MathDemo

12.7

13.0

12.0

0.8011998172263968

sin30 = 0.49999999999999994

cos30 = 0.8660254037844387

tan30 = 0.5773502691896257

```

  

#### 练习

  

你需要完成以下需求：

  

- 使用 `Math.random()` 生成两个随机数 `a` 和 `b`。

- 求出两个随机数中的较大值。

- 只能使用 Math 类中的方法。

  

#### Answer

  

```java

import java.lang.Math;

  

public class ExamPle_09 {

    public static void main(String[] args) {

        double Num_1 = Math.random();

        double Num_2 = Math.random();

        System.out.println("Num_1的值是：" + Num_1);

        System.out.println("Num_2的值是：" + Num_2);

        System.out.println("--------------------");

        System.out.println("最大值是：" + Max_Te(Num_1, Num_2));//方法一

        System.out.println("最大值是：" + Math.max(Num_1, Num_2));//方法二 直接调用自带的函数

    }

  

    static double Max_Te(double i, double j) {

        double Max = i;

        if (Max < j) {

            Max = j;

        }

        return Max;

    }

}

```

  

运行：

  

```java

Num_1的值是：0.27315468682640576

Num_2的值是：0.3135301690933455

------------------------------

最大值是：0.3135301690933455

最大值是：0.3135301690933455

```

  

## System

  

System 类提供了以下功能：

  

- 标准输入，标准输出和错误输出流；

- 访问外部定义的属性和环境变量；

- 加载文件和库的方法；

- 以及用于快速复制数组的实用方法。

  

> System 不可以被实例化，只可以使用其静态方法。

  

```java

//从指定的源数组中复制一个数组，从源数组指定的位置开始，到目标数组指定的位置

public static void arraycopy(Object src,int srcPos, Object dest,int desPos,int length)

//返回以毫秒为单位的当前时间(从1970年到现在的毫秒数)

public static long currentTimeMillis()

//终止当前正在运行的Java虚拟机，status为 0时退出

public static void exit(int status)

//  运行垃圾收集器

public static void gc()

// 取得当前系统的全部属性

public static Properties getProperties()

//获取指定键的系统属性

public static String  getProperty(String key)

```

  

#### 实例

  

```java

public class ExamPle_10 {

    public static void main(String[] args) {

        int[] a = {7, 8, 9, 10, 11};

        int[] b = {1, 2, 3, 4, 5, 6};

        //从数组a的第二个元素开始，复制到b数组的第三个位置 复制的元素长度为3

        System.arraycopy(a, 1, b, 2, 3);

        //输出结果

        System.out.println(Arrays.toString(b));

        System.out.println("当前时间：" + System.currentTimeMillis());

        System.out.println("java版本信息：" + System.getProperty("java.version"));

        //运行垃圾收集器

        System.gc();

        //退出

        System.exit(0);

    }

  

}

```

  

编译运行：

  

```bash

$ javac SystemDemo.java

$ java SystemDemo

[1, 2, 8, 9, 10, 6]

当前时间：1683634141456

java版本信息：19

```

  

#### 练习

  

你需要完成以下需求：

  

- 获取 Java 的安装目录 (`java.home`)。

- 练习 `System.arraycopy` 方法（自己随便复制两个数组）。

  

#### Answer

  

```JAVA

import java.util.Arrays;

  

public class SystemTest {

    public static void main(String[] args) {

        int[] a = {7, 8, 9, 10, 11};

        int[] b = {1, 2, 3, 4, 5, 6};

        //从数组a的第二个元素开始，复制到b数组的第三个位置 复制的元素长度为3

        System.arraycopy(a, 1, b, 2, 3);

        //输出结果

        System.out.println(Arrays.toString(b));

        System.out.println("java安装路径：" + System.getProperty("java.home"));

    }

}

```

  

运行：

  

```java

C:\JDK\jdk-19

```

  

## Random随机数

  

```java

import java.util.Random;

  

public class RandomDemo {

    public static void main(String[] args) {

        Random random = new Random();

        //随机生成一个整数 int范围

        System.out.println(random.nextInt());

        //生成 [0,n] 范围的整数  设n=100

        System.out.println(random.nextInt(100 + 1));

        //生成 [0,n) 范围的整数  设n=100

        System.out.println(random.nextInt(100));

        //生成 [m,n] 范围的整数  设n=100 m=40

        System.out.println((random.nextInt(100 - 40 + 1) + 40));

        //随机生成一个整数 long范围

        System.out.println(random.nextLong());

        //生成[0,1.0)范围的float型小数

        System.out.println(random.nextFloat());

        //生成[0,1.0)范围的double型小数

        System.out.println(random.nextDouble());

    }

}

```

  

编译运行：

  

```bash

$ javac RandomDemo.java

$ java RandomDemo

272128541

67

93

66

-23177167376469717070.93104035

0.20044632645967309

```

  

#### 练习

  

- 从控制台中获取 Int 数据 `m`，`n` `(m < n)`，先输入 `m`，后输入 `n`。

- 输出一个 `[m,n]` 之间的随机数。

  

示例：

  

```bash

输入：

    30

    40

输出：

    32

```

  

#### Answer

  

```java

import java.util.Random;

import java.util.Scanner;

  

public class ExamPle_13 {

    public static void main(String[] args) {

        Scanner Scan = new Scanner(System.in);

        Random random = new Random();

        int m = Scan.nextInt();

        int n = Scan.nextInt();

        if (n > m) {

            System.out.println((random.nextInt(n - m + 1) + m));

        } else

            System.out.println("输入数据有错误！");

    }

  

}

```

  

运行：

  

```java

30

40

33

```