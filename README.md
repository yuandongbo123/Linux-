# Linux-编程
linux 网络编程和系统编程

# 基础命令
- 显示日期与时间 date
- 显示日历命令 cal
- 计算器 bc  推出 quit
- su 切换为root
- cat 显示文件
- ls  显示文件目录
- cp 复制
- rm 删除
- mv 移动
- head 文件路径  显示文件前几行
- tali 文件路径 显示文件后几行
- tree 按树状显示文件结构 (sudo apt -get install tree)
- wc
- du 显示磁盘大小
- df 查看磁盘情况
- ln -S 目标路径 源文件   软连接
- sudo address 添加用户
- sudo chown 新用户名 待修改文件
- sudo addgroup   组名 创建新租
- sudo chgrp 修改文件所属用户组


## linux系统文件类型
- 普通文件 -
- 目录文件 d
- 字符设备文件 b
- 软链接 l
- 管道文件 p
- 套接字 s
 



## 重要热键
- tab  ctrl - c ctrl -d

## 修改文件所有权限 **（鸟哥156页）**
- chgrp ：修改文件所属用户群
- chown：修改文件拥有着
- chmod：修改文件的权限
- umask -S 显示文件的默认权限


## linux目录配置
- 可分享 /usr 存放软件 -- /opt 第三方辅助软件 -- /var/mail 邮箱
- 不可分享 /etc 配置文件 -- /boot 启动内核 -- /var/run 程序相关 -- /var/run 程序相关

## 关于执行文件路径的变量 $PATH
- echo $PATH 显示路径 echo（显示 ）

##文件查找
- which 查找path环境变量
- whereis 文件名或目录名
- find  例如   
 find ./ -name '*.jpg'  ;
find ./ -size + 20M -size 40M | xargs ls-l;
- grep 搜文件
例如 grep -r 'copy' ./ n;

##安装与卸载软件
- apt - get
- sudo vi /etc/apt/sources.list 更新原服务器
- sudo apt-get update 更新源
- sudo apt-get install tree  安装
- sudo apt-get remove   删除
- sudo dpkg -i 安装包名


##压缩与解压**（鸟哥265页）**
- tar
压缩：tar -jcv - f 文件名.tar.bz2
查询：tar -jtv -f 文件.tar.bz2;
解压： tar -jxv -f 文件.tar.bz2 -C 想解压缩的目录
- rar a-r 压缩
- x 解压


## 进程管理
- ps 查看进程
- ps aux 查看所有进程
 - env 查看当前环境变量
- vim  ~/.bashrc 配置当前用户环境变量
- vim /etc/profile 配置当前用户环境变量
- export PATH=$PATH:新路径 
- sudo su 变更root用户
- passw 设置用户密码
- ifconfig 查看网卡信息
- sudo ifconfig eth0 down 关闭网卡
- sudo ifconfig eth0 up 开启网卡
- sudo ifconfig eth0 IP 给eth0 配置临时ip
- ping[选项] 主机名/ip地址

#vim编辑器
- 按键说明（鸟哥293页）
### vim 打造vimIDE
- 1. /etc/vim/virc （cd 进入）
- 2. ~/.vimrc    他的优先级最高

### 多文件补全功能
- :n 编辑下一个文件
- :N 编辑上一个文件
- files 列出目前这个vim开启的所有文件
- sp[filenames] 多窗口
- vsp 竖直多窗口



#BASH和shell
- history 查看历史命令行
- alias 命令别名设置功能 例如 alias lm = 'ls -al'
- type name 查看命令是否是shell内剑的
## shell脚本编写
- echo 使用变量
- 变量使用时必须加上$符号 如 echo $PATH
- 使用规则语法（鸟哥319页）
- # 删除 例子 ${path#/*local/bin:} 删除 local/bin:

### 管道命令
- | 例如 ls - al /etc | less     还有 less more head tail
### 选取命令
- cut 、grep
- cut 切片 例如 echo{$PATH} | cut -d ':'  -f 5
- grep 分析一行信息有需要的就拿出来
例如：grep -v'root'

#什么是正则表达式
