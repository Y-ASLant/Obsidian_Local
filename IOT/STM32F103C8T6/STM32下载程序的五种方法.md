# STM 32 下载程序的五种方法
> [!BUG] STM 32 代码五种烧录方式
> 1. 串口下载
> 2. ST-Link V 2 下载 
> 3. ST-LINK Utility 下载
> 4. JLink 下载
> 5. STVP 下载

五种方式不知道选哪种？直接看总结。

懒得找驱动安装包、软件安装包？我都给你提供啦。

通过深入了解这些烧录方式，相信大家将能够更好地理解 STM 32 的烧录过程，选择合适的方式进行开发和调试。

## 0. 前置阅读

如果不知道如何搭建 STM 32 编程环境，不知道如何烧录 STM 32 代码，可以阅读这篇文章：

【 [零基础快速上手STM32开发（手把手保姆级教程）open in new window](https://www.lxlinux.net/e/stm32/stm32-quick-start-for-beginner.html) 】

新手小白如果连 MDK 的使用都不熟悉，那么可以通过下文先熟悉一下 MDK 的使用：

【 [一文教你使用MDK开发工具open in new window](https://www.lxlinux.net/e/stm32/mdk-development-tool-tutorial.html) 】

文中所使用的芯片是 STM 32 F 103 C 8 T 6 ，配套了一个工程模板，如果你需要自己搭建一个工程模板，可以参考下文：

【 [手把手带你创建HAL版本MDK工程模板open in new window](https://www.lxlinux.net/e/stm32/create-stm32-hal-project-template.html) 】

## 1. 安装包及驱动准备

- **安装包准备**

**1. MDK 5 安装包**

链接：https://pan.baidu.com/s/1j7USS7-rsmr7-GZ_BIIEYQ?pwd=5q3s 提取码：5 q 3 s

**3. 芯片固件包**

链接：https://pan.baidu.com/s/1Td21MOEshL7qE4afCBSjtw?pwd=86uh 提取码：86 uh

**4. 串口烧录工具（FlyMcu)**

链接：https://pan.baidu.com/s/1AvzZaWW9bk79YiuaVy-IHA?pwd=tlpp 提取码：tlpp

**5. ST-Link Utility**

链接：https://pan.baidu.com/s/1_3yyzdPzwYdv4RU2qC9vgQ?pwd=f8qn 提取码：f 8 qn

**6. STVP**

链接：https://pan.baidu.com/s/1eue65d49fJFxK1afJGyrzg?pwd=vywt 提取码：vywt

- **驱动准备**

**1. CH 340 驱动**

链接：https://pan.baidu.com/s/1Xe0Xd_HA88Yv3o4e4CLMrg?pwd=qwql 提取码：qwql

**2. ST-Link 驱动**

链接：https://pan.baidu.com/s/1-E74B4w3LXRWvdRyg4JnNg?pwd=2jfb 提取码：2 jfb

**3. JLink 驱动**

链接：https://pan.baidu.com/s/1EWs8M6XMagHknC4FUreiBw?pwd=cxyc 提取码：cxyc

- **示例代码**

**STM 32 F 103 C 8 T 6 模板工程**

链接：https://pan.baidu.com/s/1n7XHCaMYtASWdJH2uA5yDA?pwd=lw59 提取码：lw 59

## 2. 串口下载

串口下载是我初学时常用的下载方式，现在看有些不如 ST-Link 方便。使用 ST-Link 基本可以实现一键下载程序，而串口需要反复拔插跳线帽，而且还需要单独的程序员，比较麻烦。

- Need： CH 340 USB 转 TTL 模块
    
    这种设备主要作用是用来调试或下载程序。价格也很便宜，普遍 5~8 元。常见的有以下两种：
    ![[../../ASLant_Files/70f88eba70a13a2b8ac231106c723fbe_MD5.jpg|504]]
    ![[../../ASLant_Files/27836164a047abb3dac3adbc5a37e53b_MD5.jpg|500]]
    
    个人更推荐下面一款，因为它可以切换 VCC 输出电压，在对一些传感器进行独立测试的时候会比较方便。不过反正也不贵，多买几个想怎么用就怎么用。
    
### 2.1 CH 340 驱动安装

![[../../ASLant_Files/d1e02718c367e7f2ef45aeebbcdf6486_MD5.jpg]]
![[../../ASLant_Files/9a62350e777fc68941f31e525bea9a3e_MD5.jpg]] ![[../../ASLant_Files/d3b036f847704ff8aa57c990af959b46_MD5.jpg]]
### 2.2 FlyMcu 安装

串口下载工具有很多，这里推荐 FlyMcu 。

FlyMcu 是一款好用的 STM 32 烧录程序软件，对于专业的单片机开发者来说应该非常适用，软件可以广泛地应用于电路编程和应用编程领域，支持进行编程、校验、读器件信息。

这款工具是国产的，大家如果需要最新版的，可以去它们的官网下载：

http://www.mcuisp.com/

当然，用我提供的也行，反正也是他们官网下载的。

![[../../ASLant_Files/52b241ad6bff61b42c7be321eb0ed5c3_MD5.jpg]]

![[../../ASLant_Files/63c0fd192b6f3d9a3ef3b13ebba7ecea_MD5.jpg]]

![[../../ASLant_Files/a3eb1169f894fb17e65f5bcb4c55bf7e_MD5.jpg]]

下载好后解压，双击 .exe 文件即可打开，无需安装。

### 2.3 硬件连线

在下载程序之前，请先接好线。接线图如下图所示：

![[../../ASLant_Files/65e540481c52fc8103812075eaf012bc_MD5.jpg]]

电源接线没什么好说的，主要是串口这边，一定要注意**交叉接线**，也就是 CH 340 转 TLL 工具的 TX 要接板子的 RX ，CH 340 转 TLL 工具的 RX 要接板子的 TX ，千万不要接错，否则就不能烧进去！

开发板上的 PA 9 是 TX ，PA 10 是 RX ，请按上一段提到的交叉接线接好线。

### 2.4 程序下载

打开 FlyMcu 。如果你们使用的是我上面推荐的 STM 32 F 103 C 8 T 6 核心板，那么请下载 `1. 安装包及驱动准备` 我提供的模板工程，如下操作：

![[../../ASLant_Files/085bd75a8bbdf5804f05cf5d4d8f5b09_MD5.jpg]]

接下来，将板子上的 BOOT 0 跳线帽接到 1 ，BOOT 1 路线帽维持在 0 ，如下图所示：

![[../../ASLant_Files/0ed6b22403dbf3c256310c27916e9bea_MD5.jpg]]

为什么要这么操作呢？

这两个跳线帽是用来调整 BOOT 0 和 BOOT 1 的状态。跳线帽接到 1 就是高电平，接到 0 就是低电平。

BOOT 0 和 BOOT 1 是用于设置 STM 32 的启动方式的：

|BOOT 0|BOOT 1|启动模式|说明|
|---|---|---|---|
|0|X|用户闪存存储器|用户闪存存储器，也就是 flash 启动|
|1|0|系统存储器|系统存储器，用于串口下载|
|1|1|SRAM 启动|SRAM 启动，用于在 SRAM 中调试代码|

这里是用 USB 下载，也就是串口下载，所以选择表中的第二个方式也就是 **BOOT 0 选择 1， BOOT 1 选择 0** 。![[../../ASLant_Files/adceb819f948b7b0ff86d050a4714086_MD5.jpg]]

然后你就可以点击软件上的开始编程按钮，但你会发现，右边一直处于连接状态。这个时候，只有你按一下板子上的 reset 按键（板子上唯一的一个按键），它就开始往下走了。

![[../../ASLant_Files/e37c53f0daf8f52ea43ba7424396c691_MD5.jpg]]

**下载后记得把 BOOT 0 的跳线冒跳回 0 端**，BOOT 0 和 BOOT 1 都为 0 ，这样程序就从 flash 区启动，再按一下 reset 按键板子就开始运行烧录进去的代码了。

## 3. ST-Link V 2 下载

ST-Link V 2 是我现在最常用的下载方式，也是我最推荐的。 ST-Link V 2 是 STM 8 、 STM 32 系列单片机的在线仿真器和下载器。 ST-Link 出生就带有两种接口模式： SWIM 接口模式（ STM 8 ）， SWD 接口模式（ STM 32 ）。

- Need： ST-Link V 2 下载器
    
    ST-Link 是一种用于 STM 32 微控制器的调试和编程工具，它可以通过 SWD 或 JTAG 接口与开发板进行通信。一般也很便宜，七八元左右。
    
    ![[../../ASLant_Files/2f32f9397c8929dd5e698c92a5876013_MD5.jpg]]
    

### 3.1 ST-Link 驱动安装

![[../../ASLant_Files/165a54a1541b2cd4c071e1e861698f2a_MD5.jpg]]

![[../../ASLant_Files/49a2b2cf6f19e5babde30d4286770363_MD5.jpg]]

![[../../ASLant_Files/0087f2cdda542ac51a4f5db26f8638a3_MD5.jpg]]

![[../../ASLant_Files/8b4fc5c6d7d4de3abab94a489a23100f_MD5.jpg]]

![[../../ASLant_Files/70ea52a0a20ec024e3fd35a1a9fd6a96_MD5.jpg]]

![[../../ASLant_Files/b0f98d0b0658f60077512708ef08c153_MD5.jpg]]

### 3.2 安装 MDK 5

MDK 5 是由 Keil 公司发布的一款嵌入式软件开发环境，我们平时在进行 STM 32 开发的时候，基本上都是在这个软件上进行。

MDK 5 可以在它们的官网上下载，网址如下：

https://www.keil.com/demo/eval/arm.htm#/DOWNLOAD

![[../../ASLant_Files/805562b5ad979a2c045bc377d152ab0c_MD5.jpg]]

当前最新版本是 MDK 538 A ，但新版并不意味着最好，可能会有一些奇奇怪怪的问题，也可能不稳定。

推荐大家使用 MDK 534，也是我目前所使用的版本，至今未出过什么问题。安装包已经在 `1. 安装包及驱动准备` 为大家提供了，接下来我就手把手教大家在你们的电脑上安装 MDK 5 。

双击我给大家提供的安装包后，会出现以下界面，大家跟着我的图片操作即可：

![[../../ASLant_Files/4e5c086f16b8356edd40dbd5f98a38ab_MD5.jpg]]

![[../../ASLant_Files/5b0fd6d0a205a4775140f4aab3ab1b34_MD5.jpg]]

![[../../ASLant_Files/2ae50909c131716d279be7a935b7f16d_MD5.jpg]]

![[../../ASLant_Files/e44b9bf50ea16de7b51d7833c3e14e2e_MD5.jpg]]

![[../../ASLant_Files/522fea84c1288a7058859e0803e04675_MD5.jpg]]

![[../../ASLant_Files/693e8ec1ab0e15b065896eb3dd70a842_MD5.jpg]]

![[../../ASLant_Files/4ad05405df7354809e1986fbb184add3_MD5.jpg]]

![[../../ASLant_Files/17da5b92c0b286cdb3b56e4e8d9ede17_MD5.jpg]]

![[../../ASLant_Files/4972cb1432e3df9038865d939b3ef94f_MD5.jpg]]

到此为止，MDK 5 就安装完成了。

但是，我给你们提供的安装包是官网下载的正版版本，试用几天后就要收费了。破解的方法网络上有一大堆，这里我就不讲了，我也怕律师函。

接下来就要安装固件包了。什么是固件包呢？由于 ST 公司生产了非常多的芯片，每颗芯片所需要的支持文件都不一样，这些文件组合起来就是固件包。

但有这么多芯片，他们不可能把所有的固件包都集成在 MDK 5 里，否则 MDK 5 的安装包将变得超级无敌巨大，很占空间也没必要。比较好的解决方案就是你需要用到什么芯片，就安装对应的固件包就可以了。

固件包也是在官网上可以下载到，网址如下：

https://www.keil.arm.com/packs/

![[../../ASLant_Files/70883a52cb6dfbd845f17cf240c081fe_MD5.jpg]]

由于我们使用的板子是 STM 32 F 103 C 8 T 6 ，属于 F 1 系列，所以在搜索框里搜索 STM 32 F 1 即可。如果大家使用的是其它系列芯片，那就搜索对应系列的关键词，不要傻乎乎都按下图搜索哦~

![[../../ASLant_Files/5bf339362fe3d6048dc8e63ee73a2359_MD5.jpg]]

同样的，由于服务器在国外，下载速度巨慢。大家用我提供的文件就可以了，同样也是官网上下载的，原汁原味。链接在 `1. 安装包及驱动准备` 可以找到。

安装的方法很简单，只需要双击安装包即可，然后它就会自动识别固件包的目录，点击 Next ，然后等进度条走到底就 OK 了。

![[../../ASLant_Files/3f493e4d7f23b8895df0080ae5d462a0_MD5.jpg]]

### 3.3 程序编译

如果你们使用的是我上面推荐的 STM 32 F 103 C 8 T 6 核心板，那么请下载 `1. 安装包及驱动准备` 我提供的模板工程，然后打开这个工程。

![[../../ASLant_Files/14b4a34f9360d46428dc88900d8a2b52_MD5.jpg]]

![[../../ASLant_Files/e02d4f0048c5e5ad846ef3564e3c8abb_MD5.jpg]]

程序打开后，在上图中左上角箭头处，有三个按钮，我们所做的编译工作都是使用这三个按钮。那这三个按钮有什么作用呢？

- 第一个按钮： Translate 就是翻译当下修改过的文件，说明白点就是检查下有没有语法错误，并不会去链接库文件，也不会生成可执行文件。
    
- 第二个按钮： Build 就是编译当下修改过的文件，它包含了语法检查，链接动态库文件，生成可执行文件。
    
- 第三个按钮： Rebuild 重新编译整个工程，跟 Build 这个按钮实现的功能是一样的，但有所不同的是它编译的是整个工程的所有文件，耗时巨大。
    

在实际工作中，我们最经常使用的就是第二个按钮，另外两个用得不多，尤其是第一个。

### 3.4 硬件接线

![[../../ASLant_Files/c050e1a4625301aa390f9880bc57a0a5_MD5.jpg]]

核心板上边的电源线，随便找一根 microUSB 线来接就行，也就是之前手机充电线，扁头的那种，它就是用来供电的，没有传输数据。

而下边的下载引脚，主要是三根起作用： SWDIO 、 SWDCLK 、 GND 。大家认真对照核心板与 ST-Link ，别接错了哈。特别是 ST-Link ，接的是缺口对面那一排引脚，而不是靠近缺口的那一排引脚。为了让你们看更清楚，我又拍了一张细节图（够保姆吧）。

在下面这张图里，棕色是 GND ，红色是 SWDIO ，黄色是 SWDCLK ，大家可以对照着接线。

![[../../ASLant_Files/6a4687c317bcdd17812961d16ed1cb9f_MD5.jpg]]

### 3.5 程序下载

在下载之前，请先按下面的步骤做好配置。

![[../../ASLant_Files/1b0ccea0493b7f0e59e7df5d6529b888_MD5.jpg]]

![[../../ASLant_Files/75096fc11f921e5353ee171df8e9b069_MD5.jpg]]

![[../../ASLant_Files/0f07cbf1884f234ed1776fb8185eaee8_MD5.jpg]]

![[../../ASLant_Files/c1b340974a1e0417f2c49f1f3e515ffe_MD5.jpg]]

![[../../ASLant_Files/9144ca9016478b845195bc6dc3d2c0a8_MD5.jpg]]

到此为止，针对 MDK 的配置已经搞定了，现在就可以进行下载了。

在下载之前，请做好四件事：

1. 就是刚刚前面的配置，一定要配置好；
2. 设备的接线，只要有一根线没接对，就无法完成下载；
3. 编译好程序；
4. 板子一定要上电。

![[../../ASLant_Files/9d0aef28ad3b8023d769beda7be92060_MD5.jpg]]

程序下载成功之后，板子自动运行新代码，会看到 LED 灯间隔 500 毫秒亮灭交替闪烁。

![[../../ASLant_Files/fbc7e54f45beadb049c1b2d5b3af2358_MD5.jpg]]

## 4. STM 32 ST-LINK Utility 下载

STM 32 ST-LINK Utility 是针对 STM 32 全系芯片进行编程（读、写、擦除、选项字）的一款工具。

ST-LINK Utility 只支持 ST-Link （多个版本）的下载调试器，支持的芯片只有 STM 32 。

- Need： ST-Link 下载器（和 `3. ST-Link V2下载` 使用的设备一样）

### 4.1 ST-LINK Utility 安装

官网下载：

https://www.st.com/en/development-tools/stsw-link004.html

![[../../ASLant_Files/d8de59e99efa4fc23025b3fde5dd7573_MD5.jpg]]

官网需要注册、填邮箱……怪麻烦的，所以建议直接拿我准备好的安装包（ `1. 安装包及驱动准备` )，也是官网下的，4.6.0 版本。
安装没啥好说的，**无脑下一步**，有需要的话记得改下安装路径。
### 4.2 硬件连接

ST-Link V 2 和 STM 32 引脚一一对应就可以了，采用 SWD 接口模式，接好如图，插上电脑。
```text
ST-Link V2 STM32
  SWCLK => SWCLK
  SWDIO => SWDIO
    GND => GND
   3.3V => 3V3
```

![[../../ASLant_Files/861fdd5b5bad4aafb167e55484e71581_MD5.jpg]]

### 4 .2 程序下载

打开 ST-LINK Utility ，如图操作：

![[../../ASLant_Files/159efac69592832b55e2100989b8b605_MD5.jpg]]

![[../../ASLant_Files/9ccf60742712c0226f6c8a2936258391_MD5.jpg]]

这里需要选择 hex 文件，如果你们使用的是我上面推荐的 STM 32 F 103 C 8 T 6 核心板，可以下载 `1. 安装包及驱动准备` 我提供的模板工程，如下操作。想烧自己的代码要是没有 hex 文件的话可以用 MDK（Keil） 生成。

![[../../ASLant_Files/2466a5401eb821d5ba7d61614e07c198_MD5.jpg]]

![[../../ASLant_Files/480bcc6e1029617db645de9b316fda9b_MD5.jpg]]

看到出现 “Verification... OK” 就是下载成功。

![[../../ASLant_Files/386af5476368051733b808d320c14492_MD5.jpg]]

程序下载成功之后，板子自动运行新代码，会看到 LED 灯间隔 500 毫秒亮灭交替闪烁。

## 5. JLink 下载

JLINK 是一个兼容 JTAG 的仿真器，可以烧入程序和调试。

调试 ARM ，需要遵循 ARM 的调试接口协议， JTAG 就是其中的一种。JTAG 是一种国际标准测试协议，也叫 ARM 调试协议。现在多数的高级器件都支持 JTAG 协议，如 DSP 、 FPGA 器件等。

网上有的 JLink 下载用的是 JFlash ，我觉得有点麻烦了，还要再下一个软件，直接用 MDK 就行。

- Need： J-Link 仿真下载器

支持 KEIL 、 IAR 、 ADS 等编译仿真软件。支持功能 JTAG 、 SWD 、 SWO 、 VCOM 模式。正版 JLink 价格在 2000 元以上，某宝上仿的均价在 70 左右，但容易掉固件（一般商家支持帮我们重刷固件）。

![[../../ASLant_Files/d15ed483c3179b95a59245f00aab28da_MD5.jpg]]

### 5.1 J-Link 驱动安装

官网下载地址：

https://www.segger.com/downloads/jlink

也可以用我提供的驱动安装包，我的是 V 612 ，V 1、V 2、V 8、V 9 的仿真器都可以用，或者找买的客服，一般都有驱动（不走官网就跳过下两张图）。

![[../../ASLant_Files/2727fab6d8b05867c3c537b9e5633cd5_MD5.jpg]]

![[../../ASLant_Files/65cf5f6429594ecbc596a58858eb3378_MD5.jpg]]

安装好后解压打开，点下图的 .exe 文件。

![[../../ASLant_Files/599951c9dc0fb17b3f6fa8ce1dd78303_MD5.jpg]]

如下操作：

![[../../ASLant_Files/ea47506641946c547249c1158fc7be51_MD5.jpg]]

![[../../ASLant_Files/b2fe7953edaa0155fad082a94fae0891_MD5.jpg]]

![[../../ASLant_Files/962c8e2d3b2ea60466b495a3dc8a29e7_MD5.jpg]]

![[../../ASLant_Files/edef4571762d09bfffa45dcc4751015b_MD5.jpg]]

![[../../ASLant_Files/3b1e664e9e00989160287647797d5127_MD5.jpg]]

![[../../ASLant_Files/0b0dc0d72be7b633a1c4a3800b96a411_MD5.jpg]]

### 5.2 硬件连线

烧 STM 32 只要用 4 条杜邦线就可以了，和 STM 32 ST-LINK Utility 下载连线一样，采用 SWD 接口模式，这里的 VREF 就是电源正极。

![[../../ASLant_Files/7cd61fefa21e06cdf6899db3a43ab2ba_MD5.jpg]]

看图连线应该很简单吧，1、7、9 是上面一排，20 是下面一排哦。

![[../../ASLant_Files/643fe2329449140fac908927cdaee83f_MD5.jpg]]

整体连好长这样：

![[../../ASLant_Files/f94d0571955d950bdb47710e2de50aab_MD5.jpg]]

### 5.3 程序下载

使用 MDK 5 打开工程（这里用的是我的模板工程），点击魔法棒，跟我操作。

![[../../ASLant_Files/76819356766de9fca8903ed28c5b09a4_MD5.jpg]]

![[../../ASLant_Files/5bf0d84a39b0372e3df887bdb7fd1b04_MD5.jpg]]

一般这样设置就可以了，如果烧录失败，可以参考 3.5 。

![[../../ASLant_Files/99551b098cce600ebb2c8fdea387e286_MD5.jpg]]

## 6. STVP 下载

STVP 是很早的下载工具了，支持 ST 7 、 STM 8 、 STM 32 系列。说实话，这玩意从安装到使用都是太奶级别，又臭又长，真的不建议使用。。

- Need： ST-Link 下载器

### 6.1 STVP 安装

官网下载：

https://www.st.com/en/development-tools/stvp-stm32.html#get-software

和 ST-LINK Utility 一样，官网需要注册、填邮箱……怪麻烦的，所以建议直接拿我准备好的安装包（ `1. 安装包及驱动准备` ），也是官网下的。

![[../../ASLant_Files/a78ab8d160395f96fdcf313b5f27d948_MD5.jpg]]

![[../../ASLant_Files/fc60b7ac457c53bf86b05bdc5dbc015d_MD5.jpg]]

安装过程也是一路 Next 就行，由于安装时我不能截屏了，所以拍几个关键步骤出来。

![[../../ASLant_Files/9db6956741aac0707f43647f85e3acbb_MD5.jpg]]

![[../../ASLant_Files/470e38e54c1a421081e61e4977456cf4_MD5.jpg]]

![[../../ASLant_Files/7a46aac34b83523362e3dc246d9146b6_MD5.jpg]]

PS ：安装好后会看见 STVD 和 STVP ，我们用 STVP 就行。

- STVD ： ST Visual Develop ，可视化开发工具
- STVP ： ST Visual Programmer ，可视化编程工具

### 6.2 硬件连接

> 和 3.4 一样， ST-Link V 2 和 STM 32 引脚一一对应就可以了，接好如图，插上电脑。

```text
ST-Link <=> STM32
SWCLK  =>  SWCLK
SWDIO  =>  SWDIO
  GND  =>  GND
 3.3V  =>  3V3
```

![[../../ASLant_Files/861fdd5b5bad4aafb167e55484e71581_MD5.jpg]]

### 6.3 程序下载

安装好后，桌面会有这个图标，点击打开。

![[../../ASLant_Files/f299f3ec0094f856a7dbad87d5be326d_MD5.jpg]]

这里以 ST-Link 下载器和 STM 32 F 103 C 8 T 6 核心板为例：

![[../../ASLant_Files/35c8c625e8d972c908e76e691dac061e_MD5.jpg]]

弹出新窗口，如下操作，这里打开的是 `1. 安装包及驱动准备` 我提供的模板工程，大家可以选自己的，要是 hex 文件，没有可以用 MDK（Keil） 生成。

![[../../ASLant_Files/878c5da69409c26f1c71d298d6ccce0a_MD5.jpg]]

![[../../ASLant_Files/8d288dd8bc23ebf083cc972a9689ecd2_MD5.jpg]]

![[../../ASLant_Files/fe80a6217b348bd0d77a941c3e4b9e98_MD5.jpg]]

## 7. 总结

对于初学者来说，没必要掌握那么多烧录方式，就我和我身边的程序猿来说，大家都喜欢用 ST-Link V 2 搭配 MDK 5 编写、烧录程序，所以我也推荐初学者先从 ST-Link V 2 烧录方式开始，比较方便快捷。

> [!ERROR] hex 文件、 bin 文件、 axf 文件的区别：

Hex 文件、 bin 文件和 axf 文件是在嵌入式系统开发中常见的文件格式，用于存储编译后的程序代码和数据。

**hex 文件（ Intel HEX ）**： hex 文件是一种十六进制文本文件格式，用于表示程序代码和数据的二进制内容。它由一系列十六进制数值组成，每个数值对应一个字节的数据。 Hex 文件通常包含地址信息、数据记录类型和实际的数据内容。它是一种常见的文件格式，广泛用于烧录设备、调试工具和仿真器等。

**bin 文件（ Binary ）**： bin 文件是一种原始的二进制文件格式，直接以二进制形式存储程序代码和数据。 Bin 文件没有像 hex 文件那样进行十六进制的编码，而是按照字节的实际值进行存储。 Bin 文件可以更直观地表示程序的原始二进制数据，但缺少了地址和其他元数据信息，因此在烧录和调试过程中需要额外的处理。

**axf 文件（ ARM eXtended Format ）**： axf 文件是针对 ARM 架构开发的一种特定格式，包含了可执行程序的代码、数据和符号表等信息。 Axf 文件通常由 ARM 开发工具链生成，可以包含链接器产生的符号表、调试信息和其他附加的元数据。 Axf 文件在调试过程中非常有用，可以用于查看和分析程序的结构、变量信息等。
