# 使用内存

C语言是一种低级语言，可以轻松访问内存位置并执行与内存相关的操作。

例如，scanf() 函数将用户输入的值放在变量的位置或地址处。这是通过使用＆符号(取地址符号)实现的。

例如:

```c
int num;
printf("请输入一个整数");
scanf("%d", &num);
printf("%d", num);
```

`＆num`是变量`num`的地址。内存地址以**十六进制**数给出。

以下程序显示变量i和k的内存地址：

```c
#include<stdio.h>
void test(int k);

int main() {
  int i = 0;
  printf("变量i的地址是 %x\n", &i);
  test(i);
  printf("变量i的地址是 %x\n", &i);
  test(i);
  return 0;
}

void test(int k) {
  printf("变量k的地址是 %x\n", &k);
}
```

在printf语句中，％x是十六进制格式说明符。

程序输出因运行会有所不同，但看起来类似于：

```C
变量i的地址是 61fe1c
变量k的地址是 61fdf0
变量i的地址是 61fe1c
变量k的地址是 61fdf0
```

从变量声明到变量作用域结束的地址都保持不变。
# 什么是指针？

指针在C语言编程中非常重要，因为它们使你可以轻松地处理内存位置。

**指针是数组，字符串以及其他数据结构和算法的基础。**

指针是一个变量，其中包含另一个变量的地址。换句话说，它“指向”分配给变量的位置，并且可以间接访问该变量。

指针使用*符号声明，语法如下：

```c
指针数据类型 *标识符
```

实际的指针数据类型是十六进制数，但是在声明指针时，必须指出它将指向的数据类型。

星号 * 声明一个指针，并应出现在用于指针变量的标识符旁边。

以下程序演示了变量，指针和地址：

```c
int j = 63;
int *p = NULL;
p = &j;
printf("The address of j is %x\n", &j);
printf("p contains address %x\n", p);
printf("The value of j is %d\n", j);
printf("p is pointing to the value %d\n", *p);
```

关于此程序，需要注意以下几点：

在将指针分配给有效位置之前，应将其初始化为NULL。

可以使用＆符号为指针分配变量的地址。

要查看指针指向的内容，请再次使用 *，如 *p 中所示。

在这种情况下，* 被称为间接或取消引用运算符。该过程称为取消引用。

程序输出类似于：

```c
The address of j is ff3652cc
p contains address ff3652cc
The value of j is 63
p is pointing to the value 63
```

> 一些算法使用指向指针的指针。这种类型的变量声明使用**，并且可以分配另一个指针的地址，如下所示：
```c
int x = 12;
int *p = NULL
int **ptr = NULL;
p = &x;
ptr = &p;
```
