# 命令
**dd 命令用于读取、转换并输出数据。**
dd 可从标准输入或文件中读取数据，根据指定的格式来转换数据，再输出到文件、设备或标准输出。
## 参数说明:

> [!NOTE] info
> if=文件名：输入文件名，默认为标准输入。即指定源文件。
> of=文件名：输出文件名，默认为标准输出。即指定目的文件。
> ibs=bytes：一次读入bytes个字节，即指定一个块大小为bytes个字节。
> obs=bytes：一次输出bytes个字节，即指定一个块大小为bytes个字节。
> bs=bytes：同时设置读入/输出的块大小为bytes个字节。
> cbs=bytes：一次转换bytes个字节，即指定转换缓冲区大小。
> skip=blocks：从输入文件开头跳过blocks个块后再开始复制。
> seek=blocks：从输出文件开头跳过blocks个块后再开始复制。
> count=blocks：仅拷贝blocks个块，块大小等于ibs指定的字节数。
> conv=<关键字>，关键字可以有以下11种：
> conversion：用指定的参数转换文件。
> ascii：转换ebcdic为ascii
> ebcdic：转换ascii为ebcdic
> ibm：转换ascii为alternate ebcdic
> block：把每一行转换为长度为cbs，不足部分用空格填充
> unblock：使每一行的长度都为cbs，不足部分用空格填充
> lcase：把大写字符转换为小写字符
> ucase：把小写字符转换为大写字符
> swap：交换输入的每对字节
> noerror：出错时不停止
> notrunc：不截短输出文件
> sync：将每个输入块填充到ibs个字节，不足部分用空（NUL）字符补齐。
> --help：显示帮助信息
> --version：显示版本信息
> 

## 实例
- 在Linux 下制作启动盘，可使用如下命令：
  ```sh
  dd if=boot.img of=/dev/fd0 bs=1440k 
  ```
- 拷贝镜像
  ```sh
  sudo dd if=/dev/sda of=Backup.img bs=4M status=progress
  ```
# 批量脚本
```sh
#!/bin/bash

# 镜像文件路径
IMAGE_FILE="xtark.img"

# 检查镜像文件是否存在
if [ ! -f "$IMAGE_FILE" ]; then
    echo "错误：镜像文件 $IMAGE_FILE 不存在。"
    exit 1
fi

# 定义并行任务数
PARALLELISM=4

# 获取当前系统上所有的磁盘设备，假设磁盘设备名称为 /dev/sd[a-z]
DISKS=$(ls /dev/sd* | grep -E '/dev/sd[a-z]$')

# 检查是否有磁盘设备
if [ -z "$DISKS" ]; then
    echo "错误：没有找到磁盘设备。"
    exit 1
fi

# 使用xargs并行执行dd命令
echo "$DISKS" | xargs -n 1 -P $PARALLELISM -I % sh -c '
    echo "正在将镜像复制到 % ..."
    sudo dd if="'"$IMAGE_FILE"'" of="%" status=progress && echo "完成复制到 %。"
'

echo "所有磁盘复制任务已启动。"
```
