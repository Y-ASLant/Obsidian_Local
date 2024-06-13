#  安装 GCC
### Debian 系
1. 首先更新软件包
```sh
apt-get update
```

2. 安装 GCC
```sh
apt-get install gcc
```

### Redhat 系
1. 首先更新软件包
```sh
dnf update
```

2. 安装 GCC
```sh
dnf -y install gcc
```

> [!BUG]- 可能遇到的问题
![[ASLant_Files/80e37f956d4923d54c77200f3279e84c_MD5.jpg]]
[](../ASLant_Files/80e37f956d4923d54c77200f3279e84c_MD5.jpg)en: 80e37f956d4923d54c77200f3279e84c_MD5.jpg]]
[](../ASLant_Files/80e37f956d4923d54c77200f3279e84c_MD5.jpg)
```

![[../ASLant_Files/f738620db30c677c1ed857bf77ab01f9_MD5.jpg]]
### 汇编
```sh
gcc -S xxx.i -o xxx.s
```

![[../ASLant_Files/ac6798fd34c53956f6248a5bd185b7e9_MD5.jpg]]
### 编译
```sh
gcc -c xxx.s -o xxx.o
```

![[../ASLant_Files/3da25bf7c5399ad23d3cac9f1f659bb3_MD5.jpg]]
### 链接
```sh
gcc xxx.o -o xxx
```

# 单文件编译

### 输出 Hello World

```sh
vim hello.c
```

```c
#include <stdio.h>

int main(int argc, char *argv[])
{
    printf("Hello WSL");
    return 0;
}
```

```sh
gcc -o hello hello.c
```

```sh
./hello
```

# 多文件编译

```sh
gcc -o abc main.c add.c swap.c
```
或
```sh
gcc main.c add.c swap.c -o abc
```

![[../ASLant_Files/732758c194ac05e2be5c874649099129_MD5.jpg]]