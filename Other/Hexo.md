# 基于Hexo 的 Blog 搭建
### 下载加速
```sh
npm config set registry http://registry.npmjs.org
```

> 淘宝镜像
```sh
npm config set registry=https://registry.npm.taobao.org/
```

### 安装 Hexo
```sh
npm install -g hexo-cli
```

### 创建 Blog
```sh
hexo init 文件夹
```

### 安装依赖
> 需要当前目录下有package.json
```sh
npm install
```

### 生成静态 html文件
> 在博客目录下执行以下命令
```sh
Hexo generate
```
或使用简写：
```sh
Hexo g
```

### 启动本地服务器
```sh
Hexo server
```
或使用简写：
```sh
Hexo s
```

### 安装主题
> 进入博客目录安装
```sh
npm install --save hexo-theme-fluid
```

[一款 Material Design 风格的 Hexo 主题 ](https://github.com/fluid-dev/hexo-theme-fluid)

> 下载配置文件
```sh
curl -o _config.fluid.yml https://raw.githubusercontent.com/fluid-dev/hexo-theme-fluid/master/_config.yml
```

> 切换 `_config.yml` 主题
```yml
theme: fluid  # 指定主题
language: zh-CN  # 指定语言，会影响主题显示的语言，按需修改
```

> 重新生成并运行
```powershell
hexo g; hexo s
```

### 最终效果

![[../ASLant_Files/94b37e996ecbb76d6caa99a7959402d1_MD5.jpg]]