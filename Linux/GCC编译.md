> [!INFO] GCC
> GCC 是 Linux 下的编译工具集，是 GNU Compiler Collection 的缩写，包含 gcc、g++ 等编译器。
> 这个工具集不仅包含编译器，还包含其他工具集，例如 ar、nm 等。GCC 工具集不仅能编译 C/C++语言，其他例如 Objective-C、Pascal、Fortran、Java、Ada 等语言均能进行编译。
> GCC 在可以根据不同的硬件平台进行编译，即能进行交叉编译，在 A 平台上编译 B 平台的程序，支持常见的 X86、ARM、PowerPC、mips 等，以及 Linux、Windows 等软件平台。

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

![[../ASLant_Files/f738620db30c677c1ed857bf77ab01f9_MD5.jpg]]

# 工作流程

> [!NOTE] 
> GCC 编译器对程序的编译，分为 4 个阶段：预处理（预编译）、编译和优化、汇编和链接。

### 1. 预处理

 **预处理（Preprocessing）**：
   - **功能**：处理所有的预处理指令（以 `#` 开头的指令，如 `#include`、`#define` 等），并展开所有的宏。还会移除所有的注释。
   - **命令**：`gcc -E source.c -o source.i`
   - **输出**：生成一个扩展名为 `.i` 的文件，它是经过预处理的源代码。

```sh
gcc -E xxx.c -o xxx.i
```

![[../ASLant_Files/2024-06-18-13-38-30.png]]
### 2. 编译

**编译（Compilation）**：
   - **功能**：将预处理后的代码转换为汇编代码。这一步不生成机器代码，只生成汇编代码。
   - **命令**：`gcc -S source.i -o source.s`
   - **输出**：生成一个扩展名为 `.s` 的文件，它是对应的汇编代码。

```sh
gcc -S xxx.i -o xxx.s
```

![[../ASLant_Files/2024-06-18-13-40-10.png]]

### 3. 汇编

**汇编（Assembly）**：
   - **功能**：将汇编代码转换为机器代码（二进制代码），生成目标文件。这一步生成的是可重定位的目标文件，还不是最终的可执行文件。
   - **命令**：`gcc -c source.s -o source.o`
   - **输出**：生成一个扩展名为 `.o` 的文件，它是目标文件。

```sh
gcc -c xxx.s -o xxx.o
```

![[../ASLant_Files/2024-06-18-13-42-37.png]]

### 4. 链接

 **链接（Linking）**：
   - **功能**：将目标文件和所需的库链接在一起，生成最终的可执行文件。在这个阶段，链接器会解析所有的符号，处理外部引用，并生成最终的可执行文件。
   - **命令**：`gcc source.o -o executable`
   - **输出**：生成一个可执行文件，通常没有扩展名。

```sh
gcc xxx.o -o xxx
```

![[../ASLant_Files/2024-06-18-13-43-14.png]]

##### 运行
![[../ASLant_Files/2024-06-18-13-43-40.png]]
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

