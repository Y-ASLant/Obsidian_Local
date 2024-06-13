# 在WSL 2 中使用串口
# Power shell 执行
#### 安装 USBIPD
```powershell
winget install --interactive --exact dorssel.usbipd-win
```
#### 列出所有已连接 USB 设备
```powershell
usbipd list
```

```powershell

```

```powershell
usbipd attach --busid x-x --wsl
```

![[../ASLant_Files/8f4640fd697d4df036f7c15143161ac4_MD5.jpg]]
### 断开
```sh
 usbipd detach --all
```

### 再次启动
```powershell
usbipd server
```

# 效果
 <div style="text-align: center;"><video src="https://s138.ananas.chaoxing.com/sv-w7/video/f8/51/1e/73f037fd038221c190fb3ffd1350a8e5/sd.mp4" width="100%" height="100%" controls="controls" class="rounded-video"></video></div>