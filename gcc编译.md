## gcc 编译可以执行程序 4 步骤： 预处理、编译、汇编、链接
- hello.c 预处理 (g++ E)展开宏头文件、删除注释 -> hello.i
- hello.i 编译 (g++ S)检查语法规范 ->hello.s
- hello.s 汇编(g++ o)指令翻译成机器指令 ->hello.o
## gcc编译
### 4.步骤
-  I : 指定头文件的所在目录  注意 -I和目录之间没有空格
- c: 只做预处理、汇编生成 .o文件，不进行链接。得到 二进制 文件！！！
- g： 编译时添加调试语句。主要支持gdb调试
- Wall  显示警告信息
- D 向程序中“动态”注册宏定义。 define NAME VALUE
- l 指定动态库民
- L 指定动态库路径


## 制作静态库
- 1.将.c文件生成.o文件
    gcc -c add,c -o add.o
- 2. 使用ar工具制作静态库
  ar rcs lib 库名 .a  add.o sub.o div.o
- 3.编译金泰库可执行文件
  gcc test.c lib库名.a -o a.out


## 防止头文件重复包含
#ifndef
#define
#endif

## 动态库制作及使用
- 1.将.c 生成.o 文件（生成与位置无关的代码 -fPIC)
      gcc -c add.c -o add.o -fPIC
- 2.使用 gcc -shared 制作动态库
    gcc -shared -o lib库名.so add.o sub.o div.o

- 3.编译可执行程序是，指定所使用的动态库。 -l：指定库名 -L:指定库路径
   gcc test.c -o a.out -l mymath -L ./lib
- 4.运行可执行程序 ./a.out
  **链接器**：工作在链接阶段，工作是需要 -L 和 -l
   **动态连接器**
####  **1 .环境变量法** 工作在程序运行阶段，工作时需要提供动态库所在目录位置
- export LD_LIBRARY_PATH = 动态库路径
#### **2. 永久生效**：写入终端配置文件 .bashrc 建议是使用绝对路径
####                   1） vim ~/ .bashrc
####                   2) 写入 export LD_LIBRARY_PATH=动态链接库
####                   3） .. bashrc/  source ./bashrc /       重启终端  -->让修改的. bashrc生效
####                  4）./a.out 生效


##  gdb 调试工具（检查逻辑错误，检查不了语法错误）

- gdb a.out  进入gdb调试
- list    列出程序
- break 设置断点(跳出点） 例如： break  39  行
- run 程序会执行到38行
- next 下一个
- s 单步
- until 16 表示16行结束
- p i  print 简写p 查看一个变量的值‘
- ptype 查看变量类型
- contunue 跳到下一个断点
- quit 推出gdb调试
- finish 结束函数
- set args  设置main 参数
- run 字串1 字串2
- info b;查看断电信息表
#### **例如**：
- 1. gcc - gdbtext.c -o a.out -g    进入调试状态              
- 2. gdb a.out
-  3. l
- 4. b 32
- 5. run

直接run gdb 时直接报错停止的地方就是出错的地方










