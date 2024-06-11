> [!ERROR] 通过 SCP 远程上传文件到服务器
# 单线程
```python
import paramiko
import tkinter as tk
from tkinter import filedialog
from tkinter import ttk
import os


def select_folder():
    folder_selected = filedialog.askdirectory()
    folder_path.set(folder_selected)


def update_progress(current, total):
    progress['value'] = (current / total) * 100
    root.update_idletasks()


def upload_folder():
    local_folder = folder_path.get()
    remote_subdir = remote_folder.get()
    if not local_folder or not remote_subdir:
        status.set("Please select a folder and enter the remote path.")
        return

    remote_path = f"/www/wwwroot/aslant.top/{remote_subdir}"

    ssh = paramiko.SSHClient()
    ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
    try:
        ssh.connect('服务器IP', username='用户名', password='密码')
        sftp = ssh.open_sftp()

        all_files = []
        for root_dir, dirs, files in os.walk(local_folder):
            for file in files:
                all_files.append(os.path.join(root_dir, file))

        total_files = len(all_files)
        uploaded_files = 0

        for root_dir, dirs, files in os.walk(local_folder):
            for dir in dirs:
                remote_dir = os.path.join(remote_path,
                                          os.path.relpath(os.path.join(root_dir, dir), local_folder)).replace('\\', '/')
                try:
                    sftp.mkdir(remote_dir)
                except:
                    pass

            for file in files:
                local_file = os.path.join(root_dir, file)
                remote_file = os.path.join(remote_path, os.path.relpath(local_file, local_folder)).replace('\\', '/')
                sftp.put(local_file, remote_file)

                uploaded_files += 1
                update_progress(uploaded_files, total_files)

        sftp.close()
        ssh.close()
        status.set("Scp Upload Successful.")
    except Exception as e:
        status.set(f"Error: {str(e)}")


root = tk.Tk()
root.title("SCP File Upload @ASLant")

folder_path = tk.StringVar()
remote_folder = tk.StringVar()
status = tk.StringVar()

tk.Label(root, text="Select Folder:").grid(row=0, column=0, padx=10, pady=10)
tk.Entry(root, textvariable=folder_path, width=50).grid(row=0, column=1, padx=10, pady=10)
tk.Button(root, text="Browse", command=select_folder).grid(row=0, column=2, padx=10, pady=10)

tk.Label(root, text="Remote Path (Note):").grid(row=1, column=0, padx=10, pady=10)
tk.Entry(root, textvariable=remote_folder, width=50).grid(row=1, column=1, padx=10, pady=10)

tk.Button(root, text="Upload", command=upload_folder).grid(row=2, column=0, columnspan=3, padx=10, pady=10)

progress = ttk.Progressbar(root, orient='horizontal', mode='determinate', length=400)
progress.grid(row=3, column=0, columnspan=3, padx=10, pady=10)

tk.Label(root, textvariable=status, fg="red").grid(row=4, column=0, columnspan=3, padx=10, pady=10)

root.mainloop()
```

# 多线程
```python
import paramiko
import tkinter as tk
from tkinter import filedialog, messagebox
from tkinter import ttk
import os
import threading

def select_folder():
    folder_selected = filedialog.askdirectory()
    folder_path.set(folder_selected)

def update_progress(current, total):
    progress['value'] = (current / total) * 100
    root.update_idletasks()

def upload_folder():
    local_folder = folder_path.get()
    remote_subdir = remote_folder.get()
    if not local_folder or not remote_subdir:
        status.set("Please select a folder and enter the remote path.")
        return

    remote_path = f"/www/wwwroot/aslant.top/{remote_subdir}"

    def run_upload():
        ssh = paramiko.SSHClient()
        ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
        try:
            ssh.connect('服务器IP', username='用户名', password='密码')
            sftp = ssh.open_sftp()

            all_files = []
            for root_dir, dirs, files in os.walk(local_folder):
                for file in files:
                    all_files.append(os.path.join(root_dir, file))

            total_files = len(all_files)
            uploaded_files = 0

            for root_dir, dirs, files in os.walk(local_folder):
                for dir in dirs:
                    remote_dir = os.path.join(remote_path, os.path.relpath(os.path.join(root_dir, dir), local_folder)).replace('\\', '/')
                    try:
                        sftp.mkdir(remote_dir)
                    except:
                        pass

                for file in files:
                    local_file = os.path.join(root_dir, file)
                    remote_file = os.path.join(remote_path, os.path.relpath(local_file, local_folder)).replace('\\', '/')
                    sftp.put(local_file, remote_file)

                    uploaded_files += 1
                    update_progress(uploaded_files, total_files)

            sftp.close()
            ssh.close()
            status.set("Scp Upload Successful.")
        except Exception as e:
            status.set(f"Error: {str(e)}")

    upload_thread = threading.Thread(target=run_upload)
    upload_thread.start()

root = tk.Tk()
root.title("SCP File Upload @ASLant")

folder_path = tk.StringVar()
remote_folder = tk.StringVar()
status = tk.StringVar()

tk.Label(root, text="Select Folder:").grid(row=0, column=0, padx=10, pady=10)
tk.Entry(root, textvariable=folder_path, width=50).grid(row=0, column=1, padx=10, pady=10)
tk.Button(root, text="Browse", command=select_folder).grid(row=0, column=2, padx=10, pady=10)

tk.Label(root, text="Remote Path (Note):").grid(row=1, column=0, padx=10, pady=10)
tk.Entry(root, textvariable=remote_folder, width=50).grid(row=1, column=1, padx=10, pady=10)

tk.Button(root, text="Upload", command=upload_folder).grid(row=2, column=0, columnspan=3, padx=10, pady=10)

progress = ttk.Progressbar(root, orient='horizontal', mode='determinate', length=400)
progress.grid(row=3, column=0, columnspan=3, padx=10, pady=10)

tk.Label(root, textvariable=status, fg="red").grid(row=4, column=0, columnspan=3, padx=10, pady=10)

root.mainloop()

```