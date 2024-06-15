# TheFuck 安装

> [!ERROR] 自动修正命令
![[ASLant_Files/1c927c17ce3650176f37c746d0e7786e_MD5.gif]]

```python
pip3 install thefuck
```

```sh
echo 'eval $(thefuck --alias)' >> ~/.bashrc
```

```sh
source ~/.bashrc
```

# Redhat 系列

```sh
dnf -y update && dnf -y upgrade
```

```sh
dnf -y install python3 python3-pip
```

```python
pip3 install thefuck
```

```sh
echo 'eval $(thefuck --alias)' >> ~/.bashrc
```

```sh
source ~/.bashrc
```

# Thefuck 运行速度慢问题

> [!success] 在~/.zshrc 或 ~/.bshrc 中加入
> ```sh
export PATH=/usr/local/bin:/usr/bin:/bin
> ```

```sh
echo 'export PATH=/usr/local/bin:/usr/bin:/bin' >> ~/.bashrc
```

```sh
source ~/.bashrc
```

```sh
sudo sh -c 'echo "[interop]\nappendWindowsPath = false" >> /etc/wsl.conf'
```

重启 WSL 生效
```powershell
wsl.exe --shutdown
```