
```bash
# 使用 wget 静默下载文件，显示下载进度，并忽略 SSL 证书检查
wget -q --show-progress --no-check-certificate https://aslant.top/Cloud/OneDrive/Linux/ccat_install.sh

```

命令的解释：

- `-q`：静默模式。只显示错误和下载进度以外的输出。
- `--show-progress`：显示下载进度条，以提供下载状态的指示。
- `--no-check-certificate`：禁用 SSL/TLS 证书检查。在连接到使用自签名证书或由未知 CA 颁发的服务器时使用此选项。
- `"https://aslant.top/Cloud/OneDrive/Linux/ccat_install.sh"`：包含要下载文件的 URL。