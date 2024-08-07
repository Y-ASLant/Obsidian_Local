### 查看当前文件夹大小
```sh
du -sh
```


![[../ASLant_Files/2024-07-22-09-34-12.png]]

### 修改桌面壁纸
```sh
gsettings set org.gnome.desktop.background picture-uri 'file:///home/xtark/Pictures/image.jpg'
```


1. **`Ctrl` + `C`**：中断当前运行的命令。
2. **`Ctrl` + `Z`**：将当前命令放到后台，并暂停它。命令会显示一个`[1]+`的标记，表示它在后台挂起。
3. **`fg`**：将挂起的后台任务调回到前台继续运行。
4. **`bg`**：将挂起的后台任务在后台继续运行。
5. **`Ctrl` + `D`**：在Unix-like系统中，发送EOF（文件结束符），通常用于结束一个会话或关闭终端。
6. **`Tab`**：自动补全命令或文件名。
7. **`Up` 和 `Down` 箭头键**：浏览命令历史。
8. **`Home` 和 `End`**：快速跳转到命令行的开头或结尾。
9. **`Ctrl` + `U`**：删除从光标位置到行首的所有内容。
10. **`Ctrl` + `K`**：删除从光标位置到行尾的所有内容。
11. **`Ctrl` + `Y`**：粘贴最近使用`Ctrl` + `U`, `Ctrl` + `K`, 或 `Delete`删除的文本。
12. **`Ctrl` + `L`**：清屏，相当于输入`clear`命令。
13. **`Ctrl` + `R`**：搜索命令历史。

# 显示当前壁纸所在路径
```sh
gsettings get org.gnome.desktop.background picture-uri
```



