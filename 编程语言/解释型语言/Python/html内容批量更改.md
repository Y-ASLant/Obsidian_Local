> [!ERROR] 批量更改 html 内容

```python
import os
import tkinter as tk
from tkinter import filedialog
from bs4 import BeautifulSoup
from tqdm import tqdm

def process_html_files_in_directory(directory):
    # 获取指定目录及其子目录下的所有HTML文件
    html_files = []
    for root, dirs, files in os.walk(directory):
        for file in files:
            if file.endswith('.html'):
                html_files.append(os.path.join(root, file))

    # 使用tqdm显示处理进度
    for html_file_path in tqdm(html_files, desc='处理进度', unit='文件'):
        process_html_file(html_file_path)

def process_html_file(html_file_path):
    # 读取 HTML 文件
    with open(html_file_path, 'r', encoding='utf-8') as file:
        html_content = file.read()

    # 解析 HTML 内容
    soup = BeautifulSoup(html_content, 'html.parser')

    # 修改 "Table Of Contents" 为 "大纲"
    for toc in soup.find_all(string='Table Of Contents'):
        toc.replace_with('大纲')

    # 修改 "Interactive Graph" 为 "关系图谱"
    for ig in soup.find_all(string='Interactive Graph'):
        ig.replace_with('关系图谱')

    # 修改 "<span class="sidebar-section-header">Obsidian</span>" 为 "<span class="sidebar-section-header">ASLant</span>"
    for span in soup.find_all('span', {'class': 'sidebar-section-header'}):
        if span.string == 'Obsidian':
            span.string = 'ASLant'

    # 将修改后的 HTML 写回文件
    with open(html_file_path, 'w', encoding='utf-8') as file:
        file.write(str(soup))

def select_directory():
    root = tk.Tk()
    root.withdraw()  # 隐藏主窗口

    # 弹出文件选择对话框，选择目录
    directory = filedialog.askdirectory()
    if directory:
        process_html_files_in_directory(directory)
        print("所有HTML文件已成功修改。")
    else:
        print("未选择目录。")

# 创建一个简单的图形化界面
root = tk.Tk()
root.title("选择目录并处理HTML文件")

select_button = tk.Button(root, text="选择目录", command=select_directory)
select_button.pack(pady=20)

root.mainloop()

```

# 增加 html 格式化
```python
import os
import tkinter as tk
from tkinter import filedialog
from bs4 import BeautifulSoup
from tqdm import tqdm

def process_html_files_in_directory(directory):
    # 获取指定目录及其子目录下的所有HTML文件
    html_files = []
    for root, dirs, files in os.walk(directory):
        for file in files:
            if file.endswith('.html'):
                html_files.append(os.path.join(root, file))

    # 使用tqdm显示处理进度
    for html_file_path in tqdm(html_files, desc='处理进度', unit='文件'):
        process_html_file(html_file_path)

def process_html_file(html_file_path):
    # 读取 HTML 文件
    with open(html_file_path, 'r', encoding='utf-8') as file:
        html_content = file.read()

    # 解析 HTML 内容
    soup = BeautifulSoup(html_content, 'html.parser')

    # 修改 "Table Of Contents" 为 "大纲"
    for toc in soup.find_all(string='Table Of Contents'):
        toc.replace_with('大纲')

    # 修改 "Interactive Graph" 为 "关系图谱"
    for ig in soup.find_all(string='Interactive Graph'):
        ig.replace_with('关系图谱')

    # 修改 "<span class="sidebar-section-header">Obsidian</span>" 为 "<span class="sidebar-section-header">ASLant</span>"
    for span in soup.find_all('span', {'class': 'sidebar-section-header'}):
        if span.string == 'Obsidian':
            span.string = 'ASLant'

    # 格式化HTML代码
    formatted_html = soup.prettify()

    # 将修改后的 HTML 写回文件
    with open(html_file_path, 'w', encoding='utf-8') as file:
        file.write(str(formatted_html))

def select_directory():
    root = tk.Tk()
    root.withdraw()  # 隐藏主窗口

    # 弹出文件选择对话框，选择目录
    directory = filedialog.askdirectory()
    if directory:
        process_html_files_in_directory(directory)
        print("所有HTML文件已成功修改。")
    else:
        print("未选择目录。")

# 创建一个简单的图形化界面
root = tk.Tk()
root.title("选择目录并处理HTML文件")

select_button = tk.Button(root, text="选择目录", command=select_directory)
select_button.pack(pady=20)

root.mainloop()

```

# 版本三

