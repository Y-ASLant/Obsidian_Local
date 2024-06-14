# ldconfig: /usr/lib/wsl/lib/libcuda. So. 1 is not a symbolic link
在运行 `ldconfig` 时，遇到错误消息 `ldconfig: /usr/lib/wsl/lib/libcuda.so.1 is not a symbolic link`，这是因为 `ldconfig` 期望 `libcuda.so.1` 是一个符号链接，但它是一个实际文件。要解决这个问题，你可以手动创建一个符号链接指向实际的库文件。

### 请按照以下步骤进行操作：

1. 删除现有的 `libcuda.so.1` 文件：

```sh
sudo rm /usr/lib/wsl/lib/libcuda.so.1
```

2. 创建一个指向实际库文件的符号链接。首先，找到实际的库文件（通常会有一个版本号后缀，例如 `libcuda.so.1.2.3`）：

```sh
ls /usr/lib/wsl/lib/libcuda.so.*
```

3. 假设找到的实际库文件是 `libcuda.so.1.2.3`，创建符号链接：

```sh
sudo ln -s /usr/lib/wsl/lib/libcuda.so.1.2.3 /usr/lib/wsl/lib/libcuda.so.1
```

4. 重新运行 `ldconfig`：

```sh
sudo ldconfig
```

通过这些步骤，你应该能够解决 `ldconfig` 报错 `libcuda.so.1 is not a symbolic link` 的问题。如果库文件名或路径不同，请根据实际情况进行调整。