## cd命令 – 切换目录

cd命令来自于英文词组”change directory“的缩写，其功能是用于更改当前所处的工作目录，路径可以是绝对路径，也可以是相对路径，若省略不写则会跳转至当前使用者的家目录。

**语法格式：**cd [参数] [目录名]

  

**常用参数：**

| -P    | 如果切换的目标目录是一个符号链接，则直接切换到符号链接指向的目标目录                  |
| ----- | --------------------------------------------------- |
| -L    | 如果切换的目标目录是一个符号链接，则直接切换到符号链接名所在的目录                   |
| --    | 仅使用”-“选项时，当前目录将被切换到环境变量”OLDPWD”对应值的目录               |
| ~     | 切换至当前用户目录                                           |
| ..    | 切换至当前目录位置的上一级目录                                     |

**参考实例**

  

切换当前工作目录至/etc：

  

```sh
[root@linuxcool ~] # cd /etc
[root@linuxcool etc] #
```

切换至当前用户的家目录：

```sh
[root@linuxcool etc] # cd ~
[root@linuxcool ~] #
```

进入到上一级所在目录（家目录→根目录）：

```sh
[root@linuxcool ~] # cd ..
[root@linuxcool /] #
```

返回到上一次所在目录（根目录→家目录）：

```sh

[root@linuxcool /] # cd -

/root

[root@linuxcool ~] #

```


## cp命令 – 复制文件或目录

  

cp命令来自于英文单词copy的缩写，用于将一个或多个文件或目录复制到指定位置，也常用于文件的备份工作。-r参数用于递归操作，复制目录时若忘记加则会直接报错，而-f参数则用于当目标文件已存在时会直接覆盖不再询问，这两个参数尤为常用。

  

**语法格式：**cp  [参数]  源文件  目标文件

  

**常用参数：**

  

| -f   | 若目标文件已存在，则会直接覆盖原文件                         |

| :---- | :---------- |

| -i   | 若目标文件已存在，则会询问是否覆盖                           |

| -p   | 保留源文件或目录的所有属性                                   |

| -r   | 递归复制文件和目录                                           |

| -d   | 当复制符号连接时，把目标文件或目录也建立为符号连接，并指向与源文件或目录连接的原始文件或目录 |

| -l   | 对源文件建立硬连接，而非复制文件                             |

| -s   | 对源文件建立符号连接，而非复制文件                           |

| -b   | 覆盖已存在的文件目标前将目标文件备份                         |

| -v   | 详细显示cp命令执行的操作过程                                 |

| -a   | 等价于“pdr”选项                                              |

  

**参考实例**

  

在当前工作目录中，将某个文件复制一份，并定义新文件名称：

  

```bash

[root@Linux ~] # cp test.cfg kickstart.cfg

```

  

在当前工作目录中，将某个目录复制一份，并定义新目录名称：

  

```bash

[root@Linux ~] # cp -r Documents Doc

```

  

复制某个文件时，保留其原始权限及用户归属信息：

  

```bash

[root@Linux ~] # cp -a kickstart.cfg ks.cfg

```

  

将某个文件复制到/etc目录中，**并覆盖已有文件**，**不进行询问**：

  

```bash

[root@Linux ~] # cp -f ks.cfg /etc

```

  

将**多个文件一同复制**到/etc目录中，如已有目标文件名称则**默认询问**是否覆盖：

  

```bash

[root@Linux ~] # cp test.cfg ks.cfg /etc

cp: overwrite '/etc/ks.cfg'? y

```

  
  
  

## mkdir命令 – 创建目录文件

  

mkdir命令来自于英文词组“make directories”的缩写，其功能是用来创建目录文件。使用简单，但需要注意若要创建的目标目录已经存在，则会提示已存在而不继续创建，不覆盖已有文件。而目录不存在，但具有嵌套的依赖关系，例如a/b/c/d/e/f，要想一次性创建则需要加入-p参数，进行递归操作。

  

**语法格式 :** mkdir  [参数]  目录

  

**常用参数：**

  

| -p   | 递归创建多级目录             |

| :---- | :---------------------------- |

| -m   | 建立目录的同时设置目录的权限 |

| -z   | 设置安全上下文               |

| -v   | 显示目录的创建过程           |

  

**参考实例**

  

在当前工作目录中，建立一个目录文件：

  

```bash

[root@Linux ~] # mkdir dir1

```

  

在当前工作目录中，创建一个目录文件并设置700权限，不让除所有主以外任何人读、写、执行它：

  

```bash

[root@Linux ~] # mkdir -m 700 dir2

```

  

在当前工作目录中，一次性创建多个目录文件：

  

```bash

[root@Linux ~] # mkdir dir3 dir4 dir5

```

  

在系统根目录中，一次性创建多个有嵌套关系的目录文件：

  

```bash

[root@Linux ~] # mkdir -p /dir1/dir2/dir3/dir4/dir5

```

  
  
  

## mv命令 – 移动或改名文件

  

mv命令来自于英文单词move的缩写，其功能与英文含义相同，用于对文件进行剪切和重命名。

  

这是一个高频使用的文件管理命令，我们需要留意它与复制命令的区别。cp命令是用于文件的复制操作，文件个数是增加的，而mv则为剪切操作，也就是对文件进行移动（搬家）操作，文件位置发生变化，但总个数并无增加。

  

在同一个目录内对文件进行剪切的操作，实际应理解成重命名操作，例如下面的实例一所示。

  

**语法格式：**mv [参数] 源文件 目标文件

  

**常用参数：**

  

| -i   | 若存在同名文件，则向用户询问是否覆盖                         |

| :---- | :----------------------------------------- |

| -f   | 覆盖已有文件时，不进行任何提示                               |

| -b   | 当文件存在时，覆盖前为其创建一个备份                         |

| -u   | 当源文件比目标文件新，或者目标文件不存在时，才执行移动此操作 |

  

**参考实例**

  

在当前工作目录中，对某个文件进行剪切后粘贴（重命名）操作：

  

```bash

[root@Linux ~] # mv test.cfg ks.cfg

```

  

将某个文件移动到/etc目录中，保留文件原始名称：

  

```bash

[root@Linux ~] # mv ks.cfg /etc

```

  

将某个目录移动到/etc目录中，并定义新的目录名称：

  

```bash

[root@Linux ~] # mv Documents /etc/docs

```

  

将/home目录中所有的文件都移动到当前工作目录中，遇到已存在文件则直接覆盖：

  

```bash

[root@Linux ~] # mv -f /home/* .

```

  
  
  

## touch命令 – 创建空文件与修改时间戳

  

touch命令的功能是用于创建空文件与修改时间戳。如果文件不存在，则会创建出一个空内容的文本文件；如果文件已经存在，则会对文件的Atime（访问时间）和Ctime（修改时间）进行修改操作，管理员可以完成此项工作，而普通用户只能管理主机的文件。

  

**语法格式：**touch [参数] 文件

  

**常用参数：**�

  

| -a          | 改变档案的读取时间记录                     |

| ----------- | ------------------------------------------ |

| -m          | 改变档案的修改时间记录                     |

| -r          | 使用参考档的时间记录，与 --file 的效果一样 |

| -c          | 不创建新文件                               |

| -d          | 设定时间与日期，可以使用各种不同的格式     |

| -t          | 设定档案的时间记录，格式与 date 命令相同   |

| --no-create | 不创建新文件                               |

| --help      | 显示帮助信息                               |

| --version   | 列出版本讯息                               |

  

�**参考实例**

  

**创建出一个指定名称的空文件**：

  

```bash

[root@Linux ~] # touch File.txt

```

  

结合**通配符**，创建出多个指定名称的空文件：

  

```bash

[root@Linux ~] # touch File{1..5}.txt

```

  

修改指定文件的查看时间和修改时间：

  