```python
import os
import tkinter as tk
from tkinter import filedialog
from bs4 import BeautifulSoup
from tqdm import tqdm

def process_html_files_in_directory(directory):
    # 获取指定目录及其子目录下的所有HTML文件
    html_files = []
    for root, dirs, files in os.walk(directory):
        for file in files:
            if file.endswith('.html'):
                html_files.append(os.path.join(root, file))

    # 使用tqdm显示处理进度
    for html_file_path in tqdm(html_files, desc='处理进度', unit='文件'):
        process_html_file(html_file_path)

def process_html_file(html_file_path):
    # 读取 HTML 文件
    with open(html_file_path, 'r', encoding='utf-8') as file:
        html_content = file.read()

    # 解析 HTML 内容
    soup = BeautifulSoup(html_content, 'html.parser')

    # 修改 "Table Of Contents" 为 "大纲"
    for toc in soup.find_all(string='Table Of Contents'):
        toc.replace_with('大纲')

    # 修改 "Interactive Graph" 为 "关系图谱"
    for ig in soup.find_all(string='Interactive Graph'):
        ig.replace_with('关系图谱')

    # 修改 "<span class="sidebar-section-header">Obsidian</span>" 为 "<span class="sidebar-section-header">ASLant</span>"
    # for span in soup.find_all('span', {'class': 'sidebar-section-header'}):
    #     if span.string == 'Obsidian':
    #         span.string = 'ASLant'

    # 添加 JavaScript 脚本
    script_tag = soup.new_tag("script")
    script_tag.string = """
    document.addEventListener('DOMContentLoaded', () => {
        const links = document.querySelectorAll('a');

        links.forEach(link => {
            link.addEventListener('mouseover', (event) => {
                link.dataset.href = link.href; // 将原始链接存储到自定义属性
                link.href = 'javascript:void(0)'; // 将 href 属性修改为无效链接
            });

            link.addEventListener('mouseout', () => {
                link.href = link.dataset.href; // 恢复原始链接
            });

            link.addEventListener('click', (event) => {
                if (link.dataset.href) {
                    window.location.href = link.dataset.href; // 点击时跳转到原始链接
                }
            });
        });
    });
    """

    # 将脚本插入到 <head> 或 <body> 中
    if soup.head:
        soup.head.append(script_tag)
    else:
        if not soup.body:
            soup.append(soup.new_tag("body"))
        soup.body.append(script_tag)

    # 格式化HTML代码
    formatted_html = soup.prettify()

    # 将修改后的 HTML 写回文件
    with open(html_file_path, 'w', encoding='utf-8') as file:
        file.write(str(formatted_html))

def select_directory():
    root = tk.Tk()
    root.withdraw()  # 隐藏主窗口

    # 弹出文件选择对话框，选择目录
    directory = filedialog.askdirectory()
    if directory:
        process_html_files_in_directory(directory)
        print("所有HTML文件已成功修改。")
    else:
        print("未选择目录。")

# 创建一个简单的图形化界面
root = tk.Tk()
root.title("Html批量处理@ASLant")

# 设置窗口大小和位置
window_width = 300
window_height = 80
screen_width = root.winfo_screenwidth()
screen_height = root.winfo_screenheight()
position_top = int(screen_height/2 - window_height/2)
position_right = int(screen_width/2 - window_width/2)
root.geometry(f'{window_width}x{window_height}+{position_right}+{position_top}')

select_button = tk.Button(root, text="选择目录", command=select_directory)
select_button.pack(pady=20)

root.mainloop()
```

# 最终版本（已被舍弃）

> [!tldr] 原因：
> 1. 一键格式化代码会大大增加文件大小
> 2. GUI看不到处理进度，且没有成功提示
> 3. 增加的 js 代码会使双链跳转失效

