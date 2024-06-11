![[ASLant_Images/9afed5702b0bbc7043b7a3cc29555384_MD5.jpg]]

## 下载

> [!INFO] [Git DownLoad](https://git-scm.com/download/win)  

## 初始化仓库

创建一个空的 git 仓库

```shell
git init
```

## 克隆仓库

> 克隆仓库到本地

```
git clone <server>
```
  
## 仓库连接服务器

> 将当前仓库连接到指定的服务器

```shell
git remote add origin <server>
```

## 查看文件状态

> 查看文件是否修改，增加或者删除的状态

```shell
git status
```

## 添加与提交

> 添加所有修改，新增，删除的文件操作到缓存区

```shell
git add * / . / -A
```

> 添加本次提交信息

```shell
git commit -m "本次提交信息"
```

## 推送改动

> 添加文件与设置提交信息后即可提交到 master 分支

```shell
git push origin master
```

## 分支

1. 创建分支

```shell
   git checkout -b 分支名字
```

2. 切换回主分支

```shell
   git checkout master
```

3. 删除本地分支

```shell
   git branch -d 分支名字
```

4. 删除远端分支

```shell
   git push origin --delete 分支名字
```

5. 推送分支

```shell
   git push origin <branch>
```

## 更新与合并

> 更新自己的本地仓库

```shell
git pull
```

> 在 master 主分支合并其他分支

```shell
git merge <branch>
```

## 本地记录密码

> 当前项目记录账号密码，防止每一次都输入

```shell
git config --global credential.helper store
```

## 恢复本地删除的文件

如果不小心使用 `git rm -r *` 删除了文件等

使用 `git reset HEAD [被删文件夹名称]` 将文件放到暂存区

然后使用 `git checkout [被删除的文件或文件夹]` 将文件从暂存区拉回本地即可
  
## 同步 fork 拉取远程仓库代码

> 添加 fork 的主仓库

```shell
git remote add 自定义名 https://github.com/*******.git
```

查看是否添加成功

```shell
remote -v
```

拉取仓库全部分支

```shell
git fetch 自定义名
```

合并到自己分支

```shell
git merge 自定义名/master
```

  
## 指定文件不上传

----

.git 目录新建 `.gitignore` 文件，里面写上不需要上传的文件夹或文件名字即可
自动生成网站：[gitignore.io - 为你的项目创建必要的 .gitignore 文件 (toptal.com)](https://www.toptal.com/developers/gitignore)

## 重置账号密码

> 适用于莫名其妙上传没权限问题

```shell
git config --system --unset credential.helper

// 如果需要更大的范围

git config --global --unset credential.helper
```

## 生成 ssh 密钥

使用 `ssh-keygen` 命令生成公钥和私钥

其中 -t 表示类型是 rsa 类型（非对称加密）-C 就是邮箱地址

 ```shell
 ssh-keygen -t rsa -C "mail@n0ts.cn"
 ```