```

[root@Linux ~] # touch -d "2022-05-08 15:44" anaconda-ks.cfg

[root@Linux ~] # stat anaconda-ks.cfg

  File: anaconda-ks.cfg

  Size: 1256         Blocks: 8          IO Block: 4096   regular file

Device: fd00h/64768d Inode: 35319937    Links: 1

Access: (0600/-rw-------)  Uid: (    0/    root)   Gid: (    0/    root)

Context: system_u:object_r:admin_home_t:s0

Access: 2022-05-08 15:44:00.000000000 +0800

Modify: 2022-05-08 15:44:00.000000000 +0800

Change: 2022-05-06 15:43:47.843170709 +0800

 Birth: -

```

  
  
  

## rm命令 – 删除文件或目录

  

rm命令来自于英文单词remove的缩写，其功能是用于删除文件或目录，一次可以删除多个文件，或递归删除目录及其内的所有子文件。

  

rm也是一个很危险的命令，使用的时候要特别当心，尤其对于新手更要格外注意，如执行rm -rf /*命令则会清空系统中所有的文件，甚至无法恢复回来。所以我们在执行之前一定要再次确认下在哪个目录中，到底要删除什么文件，考虑好后再敲击回车，时刻保持清醒的头脑。

  

**语法格式：**rm [参数] 文件

  

**常用参数：**

  

| -f   | 强制删除（不二次询问）   |

| :--- | :---------------- |

| -i   | 删除前会询问用户是否操作 |

| -r/R | 递归删除                 |

| -v   | 显示指令的详细执行过程   |

  

**参考实例**

  

删除某个文件，默认会进行二次确认，敲击y进行确认。

  

```bash

[root@Linux ~] # rm test.cfg

rm: remove regular file 'test.cfg'? y

```

  

删除某个文件，强制操作不需要二次确认：

  

```bash

[root@Linux ~] # rm -f initial-setup-ks.cfg

```

  

删除某个目录及其内的子文件或子目录，一并都强制删除：

  

```bash

[root@Linux ~] # rm -rf Documents

```

  

强制删除当前工作目录内的所有以.txt为后缀的文件

  

```bash

[root@Linux ~] # rm -f *.txt

```

  

【删库跑路必备技能】强制清空服务器系统根目录内的所有文件：

  

```bash

[root@Linux ~] # rm -rf /*

```

  
  
  

## rmdir命令 – 删除空目录文件

  

rmdir命令来自于英文词组“remove directory”的缩写，其功能是用于删除空目录文件。rmdir命令仅能够删除空内容的目录文件，如需删除非空目录时，则需要使用带有-R参数的rm命令进行操作。而rmdir命令的-p递归删除操作亦不意味着能删除目录中已有的文件，而是要求每个子目录都必须是空的。

  

**语法格式 :** rmdir [参数] 目录

  

**常用参数：**

  

| -p            | 用递归的方式删除指定的目录路径中的所有父级目录，非空则报错 |

| ------------- | ---------------------------------------------------------- |

| -v            | 显示命令的详细执行过程                                     |

| -- -- help    | 显示命令的帮助信息                                         |

| -- -- version | 显示命令的版本信息                                         |

  

**参考实例**

  

删除指定的空目录：

  

```bash

[root@Linux ~] # rmdir Documents

```

  

删除指定的空目录，及其内的子空目录：

  

```bash

[root@Linux ~] # rmdir -p Documents

```

  

删除指定的空目录，并显示删除的过程：

  

```bash

[root@Linux ~] # rmdir -v Documents

rmdir: removing directory, 'Documents'

```

  
  
  

## apt-get命令 – 管理服务软件(基于Debian分支)

  

apt-get命令来自于英文词组“Advanced Package Tool get”的缩写，其功能是用于管理服务软件。apt-get命令主要应用于**Debian、ubuntu等系统**，能够像`yum/dnf`软件仓库一样**自动下载、配置、安装、卸载服务软件**，用户只要准确提出需求就好~

  

**语法格式：**apt-get [参数] 软件名

  

**常用参数：**

  

| update       | 重新获取软件包列表   |

| ------------ | -------------------- |

| upgrade      | 更新软件             |

| install      | 安装软件             |

| remove       | 卸载软件             |

| autoremove   | 自动卸载不使用的软件 |

| source       | 下载源代码           |

| build-dep    | 编译依赖关系         |

| dist-upgrade | 更新系统             |

| purge        | 删除配置文件         |

| clean        | 清理垃圾文件         |

| check        | 检查是否损坏         |

  

**参考实例**�

  

安装指定的服务软件：

  

```bash

[root@Linux ~] # apt-get install vim    #vim是一款Linux文本编辑软件

```

  

更新软件列表：

  

```bash

[root@Linux ~] # apt-get update

```

  

卸载指定的服务软件：

  

```bash

[root@Linux ~] # apt-get remove vim

```

  

卸载指定的服务软件及配置信息：

  

```bash

[root@Linux ~] # apt-get -purge remove vim

```

  
  
  

## yum命令 – RPM的软件包管理器(基于Red-Hat分支)

  

**Red-Hat** Package Manager（红帽软件包管理器）简称RPM

  

yum命令来自于英文词组”YellowdogUpdater,Modified“的缩写，其功能是用于在Linux系统中基于RPM技术进行软件包的管理工作。yum技术通用于**RHEL、CentOS、Fedora、OpenSUSE等主流系统**，可以让系统管理人员交互式的自动化更新和管理软件包，实现从指定服务器自动下载、更新、删除软件包的工作。

  

yum软件仓库及命令能够自动处理软件依赖关系，一次性安装所需全部软件，无需繁琐的操作。

  

**语法格式：**yum [参数] 软件包

  

**常用参数：**

  

| -h           | 显示帮助信息                                   |

| ------------ | ---------------------------------------------- |

| -y           | 对所有的提问都回答“yes”                        |

| -c           | 指定配置文件                                   |

| -q           | 安静模式                                       |

| -v           | 详细模式                                       |

| -t           | 检查外部错误                                   |

| -d           | 设置调试等级（0-10）                           |

| -e           | 设置错误等级（0-10）                           |

| -R           | 设置yum处理一个命令的最大等待时间              |

| -C           | 完全从缓存中运行，而不去下载或者更新任何头文件 |

| install      | 安装rpm软件包                                  |

| update       | 更新rpm软件包                                  |

| check-update | 检查是否有可用的更新rpm软件包                  |

| remove       | 删除指定的rpm软件包                            |

| list         | 显示软件包的信息                               |

| search       | 检查软件包的信息                               |

| info         | 显示指定的rpm软件包的描述信息和概要信息        |

| clean        | 清理yum过期的缓存                              |

| shell        | 进入yum的shell提示符                           |

| resolvedep   | 显示rpm软件包的依赖关系                        |

| localinstall | 安装本地的rpm软件包                            |

| localupdate  | 显示本地rpm软件包进行更新                      |

| deplist      | 显示rpm软件包的所有依赖关系                    |

  

**参考实例**

  

清理原有的软件仓库信息缓存：

  

```

[root@Linux ~] # yum clean all

Updating Subscription Management repositories.

Unable to read consumer identity

This system is not registered to Red Hat Subscription Management. You can use subscription-manager to register.

12 files removed

```

  

建立最新的软件仓库信息缓存：

  

```

[root@Linux ~] # yum makecache

Updating Subscription Management repositories.

Unable to read consumer identity

This system is not registered to Red Hat Subscription Management. You can use subscription-manager to register.

AppStream                                        83 MB/s | 5.3 MB     00:00    

BaseOS                                           28 MB/s | 2.2 MB     00:00    

Last metadata expiration check: 0:00:01 ago on Mon 09 May 2022 11:43:41 PM CST.

Metadata cache created.

```

  

安装指定的服务及相关软件包：

  

```

[root@Linux ~] # yum install httpd

………………省略输出信息………………

```

  

更新指定的服务及相关软件包：

  

```

[root@Linux ~] # yum update httpd

………………省略输出信息………………

```

  

卸载指定的服务及相关软件包：

  

```

[root@Linux ~] # yum remove httpd

………………省略输出信息………………

```

  

显示可安装的软件包组列表：

  

```

[root@Linux ~] # yum grouplist

Updating Subscription Management repositories.

Unable to read consumer identity

  

Last metadata expiration check: 0:03:02 ago on Mon 09 May 2022 11:43:41 PM CST.

Available Environment Groups:

   Server

   Minimal Install

   Workstation

   Virtualization Host

   Custom Operating System

Installed Environment Groups:

   Server with GUI

Installed Groups:

   Container Management

   Headless Management

Available Groups:

   .NET Core Development

………………省略部分输出信息………………

```

  

显示指定服务的软件信息：

  

```

[root@Linux ~] # yum info httpd

Updating Subscription Management repositories.

Unable to read consumer identity

Last metadata expiration check: 0:07:21 ago on Mon 09 May 2022 11:43:41 PM CST.

Installed Packages

Name         : httpd

Version      : 2.4.37

Release      : 10.module+el8+2764+7127e69e

Arch         : x86_64

Size         : 4.3 M

Source       : httpd-2.4.37-10.module+el8+2764+7127e69e.src.rpm

Repo         : @System

From repo    : AppStream

Summary      : Apache HTTP Server

URL          : https://httpd.apache.org/

License      : ASL 2.0

Description  : The Apache HTTP Server is a powerful, efficient, and extensible

             : web server.

```

  
  
  

## dnf命令 – 新一代的RPM软件包管理器

  

dnf是新一代的rpm软件包管理器。首次出现在 Fedora 18 这个发行版中。而最近，它取代了yum，正式成为 Fedora 22 的包管理器。

  

dnf包管理器克服了yum包管理器的一些瓶颈，提升了包括用户体验，内存占用，依赖分析，运行速度等多方面的内容。dnf使用 RPM, libsolv 和 hawkey 库进行包管理操作。尽管它没有预装在 CentOS 和 RHEL 7 中，但你可以在使用yum的同时使用dnf 。

  

**语法格式:** dnf  [参数]

  

**常用参数：**

  

| repolist                    | 显示系统中可用的 DNF 软件库                                  |

| --------------------------- | ------------------------------------------------------------ |

| list                        | 列出用户系统上的所有来自软件库的可用软件包和所有已经安装在系统上的软件包 |

| search <包名>               | 搜索软件库中的软件包                                         |

| provides <路径>             | 查找某一文件的提供者                                         |

| info <包名>                 | 查看软件包详情                                               |

| install <包名>              | 安装软件包                                                   |

| update <包名>               | 升级软件包                                                   |

| check-update                | 检查系统软件包的更新                                         |

| update                      | 升级所有系统软件包                                           |

| remove                      | 删除软件包                                                   |

| autoremove                  | 删除无用孤立的软件包                                         |

| clean all                   | 删除缓存的无用软件包                                         |

| help <命令名>               | 获取有关某条命令的使用帮助                                   |

| help                        | 查看所有的dnf命令及其用途                                    |

| history                     | 查看dnf命令的执行历史                                        |

| grouplist                   | 查看所有的软件包组                                           |

| groupinstall <软件包组名称> | 安装一个软件包组                                             |

| groupupdate <软件包组名称>  | 升级一个软件包组中的软件包                                   |

| groupremove <软件包组名称>  | 删除一个软件包组                                             |

| distro-sync                 | 更新软件包到最新的稳定发行版                                 |

| reinstall <包名>            | 重新安装特定软件包                                           |

| downgrade <包名>            | 回滚某个特定软件的版本                                       |

| –version                    | 查看 DNF 包管理器版本                                        |

  

**参考实例**

  

回滚acpid软件包到特定版本：

  

```

[root@Linux ~] # dnf downgrade acpid

```

  

重新安装特定软件包：

  

```

[root@Linux ~] # dnf reinstall nano

```

  

查看所有的软件包组：

  

```

[root@Linux ~] # dnf grouplist

```

  
  
  

## pwd命令 – 显示当前工作目录的路径

  

pwd命令来自于英文词组”print working directory“的缩写，其功能是用于显示当前工作目录的路径，即显示所在位置的绝对路径。

  

在实际工作中，我们经常会在不同目录之间进行切换，为了防止”迷路“，可以使用pwd命令快速查看当前所处的工作目录路径，方便开展后续工作。

  

**语法格式**：pwd [参数]

  

**常用参数：**

  

| -L   | 显示逻辑路径 |

| ---- | ------------ |

|      |              |

  

**参考实例**

  

查看当前工作目录路径：

  

```bash

[root@Linux ~] # pwd

/root

```

  
  
  

## dpkg命令 – 管理软件安装包

  

dpkg命令来自于英文词组“Debian package”的缩写，其功能是用于管理软件安装包，在Debian系统中最常用的软件安装、管理、卸载的实用工具。

  

**语法格式：**dpkg  [参数]  软件包

  

**常用参数：**�

  

| -i   | 安装软件包             |

| ---- | ---------------------- |

| -r   | 删除软件包             |

| -l   | 显示已安装软件包列表   |

| -L   | 显示于软件包关联的文件 |

| -c   | 显示软件包内文件列表   |

  

**参考实例**�

  

安装指定的软件包：

  

```bash

[root@Linux ~] # dpkg -i package.deb

```

  

卸载指定的软件包：

  

```bash

[root@Linux ~] # dpkg -r package.deb  

```

  

列出当前已安装的软件列表：

  

```bash

[root@Linux ~] # dpkg -l

```

  

显示指定软件包内的文件信息：

  

```bash

[root@Linux ~] # dpkg -c package.deb

```

  
  
  

## mmove命令 – 移动文件或目录

  

mmove命令用于在MS-DOS文件系统中，移动文件或目录，或更改名称。mmove为**mtools**工具命令，模拟MS-DOS的move命令，可在MS-DOS文件系统中移动现有的文件或目录，或是更改现有文件或目录的名称。

  

**语法格式：** mmove [源文件或目录] [目标文件或目录]

  

**常用参数：**

  

| 源文件或目录   | 执行操作的源文件或目录路径     |

| -------------- | ------------------------------ |

| 目标文件或目录 | 执行操作后的目标文件或目录路径 |

  

**参考实例**

  

使用指令mmove将文件a.txt移动到目录dir中：

  

```bash

[root@Linux ~] # mmove a.txt dir

```

  

使用指令mmove将文件”autorun.bat”移动到目录”test”中 ：

  

```bash

[root@Linux ~] # mmove autorun.bat test

```

  

以上命令执行以后，指令mmove会将文件”autorun.bat”移动到指定目录”test”中。

  

使用指令mmove将文件test移动到目录”autorun.bat”中 ：

  

```bash

[root@Linux ~] # mmove test autorun.bat

```

  

注意：用户可以使用mdir指令查看移动后的文件或目录信息。

  

使用该命令前先查看原来的目录，得到如下结果：

  

```bash

[root@Linux ~] # mdir -/ a:\*

Volume in drive A has no label #加载信息  

Volume Serial Number is 13D2~055C  

Directory for A:/ #以下为目录信息  

#文件名目录大小 修改时间  

./TEST <DIR> 2009-09-23 16:59  

AUTORUN.INF 265 2009-09-23 16:53  

AUTORUN.BAT 43 2009-09-23 16:56  

3 files 308 bytes #统计总大小  

724 325 bytes free #剩余空间

```

  

使用mmove命令，并再次查看，结果如下：

  

```bash

[root@Linux ~] # mmove autorun.bat test

[root@Linux ~] # mdir -/ a:\*

Volume in drive A has no label #加载信息  

Volume Serial Number is 13D2~055C  

Directory for A:/ #以下为目录信息  

#文件名目录大小 修改时间  

./TEST <DIR> 2009-09-23 16:59  

AUTORUN.INF 265 2009-09-23 16:53  

2 files 265 bytes #统计总大小  

724 683 bytes free #剩余空间  

cmd@cmd-desktop:~$ mdir -/ a:\test\* #再次查看test目录中文件  

AUTORUN.BAT 43 2009-09-23 16:56  

1 files 43 bytes #统计总大小  

```

  
  
  

## file命令 – 识别文件类型

  

file命令的功能是用于识别文件的类型，也可以用来辨别一些内容的编码格式。由于Linux系统并不是像Windows系统那样通过扩展名来定义文件类型，因此用户无法直接通过文件名来进行分辨。file命令则是为了解决此问题，通过分析文件头部信息中的标识来显示文件类型，使用很方便。

  

**语法格式：**file [参数] 文件

  

**常用参数：**

  

| -b   | 列出辨识结果时，不显示文件名称 (简要模式) |

| ---- | ----------------------------------------- |

| -c   | 详细显示指令执行过程                      |

| -f   | 指定名称文件，显示多个文件类型信息        |

| -L   | 直接显示符号连接所指向的文件类别          |

| -m   | 指定魔法数字文件                          |

| -v   | 显示版本信息                              |

| -z   | 尝试去解读压缩文件的内容                  |

| -i   | 显示MIME类别                              |

  

**参考实例:**

  

查看某些文件的类型：

  

```bash

[root@Linux ~] # file a.cfg

a.cfg: ASCII text, with no line terminators

[root@Linux ~] # file /dev/sda

/dev/sda: block special (8/0)

[root@Linux ~] # file Documents

Documents: directory

[root@Linux ~] # file /bin/ls

/bin/ls: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=937708964f0f7e3673465d7749d6cf6a2601dea2, stripped, too many notes (256)

```

  

查看某个文件的类型，但不显示文件名：

  

```bash

[root@Linux ~] # file -b test.cfg

ASCII text

```

  

以MIME类别来显示某个文件的类型：

  

```bash

[root@Linux ~] # file -i test.cfg

test.cfg: text/plain; charset=us-ascii

```

  

查看某个符号链接文件（快捷方式）的类型，会提示目标文件名称：

  

```bash

[root@Linux ~] # file /dev/cdrom

/dev/cdrom: symbolic link to sr0

```

  

直接查看某个符号链接文件（快捷方式）所对应的目标文件的文件类型：

  

```bash

[root@Linux ~] # file -L /dev/cdrom

/dev/cdrom: block special (11/0)

```

  
  
  

## tar命令 – 压缩和解压缩文件

  

tar命令的功能是用于压缩和解压缩文件，能够制作出Linux系统中常见的.tar、.tar.gz、.tar.bz2等格式的压缩包文件。对于RHEL7、CentOS7版本以后的系统，解压时可以不加压缩格式参数（如z或j），系统能自动进行分析并解压。

  

把要传输的文件先进行压缩再进行传输，能够很好的提高工作效率，方便分享。

  

**语法格式：**tar [参数]  [压缩后名称]  [文件或目录]

  

**常用参数：**

  

| -A                     | 新增文件到以存在的备份文件                          |

| ---------------------- | --------------------------------------------------- |

| -B                     | 设置区块大小                                        |

| -c                     | 建立新的备份文件(**压缩**)                          |

| -C <目录>              | 仅压缩指定目录里的内容或解压缩到指定目录            |

| -d                     | 记录文件的差别                                      |

| -x                     | 从归档文件中提取文件(**解压**)                      |

| -t                     | 列出备份文件的内容                                  |

| -z                     | 通过gzip指令压缩/解压缩文件，文件名最好为*.tar.gz   |

| -Z                     | 通过compress指令处理备份文件                        |

| -f<备份文件>           | 指定备份文件                                        |

| -v                     | **显示指令执行过程**                                |

| -r                     | 添加文件到已经压缩的文件                            |

| -u                     | 添加改变了和现有的文件到已经存在的压缩文件          |

| -j                     | 通过bzip2指令压缩/解压缩文件，文件名最好为*.tar.bz2 |

| -v                     | 显示操作过程                                        |

| -l                     | 文件系统边界设置                                    |

| -k                     | 保留原有文件不覆盖                                  |

| -m                     | 保留文件不被覆盖                                    |

| -w                     | 确认压缩文件的正确性                                |

| -p                     | 保留原来的文件权限与属性                            |

| -P                     | 使用文件名的绝对路径，不移除文件名称前的“/”号       |

| -N <日期格式>          | 只将较指定日期更新的文件保存到备份文件里            |

| -- -exclude=<范本样式> | 排除符合范本样式的文件                              |

| -- -remove-files       | 归档/压缩之后删除源文件                             |

  

**参考实例**

  

使用gzip压缩格式对某个目录进行打包操作，显示压缩过程，压缩包规范后缀为.tar.gz：

  

```bash

[root@Linux ~] # tar czvf nnn.tar.gz /etc  #将etc目录下压缩为nnn.tar.gz

tar: Removing leading `/' from member names

/etc/

/etc/mtab

/etc/fstab

/etc/crypttab

/etc/resolv.conf

/etc/dnf/

………………省略部分输出信息………………

```

  

使用**bzip2**压缩格式对某个目录进行打包操作，显示压缩过程，**压缩包规范后缀为.tar.bz2**：

  

```bash

[root@Linux ~] # tar cjvf name.tar.bz2 /etc

tar: Removing leading `/' from member names

/etc/

/etc/mtab

/etc/fstab

/etc/crypttab

/etc/resolv.conf

/etc/dnf/

/etc/dnf/modules.d/

/etc/dnf/modules.d/container-tools.module

………………省略部分输出信息………………

```

  

将当前工作目录内所有以.cfg为后缀的文件打包，不进行压缩：

  

```bash

[root@Linux ~] # tar cvf backup1.tar *.cfg

anaconda-ks.cfg

initial-setup-ks.cfg

```

  

将当前工作目录内的所有以.cfg为后缀的文件打包，不进行压缩，并删除原始文件：

  

```bash

[root@Linux ~] # tar cvf backup2.tar *.cfg --remove-files

anaconda-ks.cfg

initial-setup-ks.cfg

```

  

解压某个压缩包到当前工作目录：

  

```bash

[root@Linux ~] # tar xvf backup1.tar

anaconda-ks.cfg

initial-setup-ks.cfg

```

  

解压某个压缩包到/etc目录：

  

```bash

[root@Linux ~] # tar xvf backup2.tar -C /etc

anaconda-ks.cfg

initial-setup-ks.cfg

```

  

查看某个压缩包内文件信息（无需解压）：

  

```bash

[root@Linux ~] # tar tvf backup3.tar

-rw------- root/root      1256 2022-05-18 08:42 anaconda-ks.cfg

-rw-r--r-- root/root      1585 2025-05-18 08:43 initial-setup-ks.cfg

```

  
  
  

## zip命令 – 压缩文件

  

zip命令的功能是用于压缩文件，解压命令为unzip。通过zip命令可以将文件打包成.zip格式的压缩包，里面会附含文件的名称、路径、创建时间、上次修改时间等等信息，与tar命令相似。

  

**语法格式：**zip [参数] [文件]

  

**常用参数：**

  

| -q             | 不显示指令执行过程                               |

| -------------- | ------------------------------------------------ |

| -r             | 递归处理，将指定目录下的所有文件和子目录一并处理 |

| -z             | 替压缩文件加上注释                               |

| -v             | 显示指令执行过程或显示版本信息                   |

| -d             | 更新压缩包内文件                                 |

| -n<字尾字符串> | 不压缩具有特定字尾字符串的文件                   |

  

**参考实例**

  

将指定目录及其内全部文件都打包成zip格式压缩包文件：

  

```bash

[root@Linux ~] # zip -r backup1.zip /etc

  adding: etc/fstab (deflated 45%)

  adding: etc/crypttab (stored 0%)

  adding: etc/resolv.conf (stored 0%)

  adding: etc/dnf/ (stored 0%)

  adding: etc/dnf/modules.d/ (stored 0%)

  adding: etc/dnf/modules.d/container-tools.module (deflated 17%)

  adding: etc/dnf/modules.d/llvm-toolset.module (deflated 14%)

………………省略部分输出信息………………

```

  

将当前工作目录内所有以.cfg为后缀的文件打包：

  

```bash

[root@Linux ~] # zip -r backup2.zip *.cfg

  adding: anaconda-ks.cfg (deflated 44%)

  adding: initial-setup-ks.cfg (deflated 44%)

```

  

更新压缩包文件中某个文件：

  

```bash

[root@Linux ~] # zip -dv backup2.zip anaconda-ks.cfg

1>1: updating: anaconda-ks.cfg (deflated 44%)

```

  
  
  

## fdisk命令 – 管理磁盘分区

  

fdisk命令来自于英文词组“Partition table manipulator for Linux”的缩写，其功能是用于管理磁盘的分区信息。fdisk命令可以用于对磁盘进行分区操作，用户可以根据实际情况进行合理划分，这样后期挂载和使用时会方便很多。

  

**语法格式：**fdisk [参数] [设备]

  

**常用参数：**

  

| -b   | 指定每个分区的大小                                           |

| ---- | ------------------------------------------------------------ |

| -l   | 列出指定的外围设备的分区表状况                               |

| -s   | 将指定的分区大小输出到标准输出上，单位为区块                 |

| -u   | 搭配”-l”参数列表，会用分区数目取代柱面数目，来表示每个分区的起始地址 |

| -v   | 显示版本信息                                                 |

  

**参考实例**

  

查看当前系统的分区情况：

  

```bash

[root@Linux ~] # fdisk -l

Disk /dev/sda: 40 GiB, 42949672960 bytes, 83886080 sectors

Disk model: VMware Virtual S

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x7b1c23a3

  

Device     Boot    Start      End  Sectors  Size Id Type

/dev/sda1  *        2048 81885183 81883136   39G 83 Linux

/dev/sda2       81887230 83884031  1996802  975M  5 Extended

/dev/sda5       81887232 83884031  1996800  975M 82 Linux swap / Solaris

```

  
  
  

## df命令 – 显示磁盘空间使用情况

  

df命令来自于英文词组”Disk Free“的缩写，其功能是用于显示系统上磁盘空间的使用量情况。df命令显示的磁盘使用量情况含可用、已有及使用率等信息，默认单位为Kb，建议使用-h参数进行单位换算，毕竟135M比138240Kb更利于阅读对吧~

  

**语法格式：** df [参数] [对象磁盘/分区]

  

**常用参数：**

  

| -a                | 显示所有系统文件                     |

| ----------------- | ------------------------------------ |

| -B <块大小>       | 指定显示时的块大小                   |

| -h                | 以容易阅读的方式显示                 |

| -H                | 以1000字节为换算单位来显示           |

| -i                | 显示索引字节信息                     |

| -k                | 指定块大小为1KB                      |

| -l                | 只显示本地文件系统                   |

| -t <文件系统类型> | 只显示指定类型的文件系统             |

| -T                | 输出时显示文件系统类型               |

| -- -sync          | 在取得磁盘使用信息前，先执行sync命令 |

  

**参考实例**

  

带有容量单位的显示系统全部磁盘使用量情况：

  

```bash

[root@Linux ~] # df -h

Filesystem             Size  Used Avail Use% Mounted on

devtmpfs               969M     0  969M   0% /dev

tmpfs                  984M     0  984M   0% /dev/shm

tmpfs                  984M  9.6M  974M   1% /run

tmpfs                  984M     0  984M   0% /sys/fs/cgroup

/dev/mapper/rhel-root   17G  3.9G   14G  23% /

/dev/sr0               6.7G  6.7G     0 100% /media/cdrom

/dev/sda1             1014M  152M  863M  15% /boot

tmpfs                  197M   16K  197M   1% /run/user/42

tmpfs                  197M  3.5M  194M   2% /run/user/0

```

  

带有容量单位的显示指定磁盘分区使用量情况：

  

```bash

[root@Linux ~] # df -h /boot

Filesystem      Size  Used Avail Use% Mounted on

/dev/sda1      1014M  152M  863M  15% /boot

```

  

显示系统中所有文件系统格式为xfs的磁盘分区使用量情况：

  

```bash

[root@Linux ~] # df -t xfs

Filesystem            1K-blocks    Used Available Use% Mounted on

/dev/mapper/rhel-root  17811456 4041320  13770136  23% /

/dev/sda1               1038336  155556    882780  15% /boot

```

  
  
  

## cat命令 – 在终端设备上显示文件内容

  

cat命令来自于英文单词concatenate的缩写，其功能是用于查看文件内容。在Linux系统中有很多用于查看文件内容的命令，例如more、tail、head……等等，每个命令都有各自的特点。cat命令适合查看内容较少的、纯文本的文件。

  

对于内容较多的文件，使用cat命令查看后会在屏幕上快速滚屏，用户往往看不清所显示的具体内容，只好按Ctrl+c键中断命令的执行，所以对于大文件，干脆用more命令吧~

  

**语法格式：**cat [参数] 文件

  

**常用参数：**

  

| -n        | 显示行数（空行也编号）                  |

| --------- | --------------------------------------- |

| -s        | 显示行数（多个空行算一个编号）          |

| -b        | 显示行数（空行不编号）                  |

| -E        | 每行结束处显示$符号                     |

| -T        | 将TAB字符显示为 ^I符号                  |

| -v        | 使用 ^ 和 M- 引用，除了 LFD 和 TAB 之外 |

| -e        | 等价于”-vE”组合                         |

| -t        | 等价于”-vT”组合                         |

| -A        | 等价于 -vET组合                         |

| --help    | 显示帮助信息                            |

| --version | 显示版本信息                            |

  

**参考实例**

  

查看某个文件的内容：

  

```sh

[root@linuxcool ~] # cat anaconda-ks.cfg

#version=RHEL8

ignoredisk --only-use=sda

autopart --type=lvm

# Partition clearing information

………………省略部分输出信息………………

```

  

查看某个文件的内容，并显示行号：

  

```sh

[root@linuxcool ~] # cat -n anaconda-ks.cfg

     1   #version=RHEL8

     2   ignoredisk --only-use=sda

     3   autopart --type=lvm

     4   # Partition clearing information

     5   clearpart --none --initlabel

     6   # Use graphical install

………………省略部分输出信息………………

```

  

搭配空设备文件和输出重定向操作符，将某个文件内容清空：

  

```sh

[root@linuxcool ~] # cat /dev/null > anaconda-ks.cfg

[root@linuxcool ~] # cat anaconda-ks.cfg

[root@linuxcool ~] #

```

  

持续写入文件内容，直到碰到EOF符后才会结束并保存：

  

```sh

[root@linuxcool ~] # cat > anaconda-ks.cfg << EOF

> Hello,World

> Linux!~

> EOF

[root@linuxcool ~] # cat anaconda-ks.cfg

Hello,World

Linux!~

```

  

搭配输出重定向操作符，将光盘设备制作成镜像文件：

  

```shell

[root@linuxcool ~] # cat /dev/cdrom > rhel.iso

[root@linuxcool ~] # ls rhel.iso  -lh

-rw-r--r--. 1 root root 6.7G May  2 00:43 rhel.iso

[root@linuxcool ~] # file rhel.iso

rhel.iso: DOS/MBR boot sector; partition 2 : ID=0xef, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 23128, 19888 sectors

```

  
  
  

## more命令 – 分页显示文本文件内容

  

more命令的功能是用于分页显示文本文件内容。如果文本文件中的内容较多较长，使用cat命令读取后则很难看清，这时使用more命令进行分页查看就更加合适了，可以把文本内容一页一页的显示在终端界面上，用户每按一次回车即向下一行，每按一次空格即向下一页，直至看完为止。

  

**语法格式：**more [参数] 文件

  

**常用参数：**

  

| -num      | 指定每屏显示的行数                                           |

| --------- | ------------------------------------------------------------ |

| -l        | more在通常情况下把 **^L** 当作特殊字符, 遇到这个字符就会暂停,-l选项可以阻止这种特性 |

| -f        | 计算实际的行数，而非自动换行的行数                           |

| -p        | 先清除屏幕再显示文本文件的剩余内容                           |

| -c        | 与-p相似，不滚屏，先显示内容再清除旧内容                     |

| -s        | 多个空行压缩成一行显示                                       |

| -u        | 禁止下划线                                                   |

| +/pattern | 在每个文档显示前搜寻该字(pattern)，然后从该字串之后开始显示  |

| +num      | 从第 num 行开始显示                                          |

  

**参考实例**

  

分页显示指定的文本文件内容：

  

```sh

[root@linuxcool ~] # more anaconda-ks.cfg

#version=RHEL8

ignoredisk --only-use=sda

autopart --type=lvm

# Partition clearing information

clearpart --none --initlabel

# Use graphical install

graphical

# Use CDROM installation media

cdrom

………………省略部分输出信息………………

```

  

先进行清屏操作，随后以每次10行内容的格式显示指定的文本文件内容：

  

```sh

[root@linuxcool ~] # more -c -10 anaconda-ks.cfg

#version=RHEL8

ignoredisk --only-use=sda

autopart --type=lvm

# Partition clearing information

clearpart --none --initlabel

# Use graphical install

graphical

repo --name="AppStream" --baseurl=file:///run/install/repo/AppStream

# Use CDROM installation media

cdrom

--More--(20%)

```

  

分页显示指定的文本文件内容，遇到连续两行以上空白行的情况，则以一行空白行显示：

  

```sh

[root@linuxcool ~] # more -s anaconda-ks.cfg

………………省略输出信息………………

```

  

从第10行开始，分页显示指定的文本文件内容：

  

```sh

[root@linuxcool ~] # more +10 anaconda-ks.cfg

cdrom

# Keyboard layouts

keyboard --vckeymap=us --xlayouts='us'

# System language

lang en_US.UTF-8

  

# Network information

network  --bootproto=static --device=ens160 --ip=192.168.10.10 --netmask=255.255.255.0 --onboot=off --ipv6=auto --activate

network  --hostname=linuxprobe.com

# Root password

………………省略部分输出信息………………

```

  
  
  

## find命令 – 根据路径和条件搜索指定文件

  

find命令的功能是根据给定的路径和条件查找相关文件或目录，可以使用的参数很多，并且支持正则表达式，结合管道符后能够实现更加复杂的功能，是系统管理员和普通用户日常工作必须掌握的命令之一。

  

find命令通常进行的是从根目录（/）开始的全盘搜索，有别于whereis、which、locate……等等的有条件或部分文件的搜索。对于服务器负载较高的情况，建议不要在高峰时期使用find命令的模糊搜索，会相对消耗较多的系统资源。

  

**语法格式**：find [路径] [参数]

  

**常用参数**：

  

| -name             | 匹配名称                                                     |

| ----------------- | ------------------------------------------------------------ |

| -perm             | 匹配权限（mode为完全匹配，-mode为包含即可）                  |

| -user             | 匹配所有者                                                   |

| -group            | 匹配所有组                                                   |

| -mtime -n +n      | 匹配修改内容的时间（-n指n天以内，+n指n天以前）               |

| -atime -n +n      | 匹配访问文件的时间（-n指n天以内，+n指n天以前）               |

| -ctime -n +n      | 匹配修改文件权限的时间（-n指n天以内，+n指n天以前）           |

| -nouser           | 匹配无所有者的文件                                           |

| -nogroup          | 匹配无所有组的文件                                           |

| -newer f1 !f2     | 匹配比文件f1新但比f2旧的文件                                 |

| -type b/d/c/p/l/f | 匹配文件类型（后面的字幕字母依次表示块设备、目录、字符设备、管道、链接文件、文本文件） |

| -size             | 匹配文件的大小（+50KB为查找超过50KB的文件，而-50KB为查找小于50KB的文件） |

| -prune            | 忽略某个目录                                                 |

| -exec …… {}\;     | 后面可跟用于进一步处理搜索结果的命令                         |

  

**参考实例**

  

全盘搜索系统中所有以.conf结尾的文件：

  

```sh

[root@linuxcool ~] # find / -name *.conf

/run/tmpfiles.d/kmod.conf

/etc/resolv.conf

/etc/dnf/dnf.conf

/etc/dnf/plugins/copr.conf

/etc/dnf/plugins/debuginfo-install.conf

/etc/dnf/plugins/product-id.conf

/etc/dnf/plugins/subscription-manager.conf

………………省略部分输出信息………………

```

  

在/etc目录中搜索所有大于1M大小的文件：

  

```sh

[root@linuxcool ~] # find /etc -size +1M

/etc/selinux/targeted/policy/policy.31

/etc/udev/hwdb.bin

```

  

在/home目录中搜索所有属于指定用户的文件：

  

```sh

[root@linuxcool ~] # find /home -user linuxprobe

/home/linuxprobe

/home/linuxprobe/.mozilla

/home/linuxprobe/.mozilla/extensions

/home/linuxprobe/.mozilla/plugins

/home/linuxprobe/.bash_logout

/home/linuxprobe/.bash_profile

/home/linuxprobe/.bashrc

```

  

列出当前工作目录中的所有文件、目录以及子文件信息：

  

```sh

[root@linuxcool ~] # find .

.

./.bash_logout

./.bash_profile

./.bashrc

./.cshrc

./.tcshrc

./anaconda-ks.cfg

………………省略部分输出信息………………

```

  

在/var/log目录下搜索所有指定后缀的文件，后缀不需要大小写。

  

```sh

[root@linuxcool ~] # find /var/log -iname "*.log"

/var/log/audit/audit.log

/var/log/rhsm/rhsmcertd.log

/var/log/rhsm/rhsm.log

/var/log/sssd/sssd.log

/var/log/sssd/sssd_implicit_files.log

/var/log/sssd/sssd_nss.log

/var/log/sssd/sssd_kcm.log

/var/log/tuned/tuned.log

/var/log/anaconda/anaconda.log

/var/log/anaconda/X.log

………………省略部分输出信息………………

```

  

在/var/log目录下搜索所有后缀不是.log的文件：

  

```sh

[root@linuxcool ~] # find /var/log ! -name "*.log"

/var/log

/var/log/lastlog

/var/log/README

/var/log/private

/var/log/wtmp

/var/log/btmp

/var/log/samba

```

  

搜索当前工作目录中的所有近7天被修改过的文件：

  

```sh

[root@linuxcool ~] # find . -mtime +7

./.bash_logout

./.bash_profile

./.bashrc

./.cshrc

./.tcshrc

………………省略部分输出信息………………

```

  

全盘搜索系统中所有类型为目录，且权限为1777的目录文件：

  

```sh

[root@linuxcool ~] # find / -type d -perm 1777

/dev/mqueue

/dev/shm

/var/tmp

/tmp

………………省略部分输出信息………………

```

  

全盘搜索系统中所有类型为普通文件，且可以执行的文件信息：

  

```sh

[root@linuxcool ~] # find / -type f -perm /a=x

/boot/vmlinuz-4.18.0-80.el8.x86_64

/boot/vmlinuz-0-rescue-c8b04558503242459d908c6c22a2d481

/etc/X11/xinit/xinitrc.d/50-systemd-user.sh

/etc/X11/xinit/xinitrc.d/00-start-message-bus.sh

/etc/X11/xinit/xinitrc.d/localuser.sh

/etc/X11/xinit/Xclients

/etc/X11/xinit/Xsession

/etc/X11/xinit/xinitrc

………………省略部分输出信息………………

```

  

全盘搜索系统中所有后缀为.mp4的文件，并删除所有查找到的文件：

  

```sh

[root@linuxcool ~] # find / -name "*.mp4" -exec rm -rf {} \;

```

  
  
  

## which命令 – 查找命令文件

  

which命令的功能是用于查找命令文件，能够快速搜索二进制程序所对应的位置。如果我们既不关心同名文件（find与locate），也不关心命令所对应的源代码和帮助文件（whereis），仅仅是想找到命令本身所在的路径，那么这个which命令就太合适了。

  

**语法格式：**which [参数] 文件

  

**常用参数：**

  

| -n   | 指定文件名长度（不含路径） |

| ---- | -------------------------- |

| -p   | 指定文件名长度（含路径）   |

| -w   | 指定输出时栏位的宽度       |

| -V   | 显示版本信息               |

  

**参考实例**

  

查找某个指定命令文件所在位置：

  

```sh

[root@linuxcool ~] # which reboot

/usr/sbin/reboot

```

  

查找多个指定命令文件所在位置：

  

```sh

[root@linuxcool ~] # which shutdown poweroff

/usr/sbin/shutdown

/usr/sbin/poweroff

```

  
  
  

## ls命令 – 显示指定工作目录下的文件及属性信息

  

ls是最常被使用到的Linux命令之一，来自于英文单词list的缩写，也正如list单词的英文意思，其功能是列举出指定目录下的文件名称及其属性。

  

默认不加参数的情况下，ls命令会列出当前工作目录中的文件信息，经常与cd和pwd命令搭配使用，十分方便。而带上参数后，我们则可以做更多的事情，作为最基础、最频繁使用的命令，有必要仔细了解下其常用功能。

  

**语法格式:** ls [参数] [文件]

  

**常用参数：**

  

| -a      | 显示所有文件及目录 (包括以“.”开头的隐藏文件)     |

| ------- | ------------------------------------------------ |

| -l      | 使用长格式列出文件及目录的详细信息               |

| -r      | 将文件以相反次序显示(默认依英文字母次序)         |

| -t      | 根据最后的修改时间排序                           |

| -A      | 同 -a ，但不列出 “.” (当前目录) 及 “..” (父目录) |

| -S      | 根据文件大小排序                                 |

| -R      | 递归列出所有子目录                               |

| -d      | 查看目录的信息，而不是里面子文件的信息           |

| -i      | 输出文件的inode节点信息                          |

| -m      | 水平列出文件，以逗号间隔                         |

| -X      | 按文件扩展名排序                                 |

| --color | 输出信息中带有着色效果                           |

  

**参考实例**

  

输出当前目录中的文件（默认不含隐藏文件）：

  

```bash

[root@Linux ~] # ls

Desktop   Downloads  Music   Public   Videos

```

  

输出当前目录中的文件（含隐藏文件）：

  

```bash

[root@Linux ~] # ls -a

.bashrc  Documents       Music      Videos

 .cache   Downloads      Pictures   .viminfo

test.cfg  .config  .esd_auth             .pki

.bash_history    .cshrc   .ICEauthority         Public

.bash_logout     .dbus    initial-setup-ks.cfg  .tcshrc

.bash_profile    Desktop  .local                Templates

```

  

输出文件的长格式，包含属性详情信息：

  

```bash

[root@Linux ~] # ls -l

total 8

-rw-------. 1 root root 1430 Dec 14 08:05 test.cfg

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Desktop

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Documents

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Downloads

-rw-r--r--. 1 root root 1585 Dec 14 08:34 initial-setup-ks.cfg

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Music

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Pictures

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Public

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Templates

drwxr-xr-x. 2 root root    6 Dec 14 08:37 Videos

```

  

![[../ASLant_Files/a0563078b1a4006e9f235c725fa5d991_MD5.jpg]]

  

![[../ASLant_Files/6296485a883dec2810b30a8c7cbc9f05_MD5.jpg]]

  

输出指定目录中的文件列表：

  

```sh

[root@Linux ~] # ls /etc

adjtime                     hosts                     pulse

aliases                     hosts.allow               qemu-ga

alsa                        hosts.deny                qemu-kvm

alternatives                hp                        radvd.conf

anacrontab                  idmapd.conf               ras

asound.conf                 init.d                    rc0.d

at.deny                     inittab                   rc1.d

………………省略部分输出信息………………

```

  

输出文件名称及inode属性块号码：

  

```sh

[root@Linux ~] # ls -i

35290115 test.cfg  35290137 initial-setup-ks.cfg  35290164 Templates

 1137391 Desktop          17840039 Music                 51609597 Videos

 1137392 Documents        35290165 Pictures

17840038 Downloads        51609596 Public

```

  

搭配通配符一起使用，输出指定目录中所有以sd开头的文件名称：

  

```sh

[root@Linux ~] # ls /dev/sd*

/dev/sda  /dev/sda1  /dev/sda2

```

  

依据文件大小进行排序，输出指定目录中文件属性详情信息：

  

```sh

[root@Linux ~] # ls -Sl /etc

total 1348

-rw-r--r--.  1 root root    692241 Sep 10  2018 services

-rw-r--r--.  1 root root     66482 Dec 14 08:34 ld.so.cache

-rw-r--r--.  1 root root     60352 May 11  2017 mime.types

-rw-r--r--.  1 root dnsmasq  26843 Aug 12  2018 dnsmasq.conf

-rw-r--r--.  1 root root     25696 Dec 12  2018 brltty.conf

-rw-r--r--.  1 root root      9450 Aug 12  2018 nanorc

-rw-r--r--.  1 root root      7265 Dec 14 08:03 kdump.conf

-rw-------.  1 tss  tss       7046 Aug 13  2018 tcsd.conf

………………省略部分输出信息………………

```

  
  
  

## ssh命令 – 安全的远程连接服务器

  

ssh命令的功能是用于安全的远程连接服务器主机系统，作为openssh套件中的客户端连接工具，ssh命令可以让我们轻松的基于ssh加密协议进行远程主机访问，从而实现对远程服务器的管理工作。

  

**语法格式:** ssh [参数] 远程主机

  

**常用参数：**

  

| -1           | 强制使用ssh协议版本1                                         |

| ------------ | ------------------------------------------------------------ |

| -2           | 强制使用ssh协议版本2                                         |

| -4           | 强制使用IPv4地址                                             |

| -6           | 强制使用IPv6地址                                             |

| -A           | 开启认证代理连接转发功能                                     |

| -a           | 关闭认证代理连接转发功能                                     |

| -b<IP地址>   | 使用本机指定的地址作为对位连接的源IP地址                     |

| -C           | 请求压缩所有数据                                             |

| -F<配置文件> | 指定ssh指令的配置文件，默认的配置文件为“/etc/ssh/ssh_config” |

| -f           | 后台执行ssh指令                                              |

| -g           | 允许远程主机连接本机的转发端口                               |

| -i<身份文件> | 指定身份文件（即私钥文件）                                   |

| -l<登录名>   | 指定连接远程服务器的登录用户名                               |

| -N           | 不执行远程指令                                               |

| -o<选项>     | 指定配置选项                                                 |

| -p<端口>     | 指定远程服务器上的端口                                       |

| -q           | 静默模式，所有的警告和诊断信息被禁止输出                     |

| -X           | 开启X11转发功能                                              |

| -x           | 关闭X11转发功能                                              |

| -y           | 开启信任X11转发功能                                          |

  

**参考实例**

  

基于ssh协议，远程访问服务器主机系统：

  

```sh

[root@linuxcool ~] # ssh 192.168.10.10

The authenticity of host '192.168.10.10 (192.168.10.10)' can't be established.

ECDSA key fingerprint is SHA256:ZEjdfRjQV8pVVfu0TSYvDP5UvOHuuogMQSDUgLPG3Kc.

Are you sure you want to continue connecting (yes/no)? yes

  

Warning: Permanently added '192.168.10.10' (ECDSA) to the list of known hosts.

root@192.168.10.10's password: 此处输入远程服务器管理员密码

Activate the web console with: systemctl enable --now cockpit.socket

  

Last login: Tue Dec 14 08:49:08 2022

[root@linuxprobe ~] #

```

  

使用指定的用户身份登录远程服务器主机系统：

  

```sh

[root@linuxcool ~] # ssh -l linuxprobe 192.168.10.10

linuxprobe@192.168.10.10's password: 此处输入指定用户的密码

Activate the web console with: systemctl enable --now cockpit.socket

  

[linuxprobe@linuxprobe ~]$

```

  

登录远程服务器主机系统后执行一条命令：

  

```sh

[root@linuxcool ~] # ssh 192.168.10.10 "free -m"

root@192.168.10.10's password: 此处输入远程服务器管理员密码

              total        used        free      shared  buff/cache   available

Mem:           1966        1359          76          21         530         407

Swap:          2047           9        2038

```

  

强制使用v1版本的ssh加密协议连接远程服务器主机：

  

```sh

[root@linuxcool ~] # ssh -1 192.168.10.10

```

  
  
  

## netstat命令 – 显示网络状态

  

netstat命令来自于英文词组”network statistics“的缩写，其功能是用于显示各种网络相关信息，例如网络连接状态、路由表信息、接口状态、NAT、多播成员等等。

  

netstat命令不仅应用于Linux系统，而且在Windows XP、Windows 7、Windows 10及Windows 11中均已默认支持，并且可用参数也相同，有经验的运维人员可以直接上手。

  

**语法格式：**netstat [参数]

  

**常用参数：**

  

| -a   | 显示所有连线中的Socket                   |

| ---- | ---------------------------------------- |

| -p   | 显示正在使用Socket的程序识别码和程序名称 |

| -l   | 仅列出在监听的服务状态                   |

| -t   | 显示TCP传输协议的连线状况                |

| -u   | 显示UDP传输协议的连线状况                |

| -i   | 显示网络界面信息表单                     |

| -r   | 显示路由表信息                           |

| -n   | 直接使用IP地址，不通过域名服务器         |

  

**参考实例**

  

显示系统网络状态中的所有连接信息：

  

```sh

[root@linuxcool ~] # netstat -a

Active Internet connections (servers and established)

Proto Recv-Q Send-Q Local Address           Foreign Address         State      

tcp        0      0 0.0.0.0:http            0.0.0.0:*               LISTEN    

tcp        0      0 0.0.0.0:https           0.0.0.0:*               LISTEN    

tcp        0      0 0.0.0.0:ms-wbt-server   0.0.0.0:*               LISTEN    

```

  

显示系统网络状态中的UDP连接信息：

  

```sh

[root@linuxcool ~] # netstat -nu

Active Internet connections (w/o servers)

Proto Recv-Q Send-Q Local Address           Foreign Address         State      

udp        0      0 172.19.226.238:68       172.19.239.253:67       ESTABLISHED

```

  

显示系统网络状态中的UDP连接端口号使用信息：

  

```sh

[root@linuxcool ~] # netstat -apu

Active Internet connections (servers and established)

Proto Recv-Q Send-Q Local Address    Foreign Address       State    PID/Program name    

udp        0      0 linuxcool:bootpc _gateway:bootps  ESTABLISHED   1024/NetworkManager

udp        0      0 localhost:323           0.0.0.0:*               875/chronyd        

udp6       0      0 localhost:323           [::]:*                  875/chronyd

```

  

显示网卡当前状态信息：

  

```sh

[root@linuxcool~] # netstat -i

Kernel Interface table

Iface             MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg

eth0             1500    31945      0      0 0         39499      0      0      0 BMRU

lo              65536        0      0      0 0             0      0      0      0 LRU

```

  

显示网络路由表状态信息：

  

```sh

[root@linuxcool ~] # netstat -r

Kernel IP routing table

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

default         _gateway        0.0.0.0         UG        0 0          0 eth0

172.19.224.0    0.0.0.0         255.255.240.0   U         0 0          0 eth0

```

  

找到某个服务所对应的连接信息：

  

```sh

[root@linuxcool ~] # netstat -ap | grep ssh

unix  2      [ ]         STREAM     CONNECTED     89121805 203890/sshd: root [  

unix  3      [ ]         STREAM     CONNECTED     27396    1754/sshd            

unix  3      [ ]         STREAM     CONNECTED     89120965 203890/sshd: root [  

unix  2      [ ]         STREAM     CONNECTED     89116510 203903/sshd: root@p  

unix  2      [ ]         STREAM     CONNECTED     89121803 203890/sshd: root [  

unix  2      [ ]         STREAM     CONNECTED     29959    1754/sshd            

unix  2      [ ]         DGRAM                    89111175 203890/sshd: root [  

unix  3      [ ]         STREAM     CONNECTED     89120964 203903/sshd: root@p  

```

  
  
  

## wget命令 – 下载网络文件

  

wget命令来自于英文词组”web get“的缩写，其功能是用于从指定网址下载网络文件。wget命令非常稳定，一般即便网络波动也不会导致下载失败，而是不断的尝试重连，直至整个文件下载完毕。

  

wget命令支持如HTTP、HTTPS、FTP等常见协议，可以在命令行中直接下载网络文件。

  

**语法格式：** wget [参数] 网址

  

**常用参数：**

  

| -V                  | 显示版本信息       |

| ------------------- | ------------------ |

| -h                  | 显示帮助信息       |

| -b                  | 启动后转入后台执行 |

| -c                  | 支持断点续传       |

| -O                  | 定义本地文件名     |

| -e <命令>           | 执行指定的命令     |

| --limit-rate=<速率> | 限制下载速度       |

  

**参考实例**

  

下载指定的网络文件：

  

```sh

[root@linuxprobe ~] # wget https://www.linuxprobe.com/docs/LinuxProbe.pdf

--2022-05-11 18:36:42--  https://www.linuxprobe.com/docs/LinuxProbe.pdf

Resolving www.linuxprobe.com (www.linuxprobe.com)... 58.218.215.124

Connecting to www.linuxprobe.com (www.linuxprobe.com)|58.218.215.124|:443... connected.

HTTP request sent, awaiting response... 200 OK

Length: 17676281 (17M) [application/pdf]

Saving to: ‘LinuxProbe.pdf’

  

LinuxProbe.pdf    100%[=================================>]  16.86M  30.0MB/s    in 0.6s    

  

2022-05-11 18:36:42 (30.0 MB/s) - ‘LinuxProbe.pdf’ saved [17676281/17676281]

```

  

下载指定的网络文件，并定义保存在本地的文件名称：

  

```sh

[root@linuxcool ~] # wget -O Book.pdf https://www.linuxprobe.com/docs/LinuxProbe.pdf

```

  

下载指定的网络文件，限速最高每秒300k：

  

```sh

[root@linuxcool ~] # wget --limit-rate=300k https://www.linuxprobe.com/docs/LinuxProbe.pdf

```

  

启用断点续传技术下载指定的网络文件：

  

```sh

[root@linuxcool ~] # wget -c https://www.linuxprobe.com/docs/LinuxProbe.pdf

```

  

下载指定的网络文件，将任务放至后台执行：

  

```sh

[root@linuxcool ~] # wget -b https://www.linuxprobe.com/docs/LinuxProbe.pdf

Continuing in background, pid 237616.

Output will be written to ‘wget-log’.

```

  
  
  

## bc命令 – 数字计算器

  

bc命令来自于英文词组“Binary Calculator”的缩写，中文译为二进制计算器，其功能是用于数字计算。Bash解释器仅能够进行整数计算，而不支持浮点运算，因此有时要用到bc命令进行高精度的数字计算工作。

  

**语法格式：**bc [选项]

  

**常用参数：**

  

| -i   | 强制进入交互式模式       |

| ---- | ------------------------ |

| -l   | 定义使用的标准数学库     |

| -w   | 定义使用的标准数学库     |

| -q   | 打印正常的GNU bc环境信息 |

  

**参考实例**

  

计算得出指定的浮点数乘法结果：

  

```sh

[root@linuxcool ~] # bc

1.2345*3

3.7035

```

  

设定计算精度为小数点后3位，取浮点数除法结果：

  

```sh

[root@linuxcool ~] # bc

scale=3

3/8

.375

```

  

分别计算整数的平方与平方根结果：

  

```sh

[root@linuxcool ~] # bc

10^10

10000000000

sqrt(100)

10.000

```

  
  
  

## 参考书籍：[《Linux就该这么学-刘遄》](https://www.aliyundrive.com/s/VX8xQV7EQCs)