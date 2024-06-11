# 自定义命令
### 方法一
```sh
vim ~/.bashrc
```

文件末尾添加
```sh
alias ASLant="cd /mnt/h/WSL/Kali/ASLant"
```

生效
```sh
source ~/.bashrc
```

![[../ASLant_Images/2024-05-24-09-58-15.png]]

### 方法二

> [!BUG] 首先进入需要作为工作目录的文件夹!!!

```sh
echo "alias ASLant='cd $(pwd)'" >> ~/.bashrc
```

```sh
source ~/.bashrc
```
# Vim 添加行号


```sh
vim /etc/vim/vimrc
```

```sh
set number
```




`ldconfig` 命令用于更新动态链接库缓存并创建必要的符号链接。在执行 `ldconfig` 时，出现了 `/usr/lib/wsl/lib/libcuda.so.1 is not a symbolic link` 这样的错误，这意味着文件 `/usr/lib/wsl/lib/libcuda.so.1` 不是一个符号链接，而 `ldconfig` 期望它是一个符号链接。

要解决这个问题，可以按照以下步骤操作：

1. **检查当前文件类型**：
   检查 `/usr/lib/wsl/lib/libcuda.so.1` 的文件类型：
   ```sh
   ls -l /usr/lib/wsl/lib/libcuda.so.1
   ```
   这将显示该文件是普通文件还是符号链接。

2. **备份当前文件**：
   在修改之前，备份当前文件以防万一：
   ```sh
   sudo cp /usr/lib/wsl/lib/libcuda.so.1 /usr/lib/wsl/lib/libcuda.so.1.bak
   ```

3. **删除当前文件**：
   如果该文件不是符号链接，您可以删除它：
   ```sh
   sudo rm /usr/lib/wsl/lib/libcuda.so.1
   ```

4. **创建符号链接**：
   查找正确的目标库文件并创建符号链接。首先找到实际的库文件（例如，`libcuda.so.1.x.x`），然后创建符号链接。假设实际库文件为 `libcuda.so.1.1`，您可以这样操作：
   ```sh
   sudo ln -s /usr/lib/wsl/lib/libcuda.so.1.1 /usr/lib/wsl/lib/libcuda.so.1
   ```

5. **更新库缓存**：
   运行 `ldconfig` 更新动态链接库缓存：
   ```sh
   sudo ldconfig
   ```
