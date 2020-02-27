# 虚拟机&shell脚本



***ubuntu同窗口与打开多个终端***

`Ctrl + Shift + T,一个终端开启多个小终端`

`Ctrl + Alt + T 开启多个终端`

`Ctrl + Shift + =**放大**终端字体`

`Ctrl + - **缩小**终端字体  -是减号`

开启ssh

`sudo /etc/init.d/ssh start`

***IDS 入侵检测系统(IDS: Intrusion Detection Systems))***

提供报告和事后监督为主

***IPS类(入侵防御系统(IPS: Intrusion Prevention System))***

可以分析到数据包内容

# 正则表达式

找出中文

`[^\x00-\xff]`^

所有数字

`\d`

单词

`\w`

换行

`\n`

TAb

`\t`

所有不可见字符

`\s`

***大写反之***

出现次数

`\d{1,2}`

不区分位数

`\d+`

开头为ab的

`\b[a-b]\w+`

# makefile

https://blog.csdn.net/l297969586/article/details/74393320

***编译***

windows下编译首先向编译成.obj；检查语法的正确性 函数和变量的声明的正确



***链接***

unix是.o文件，object fileobj文件合成可执行文件 寻找函数的实现



***

target：目标文件 obj，执行文件 标签

prerequisites：target所需要的文件和目标

command：make所执行的命令

***sum up target这一个或多个的目标文件依赖于prerequisites中的文件，其生成规则定义在command中;prerequisites中如果有一个以上的文件比target文件要新的话，command所定义的命令就会被执行***

### gdb调试

b funname

r

单步：si：进入函数

ni：跳过函数

跳出库函数：fini

### Typora教程

[教程][https://www.jianshu.com/p/a6a6a22e9393]

### vscode快捷键

* 删除行：ctrl+shift+k

* 替换：Ctrl +H

* 插入

  ![image-20200212135827660](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200212135827660.png)

* 复制

  ![image-20200212135926744](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200212135926744.png)

* 回退光标 Ctrl + U

