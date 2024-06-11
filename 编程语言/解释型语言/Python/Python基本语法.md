> [!check] 最后更新于 [[2024-05-19]]
# Python 保留字

> [!BUG] 查看保留字
> ```Python
> # 调用官方库
>  import keyword
>  # 显示Python自带保留字
>  keyword.kwlist
> ```

```Python
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

## 注释

### 单行注释

> [!INFO] Python中单行注释以 **#** 开头

```Pyhton
# 第一个注释 print ("Hello, Python!") # 第二个注释
```

执行以上代码，输出结果为：
```Python
Hello, Python!
```

### 多行注释

> [!INFO] 多行注释可以用多个 # 号，还有 ''' 和 """：

```Pyhton
# 第一个注释
# 第二个注释
 
'''
第三注释
第四注释
'''
 
"""
第五注释
第六注释
"""
print ("Hello, Python!")
```

执行以上代码，输出结果为：
```Python
Hello, Python!
```


## 行与缩进

> [!INFO] Python 最具特色的就是使用缩进来表示代码块，不需要使用大括号 {} 。
**缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。**

### 正确实例

```Python
if True:
    print ("True")
else:
    print ("False")
```

### 错误实例

> [!BUG] 错误原因
> 最后一行语句缩进数的空格数不一致，导致运行错误。

```Python
if True:
    print ("Answer")
    print ("True")
else:
    print ("Answer")
  print ("False")    # 缩进不一致，会导致运行错误
```

> [!BUG ] 执行后
> ```Pyhton
>  File "test. Py", line 6
>  Print ("False")    # 缩进不一致，会导致运行错误
>                                    ^
>  IndentationError: unindent does not match any outer indentation level
>

# 多行语句

> [!INFO] Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠 \ 来实现多行语句

```Python
total = item_one + \
        item_two + \
        item_three
```

在 [], {}, 或 () 中的多行语句，**不需要**使用反斜杠
```Python
total = ['item_one', 'item_two', 'item_three',
        'item_four', 'item_five']
```

# 数字 (Number) 类型

> [!INFO] Python 中数字有四种类型：整数、布尔型、浮点数和复数。
- [*] **Int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python 2 中的 Long。
- [*] **Bool** (布尔), 如 True。
- [*] **Float** (浮点数), 如 1.23、3 E-2
- [*] **Complex** (复数), 如 1 + 2 j、 1.1 + 2.2 j

# 空行

> [!INFO] **空行也是程序代码的一部分**

- [*] 函数之间或类的方法之间用空行分隔，表示一段新的代码的开始。类和函数入口之间也用一行空行分隔，以突出函数入口的开始。
- [*] **空行与代码缩进不同，空行并不是 Python 语法的一部分。**
- [*] 书写时不插入空行，Python 解释器运行也不会出错。但是空行的作用在于分隔两段不同功能或含义的代码，便于日后代码的维护或重构。

# 字符串(String)

