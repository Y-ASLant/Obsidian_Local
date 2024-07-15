# [ubuntu下 vi输入方向键会变成ABCD的解决方法](https://www.cnblogs.com/xiaomagua/p/7277872.html "发布于 2017-08-03 09:13")

方法1、编辑/etc/vim/vimrc.tiny

　　sudo vi /etc/vim/vimrc.tiny，这个文件里面的倒数第二句话是“set compatible”，

　　将“compatible”改成“nocompatible”非兼容模式就可以解决方向键变ABCD的问题了。

　　**Backspace键**的问题，在刚才那句话后面再加一句：set backspace=2 

方法2.ubuntu预装的是vim tiny版本，安装vim full版本即可解决。

　　先卸载vim-tiny：

　　　　$ sudo apt-get remove vim-common

　　再安装vim full：

　　　　$ sudo apt-get install vim