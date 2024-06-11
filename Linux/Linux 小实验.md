### 实验_1

> [!ERROR] 有一个非常重要的文件（sources. List）但是你忘了它在哪了，你依稀记得它在 /etc/ 目录下，现在要你把这个文件找出来，然后设置成自己（shiyanlou 用户）可以访问，但是其他用户并不能访问。

```sh
sudo find /etc -name sources.list

# sudo：以超级用户（root）权限执行命令。
# find：用于在文件系统中搜索文件和目录的命令。
# /etc：指定搜索的起始目录，这里是根目录下的/etc目录，通常包含系统的配置文件。
# -name sources.list：指定要搜索的文件名，这里是搜索名为 "sources.list" 的文件。
这条命令的目的是在整个/etc目录下搜索名为 "sources.list" 的文件，以查找软件包管理系统的软件源配置文件。

sudo chown shiyanlou /etc/apt/sources.list

# sudo：以超级用户权限执行命令。
# chown：用于更改文件或目录的所有者（owner）。
# shiyanlou：指定新的所有者用户名。
# /etc/apt/sources.list：要更改所有者的文件路径，这是软件源配置文件的路径。
此命令的目的是将文件 "/etc/apt/sources.list" 的所有权更改为用户 "shiyanlou"。通常，这是为了让用户 "shiyanlou" 具有编辑该文件的权限。

sudo chmod 600 /etc/apt/sources.list

# sudo：以超级用户权限执行命令。
# chmod：用于更改文件或目录的权限。
# 600：指定新的文件权限，其中 "6" 表示文件所有者有读（4）和写（2）权限，没有执行权限。
此命令的目的是将文件 "/etc/apt/sources.list" 的权限设置为只允许所有者读取和编辑该文件，而其他用户没有访问权限。这是出于安全考虑，以确保只有授权的用户可以修改软件源配置文件，因为该文件包含系统软件包管理器的重要信息。

```