# 下载特定类型的文件（如 `.exe` 和 `.zip` 文件），使用 `--accept` 选项来指定要下载的文件类型

```bash
wget -r -np -nH --cut-dirs=3 --accept=pdsprj,exe,zip https://aslant.top/Cloud/E5/Work_space/Proteus_%E4%BB%BF%E7%9C%9F/
```

这个命令会递归下载目录下的所有 .pdsprj .exe 和 .zip ` 文件，并且忽略其他文件类型。

完整命令的解释如下：
- `-r`：递归下载。
- `-np`：不向上级目录递归。
- `-nH`：不生成主机目录。
- `--cut-dirs=3`：忽略 URL 的开头的 3 个目录。
- `--accept=exe,zip`：只接受 `.exe` 和 `.zip` 文件。

运行此命令会下载指定目录下的所有 `.exe` 和 `.zip` 文件到当前工作目录。