## 所需文件
----    
- [Firmware底包]()  
- [Armbian 5.88]()  
- [Armbian 5.9.0]()  
- [烧录工具B]()  
- [SSH连接工具]()   

## 首先刷入 Armbian 5.88（直接刷 Armbian 5.9.0 是刷不进去的）   
----


## 接着刷入 ARMbian 5.9.0 启用千兆网口   
----
> 默认账户：root
>
> 默认密码：1234        


- 在路由器中找到 Armbian 的 ip 地址（amol） 


![[../ASLant_Files/5bba03a13253e4db0fd4cd6d11e85778_MD5.jpg]]

### 使用 SSH 工具连接 
----
- 连接后    
  
> 更改新密码：ASLant 123     
> 选择语言：162     
> Ctrl + C      


### 刷入到 ` EMMC ` 中：  
----
```sh
cd /boot/install    

sudo ./install.sh

等待.....
``` 

![[../ASLant_Files/3bcc068f898226c36ccc839c56360414_MD5.jpg]]  

![[../ASLant_Files/412a34ff71542cd46eb62a1fccf25d74_MD5.jpg]]   


### 完成后，拔电源，拔掉 U 盘。
----
ARMbian 系统刷入到板载芯片完成。     


### 设置固定 IP  
----

![[../ASLant_Files/24993425526d3ff03e9dd10b476f3904_MD5.jpg]]       

### 换 Debian 源  
----    

```sh
mv /etc/apt/sources.list /etc/apt/sources.list.bk
nano /etc/apt/sources.list
```     

### Debian 源
```vim
deb https://mirrors.ustc.edu.cn/debian/ bullseye main non-free contrib
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye main non-free contrib
deb https://mirrors.ustc.edu.cn/debian-security/ bullseye-security main
deb-src https://mirrors.ustc.edu.cn/debian-security/ bullseye-security main
deb https://mirrors.ustc.edu.cn/debian/ bullseye-updates main non-free contrib
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye-updates main non-free contrib
deb https://mirrors.ustc.edu.cn/debian/ bullseye-backports main non-free contrib
deb-src https://mirrors.ustc.edu.cn/debian/ bullseye-backports main non-free contrib
```     

```sh
apt-get update && apt-get upgrade
更新软件    

``` 


![[../ASLant_Files/5b53af5ba852632e4139c430b75d304a_MD5.jpg]]    

![[../ASLant_Files/58a67b7b77f6b5b8ebca8b2371173683_MD5.jpg]]   



### 安装 Docker  
----
```sh   

apt install docker.io

``` 

### 甜糖科技    
----
```sh
wget https://gitee.com/pj-xiaoyu/download/raw/main/TTarm32.sh && sudo bash TTarm32.sh
```

![[../ASLant_Files/14a13e14ba421c2db0c24c6709529aa3_MD5.jpg]]   


```sh   
打开网卡混杂模式
ip link set eth0 promisc on 

创建网络
docker network create -d macvlan --subnet=192.168.100.0/24 --gateway=192.168.100.1 -o parent=eth0 macnet
自己根据 玩客云 所在网段修改，如：玩客云IP:192.168.1.175，则192.168.0.0/24 改成 192.168.1.0/24，192.168.0.1改成主路由地址]
拉取镜像
docker pull jyhking/onecloud:1.1
docker run -itd --name=OneCloud --restart=always --network=macnet --privileged=true jyhking/onecloud:1.1 /sbin/init
安装阿里云webdev代码

wget https://github.com/messense/aliyundrive-webdav/releases/download/v1.8.7/aliyundrive-webdav_1.8.7-1_arm_cortex-a5_vfpv4.ipk
wget https://github.com/messense/aliyundrive-webdav/releases/download/v1.8.7/luci-app-aliyundrive-webdav_1.8.7_all.ipk
wget https://github.com/messense/aliyundrive-webdav/releases/download/v1.8.7/luci-i18n-aliyundrive-webdav-zh-cn_1.8.7-1_all.ipk
opkg install aliyundrive-webdav_1.8.7-1_arm_cortex-a5_vfpv4.ipk
opkg install luci-app-aliyundrive-webdav_1.8.7_all.ipk
opkg install luci-i18n-aliyundrive-webdav-zh-cn_1.8.7-1_all.ipk
``` 
