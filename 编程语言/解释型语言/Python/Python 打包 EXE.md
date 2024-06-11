#### 安装 Pyinstaller

```Shell
pip install pyinstaller
```
### 打包 Py 代码
```python
pyinstaller -F -w main.py -i main.ico --workpath build路径 --distpath exe打包路径 -n exe名字
```
### 主要参数
- -F, --onefile 打包一个单个文件，如果你的代码都写在了一个 py 文件的话，可以使用这个命令，如果是多个 py 文件，就别用；
- -D, --onedir 打包多个文件，在 dist 中生成很多依赖文件，适合以框架的形式编写工具代码，代码易于维护；
- -a, --ascii 不包含 unicode 编码的支持 (包括默认值: 如果可用)
- -c, --console 使用控制台子系统执行（默认），只对 windows 有效
- -w, --windowed, --noconsole 使用 windows 子系统执行，当程序启动的时候不会打开命令行（只对 windows 有效）
- -i , --icon=<File.ico>将 file. Ico 添加为打包的 exe 文件的图表，只对 windows 系统有效
- --icon=<File.exe,n>将 file. Exe 的第 n 个图标添加为可执行文件的资源，只对 windows 系统有效
- -n Name，--name=Name 可选的项目，生成的. Spec 文件的名字和 exe 名字
- -p 设置导入路径（和使用 PYTHONPATH 效果相似），可以使用路径分隔符（windows 使用分好，linux 使用冒号），制定多个目录的时候可以指定多个-p 参数来设置，让 pyinstaller 自己去找程序的资源
- -key KEY 用于加密 Python 字节码的密钥
- -add-data 可以将一些非二进制文件添加到 exe 文件中进行打包，参数为格式为 static; static
- --distpath 指定打包后的程序存放目录，exe 文件默认存放在当前目录下的 dist 目录中
- --workpath 为输出的所有临时文件指定存放目录，默认为当前目录下的 build 目录

### 示例 1

```python
# 直接打包成exe 图标默认 且不带cmd
Pyinstaller -F -w main_test.py
```

### 示例 2

```python
# 打包成exe 不带cmd 名字为Test 保存位置为I盘根目录
 pyinstaller -F -w --distpath=I:\ main.py -n Test
```