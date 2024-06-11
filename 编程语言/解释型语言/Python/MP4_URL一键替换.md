# 最终代码

> [!BUG] 粘贴格式
> ``` url
> https://s2.ananas.chaoxing.com/sv-w7/video/b4/68/7b/853cd350cf73014f334d4a73295948fe/sd.mp4?at_=1717315779151&ak_=ffef52ffdf3fc87b002f7c4c9f53bf1a&ad_=2d5ae5ebb06bbd1c0c9a2866782670a0
> ```

```python
import tkinter as tk
from tkinter import messagebox
import pyperclip
import re

def replace_and_copy():
    original_url = input_entry.get()
    if original_url.startswith("https://s2.ananas"):
        # 去除URL中的参数
        cleaned_url = re.sub(r'\?.*$', '', original_url)
        # 替换域名
        new_url = cleaned_url.replace("https://s2.ananas", "https://s138.ananas")
        # 生成HTML模板
        html_template = f'<div style="text-align: center;"><video src="{new_url}" width="100%" height="100%" controls="controls" class="rounded-video"></video></div>'
        # 更新输出文本框
        output_text.delete("1.0", tk.END)
        output_text.insert(tk.END, html_template)
        # 复制到剪贴板
        pyperclip.copy(html_template)
    else:
        messagebox.showwarning("Warning", "The URL must start with 'https://s2.ananas'.")

def clear_all():
    input_entry.delete(0, tk.END)
    output_text.delete("1.0", tk.END)

# 创建主窗口
root = tk.Tk()
root.title("URL Domain Replacer")

# 创建输入框标签
input_label = tk.Label(root, text="Enter the URL:")
input_label.pack()

# 创建输入框
input_entry = tk.Entry(root, width=50)
input_entry.pack()

# 创建输出框标签
output_label = tk.Label(root, text="Output HTML:")
output_label.pack()

# 创建输出文本框
output_text = tk.Text(root, height=10, width=60)
output_text.pack()

# 创建按钮框架
button_frame = tk.Frame(root)
button_frame.pack(pady=10)

# 创建替换并复制按钮
replace_and_copy_button = tk.Button(button_frame, text="Replace and Copy", command=replace_and_copy)
replace_and_copy_button.grid(row=0, column=0, padx=5)

# 创建清空按钮
clear_button = tk.Button(button_frame, text="Clear All", command=clear_all)
clear_button.grid(row=0, column=1, padx=5)

# 运行主循环
root.mainloop()
```

# 导出结果
```html
<div style="text-align: center;"><video src="https://s138.ananas.chaoxing.com/sv-w7/video/b4/68/7b/853cd350cf73014f334d4a73295948fe/sd.mp4" width="100%" height="100%" controls="controls" class="rounded-video"></video></div>
```