```python
import os
import tkinter as tk
from tkinter import filedialog
from bs4 import BeautifulSoup
from tqdm import tqdm

def process_html_files_in_directory(directory, excluded_folders):
    # 获取指定目录及其子目录下的所有HTML文件
    html_files = []
    for root, dirs, files in os.walk(directory):
        for file in files:
            if file.endswith('.html'):
                html_files.append(os.path.join(root, file))

    # 使用tqdm显示处理进度
    for html_file_path in tqdm(html_files, desc='处理进度', unit='文件'):
        # 检查文件是否在排除的文件夹中
        if any(excluded_folder in html_file_path for excluded_folder in excluded_folders):
            process_html_file(html_file_path, skip_formatting=True)
        else:
            process_html_file(html_file_path, skip_formatting=False)

def process_html_file(html_file_path, skip_formatting):
    # 读取 HTML 文件
    with open(html_file_path, 'r', encoding='utf-8') as file:
        html_content = file.read()

    # 解析 HTML 内容
    soup = BeautifulSoup(html_content, 'html.parser')

    # 修改 "Table Of Contents" 为 "大纲"
    for toc in soup.find_all(string='Table Of Contents'):
        toc.replace_with('大纲')

    # 修改 "Interactive Graph" 为 "关系图谱"
    for ig in soup.find_all(string='Interactive Graph'):
        ig.replace_with('关系图谱')

    # 添加 JavaScript 脚本
    script_tag = soup.new_tag("script")
    script_tag.string = """
    document.addEventListener('DOMContentLoaded', () => {
        const links = document.querySelectorAll('a');

        links.forEach(link => {
            link.addEventListener('mouseover', (event) => {
                link.dataset.href = link.href; // 将原始链接存储到自定义属性
                link.href = 'javascript:void(0)'; // 将 href 属性修改为无效链接
            });

            link.addEventListener('mouseout', () => {
                link.href = link.dataset.href; // 恢复原始链接
            });

            link.addEventListener('click', (event) => {
                if (link.dataset.href) {
                    window.location.href = link.dataset.href; // 点击时跳转到原始链接
                }
            });
        });
    });
    """

    # 将脚本插入到 <head> 或 <body> 中
    if soup.head:
        soup.head.append(script_tag)
    else:
        if not soup.body:
            soup.append(soup.new_tag("body"))
        soup.body.append(script_tag)

    if not skip_formatting:
        # 格式化HTML代码
        formatted_html = soup.prettify()
        # 将修改后的 HTML 写回文件
        with open(html_file_path, 'w', encoding='utf-8') as file:
            file.write(str(formatted_html))
    else:
        # 将修改后的 HTML 写回文件（不格式化）
        with open(html_file_path, 'w', encoding='utf-8') as file:
            file.write(str(soup))

def select_directory():
    root = tk.Tk()
    root.withdraw()  # 隐藏主窗口

    # 弹出文件选择对话框，选择目录
    directory = filedialog.askdirectory()
    if directory:
        # 获取用户输入的排除文件夹
        excluded_folders = exclude_entry.get().split(',')
        excluded_folders = [folder.strip() for folder in excluded_folders]

        process_html_files_in_directory(directory, excluded_folders)
        print("所有HTML文件已成功修改。")
    else:
        print("未选择目录。")

# 创建一个简单的图形化界面
root = tk.Tk()
root.title("Html批量处理@ASLant")

# 设置窗口大小和位置
window_width = 400
window_height = 150
screen_width = root.winfo_screenwidth()
screen_height = root.winfo_screenheight()
position_top = int(screen_height/2 - window_height/2)
position_right = int(screen_width/2 - window_width/2)
root.geometry(f'{window_width}x{window_height}+{position_right}+{position_top}')

# 添加选择目录按钮
select_button = tk.Button(root, text="选择目录", command=select_directory)
select_button.pack(pady=20)

# 添加排除文件夹输入框和标签
exclude_label = tk.Label(root, text="排除文件夹 (用逗号分隔):")
exclude_label.pack()
exclude_entry = tk.Entry(root, width=50)
exclude_entry.pack()

root.mainloop()

```

# 最终版本
```python
import os
import tkinter as tk
from tkinter import filedialog, ttk
from bs4 import BeautifulSoup

def process_html_files_in_directory(directory, progress_var, progress_bar, root):
    # 获取指定目录及其子目录下的所有HTML文件
    html_files = []
    for root_dir, _, files in os.walk(directory):
        for file in files:
            if file.endswith('.html'):
                html_files.append(os.path.join(root_dir, file))

    total_files = len(html_files)
    progress_var.set(0)
    progress_bar['maximum'] = total_files

    # 处理进度
    for i, html_file_path in enumerate(html_files, start=1):
        process_html_file(html_file_path)
        progress_var.set(i)
        root.update_idletasks()  # 更新进度条

def process_html_file(html_file_path):
    # 读取 HTML 文件
    with open(html_file_path, 'r', encoding='utf-8') as file:
        html_content = file.read()

    # 解析 HTML 内容
    soup = BeautifulSoup(html_content, 'html.parser')

    # 修改 "Table Of Contents" 为 "大纲"
    for toc in soup.find_all(string='Table Of Contents'):
        toc.replace_with('大纲')

    # 修改 "Interactive Graph" 为 "关系图谱"
    for ig in soup.find_all(string='Interactive Graph'):
        ig.replace_with('关系图谱')

    # 将修改后的 HTML 写回文件
    with open(html_file_path, 'w', encoding='utf-8') as file:
        file.write(str(soup))

def select_directory():
    directory = filedialog.askdirectory()
    if directory:
        progress_label.config(text="Processing......")
        process_html_files_in_directory(directory, progress_var, progress_bar, root)
        progress_label.config(text="Successfully!")
    else:
        progress_label.config(text="No directory selected.")

# 创建一个简单的图形化界面
root = tk.Tk()
root.title("Html批量处理@ASLant")

# 设置窗口大小和位置
window_width = 400
window_height = 160
screen_width = root.winfo_screenwidth()
screen_height = root.winfo_screenheight()
position_top = int(screen_height / 2 - window_height / 2)
position_right = int(screen_width / 2 - window_width / 2)
root.geometry(f'{window_width}x{window_height}+{position_right}+{position_top}')

# 添加选择目录按钮
select_button = tk.Button(root, text="选择目录", command=select_directory)
select_button.pack(pady=20)

# 添加进度条
progress_var = tk.IntVar()
progress_bar = ttk.Progressbar(root, variable=progress_var, maximum=100)
progress_bar.pack(fill=tk.X, padx=20, pady=10)

# 添加进度标签
progress_label = tk.Label(root, text="")
progress_label.pack()

root.mainloop()
```

> [!ERROR] [Download](https://aslant.top/Cloud/OneDrive/Other/HTML-R.exe)