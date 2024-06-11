# Kotlin 简介

![[ASLant_Images/265e74639a14dcd6c1387b2e82b23a5b_MD5.jpg]]

- Kotlin 是一种在 Java 虚拟机上运行的静态类型编程语言，被称之为 Android 世界的Swift，由 JetBrains 设计开发并开源。
- Kotlin 可以编译成Java字节码，也可以编译成 JavaScript，方便在没有 JVM 的设备上运行。
- 在Google I/O 2017中，Google 宣布 Kotlin 成为 Android 官方开发语言。
- **Kotlin 程序文件以 .kt 结尾，如：hello.kt 、app.kt**
### 为什么选择 Kotlin？

- 简洁: 大大减少样板代码的数量。
- 安全: 避免空指针异常等整个类的错误。
- 互操作性: 充分利用 JVM、Android 和浏览器的现有库。
- 工具友好: 可用任何 Java IDE 或者使用命令行构建。
### Android Studio 下载
> [!BUG] [Android Studio 2023.3.1.18](https://redirector.gvt1.com/edgedl/android/studio/install/2023.3.1.18/android-studio-2023.3.1.18-windows.exe)
# Kotlin 基础语法
### 包声明

代码文件的开头一般为包的声明：
```kotlin
package com.aslant.main
import java.util.*

fun test() {}
class ASLant {}
```

- kotlin源文件不需要相匹配的目录和包，源文件可以放在任何文件目录。
- 以上例中 test() 的全名是 com.aslant.main.test、ASLant 的全名是 com.aslant.main.ASLant。
- 如果没有指定包，默认为 default 包。