- [*] Python 中单引号 ' 和双引号 " 使用完全相同。
- [*] 使用**三引号**(''' 或 """)可以指定一个多行字符串。
- [*] 转义符 \\。
- [*] 反斜杠可以用来转义，使用 r 可以让反斜杠不发生转义。如 **r"this is a line with \\n"** 则 \\n 会显示，并不是换行。
- [*] 按字面意义级联字符串，如 **"this " "is " "string"** 会被自动转换为 **this is string**。
- [*] 字符串可以用 + 运算符连接在一起，用 * 运算符重复。
- [*] Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始。
- [*] Python 中的字符串不能改变。
- [*] Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。
- [*] 字符串切片 str[start:end]，其中 start（包含）是切片开始的索引，end（不包含）是切片结束的索引。
- [*] 字符串的切片可以加上步长参数 step，语法格式如下：str[start:end:step]
```Python
word = '字符串'
sentence = "这是一个句子。"
paragraph = """这是一个段落，
可以由多行组成"""
```
### 实例

```Python
str='123456789'

print(str)                 # 输出字符串
print(str[0:-1])           # 输出第一个到倒数第二个的所有字符
print(str[0])              # 输出字符串第一个字符
print(str[2:5])            # 输出从第三个开始到第六个的字符（不包含）
print(str[2:])             # 输出从第三个开始后的所有字符
print(str[1:5:2])          # 输出从第二个开始到第五个且每隔一个的字符（步长为2）
print(str * 2)             # 输出字符串两次
print(str + '你好')         # 连接字符串
 
print('------------------------------')
 
print('hello\nASLant')      # 使用反斜杠(\)+n转义特殊字符
print(r'hello\nASLant')     # 在字符串前面添加一个 r，表示原始字符串，不会发生转义
```
#### 注意

- [*] **这里的 r 指 raw，即 raw string，会自动将反斜杠转义**
```Python
>>> print('\n')       # 输出空行

>>> print(r'\n')      # 输出 \n
\n
>>>
```
### 输出结果

```Python
123456789
12345678
1
345
3456789
24
123456789123456789
123456789你好
------------------------------
hello
ASLant
hello\nASLant
```

# 等待用户输入
## 实例

- [*] **执行下面的程序在按回车键后就会等待用户输入：**
```Python
input("\n\n按下 enter 键后退出。")
```

以上代码中，\\n\\n 在结果输出前会输出两个新的空行。一旦用户按下 **enter** 键时，程序将退出。

# 同一行显示多条语句

> [!TIP] Python 可以在同一行中使用多条语句，语句之间使用分号 ; 分割，以下是一个简单的实例：

### 实例
```Python
import sys; x = 'ASLant'; sys.stdout.write(x + '\n')
```

### 运行结果
```Python
ASLant
```

# 多个语句构成代码组

<font color="#00b050">缩进相同的一组语句构成一个代码块，我们称之代码组。</font>
像 if、while、def 和 class 这样的复合语句，首行<font color="#0070c0">以关键字开始，以冒号 ( : ) 结束</font>，该行之后的一行或多行代码构成代码组。
我们将<font color="#00b050">首行及后面的代码组称为一个子句(clause)</font>。
### 实例

```Python
if expression : 
   suite
elif expression : 
   suite 
else : 
   suite
```

# print 输出

**print** 默认输出是换行的，如果要实现不换行需要在变量末尾加上 <font color="#00b050">end=""</font>
```Python
x="a"
y="b"
# 换行输出
print( x )
print( y )
 
print('---------')
# 不换行输出
print( x, end=" " )
print( y, end=" " )
print()
```

### 运行结果
```Python
a
b
---------
a b

```

# import 与 from...import

> [!BUG] import
> 在 python 用 import 或者 from... Import 来导入相应的模块。
> 将整个模块 (somemodule) 导入，格式为： import somemodule
### 导入 sys 模块
```Python
import sys
print('================Python import mode==========================')
print ('命令行参数为:')
for i in sys.argv:
    print (i)
print ('\n python 路径为',sys.path)
```

> [!danger] from... Import
> 从某个模块中导入某个函数, 格式为： from somemodule import somefunction
> 从某个模块中导入多个函数, 格式为： from somemodule import firstfunc, secondfunc, thirdfunc
> 将某个模块中的全部函数导入，格式为： from somemodule import *
> 
### 导入 sys 模块的 argv, path 成员
```Python
from sys import argv,path  #  导入特定的成员
 
print('================python from import===================================')
print('path:',path) # 因为已经导入path成员，所以此处引用时不需要加sys.path
```

# Python3 基本数据类型

- [*] Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。
- [*] 在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型。
- [*] 等号（=）用来给变量赋值。
- [*] 等号（=）运算符左边是一个变量名,等号（=）运算符右边是存储在变量中的值。例如：
### 实例
```Python
counter = 100          # 整型变量
miles   = 1000.0       # 浮点型变量
name    = "ASLant"     # 字符串

print (counter)
print (miles)
print (name)
```
### 运行结果
```Python
100
1000.0
ASLant
```
# 多个变量赋值

> [!INFO] Python允许你同时为多个变量赋值。例如：

```PYthon
a = b = c = 1
```

- [*] 以上实例，创建一个整型对象，值为 1，从后向前赋值，三个变量被赋予相同的数值。

> [!INFO] 也可以为多个对象指定多个变量。

```Python
a, b, c = 1, 2, "runoob"
```

- [*] 以上实例，两个整型对象 1 和 2 的分配给变量 a 和 b，字符串对象 "runoob" 分配给变量 c。

# 标准数据类型
### Python3 中常见的数据类型有：

- [*] **Number**（数字）
- [*] **String**（字符串）
- [*] **bool**（布尔类型）
- [*] **List**（列表）
- [*] **Tuple**（元组）
- [*] **Set**（集合）
- [*] **Dictionary**（字典）
### Python3 的六个标准数据类型中：

- [p] **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- [p] **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。

此外还有一些高级的数据类型，如: 字节数组类型(bytes)。

# Number（数字）

Python3 支持 **int、float、bool、complex（复数）**。

在Python 3里，只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。

像大多数语言一样，数值类型的赋值和计算都是很直观的。

### 使用内置的 type() 函数来查询变量所指的对象类型

```Python
a, b, c, d = 20, 5.5, True, 4+3j
```

```Python
print(type(a), type(b), type(c), type(d))
```
### 运行结果
```Python
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'> 
```
### 使用 isinstance 来判断对象类型

```Python
a = 111
```

```Python
isinstance(a, int)
```
### 运行结果
```Python
True
```
##### isinstance 和 type 的区别

- [*] **type**()不会认为子类是一种父类类型。
- [*] **isinstance**()会认为子类是一种父类类型。

#### 注意

- [/] 在Python 3 中，bool 是 int 的子类，True 和 False 可以和数字相加， True\==1、False\==0 会返回 True，但可以通过 is 来判断类型。
```Python
>>> issubclass(bool, int) 
True
>>> True==1
True
>>> False==0
True
>>> True+1
2
>>> False+1
1
>>> 1 is True
False
>>> 0 is False
False
```

- [n] 在 Python 2 中是没有布尔型的，它用数字 0 表示 False，用 1 表示 True。

