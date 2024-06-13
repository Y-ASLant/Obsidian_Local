# Linux 

> [!BUG] [Python 源码](https://www.python.org/downloads/source/)

### 一键安装

> [!danger] 一键安装脚本
> ```sh
>curl -sSL https://aslant.top/Cloud/OneDrive/Linux/shell/Python_install.sh | bash
> ```

### 手动安装

###### 下载源码
```sh
wget https://www.python.org/ftp/python/3.12.3/Python-3.12.3.tar.xz
```

###### 解压
```sh
tar -xvf Python-3.12.3.tar.xz
```

###### 进入解压后的文件夹
```sh
cd Python-3.12.3
```

###### 根据当前系统的环境和配置来生成一个特定于该系统的 Makefile
```sh
./configure
```

###### 编译安装 (全速)
```sh
make -j$(nproc) && make install
```

###### 检查 Python3 是否正常可用：
```sh
python3 -V
```

![[../../../ASLant_Files/d19cd0e11399e15b584dec5e863dc053_MD5.jpg]]

# Windows

> [!BUG] [Download](https://www.python.org/downloads/windows/)
