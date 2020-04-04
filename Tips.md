[toc]

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

#### bash脚本快捷键

**删除**

【Ctrl】+【D】删除光标所在位置上的字符相当于VIM里x或者dl

【Ctrl】+【H】删除光标所在位置前的字符相当于VIM里hx或者dh

【Ctrl】+【K】删除光标后面所有字符相当于VIM里d shift+$

【Ctrl】+【U】删除光标前面所有字符相当于VIM里d shift+^

【Ctrl】+【W】删除光标前一个单词相当于VIM里db

【Ctrl】+【Y】恢复ctrl+u上次执行时删除的字符

【Ctrl】+【?】撤消前一次输入

【Alt】+【R】撤消前一次动作

【Alt】+【D】删除光标所在位置的后单词

**移动**

【Ctrl】+【A】将光标移动到命令行开头相当于VIM里shift+^

【Ctrl】+【E】将光标移动到命令行结尾处相当于VIM里shift+$

【Ctrl】+【F】光标向后移动一个字符相当于VIM里l

【Ctrl】+【B】光标向前移动一个字符相当于VIM里h

【Ctrl】+【方向键左键】光标移动到前一个单词开头

【Ctrl】+【方向键右键】光标移动到后一个单词结尾

【Ctrl】+【X】在上次光标所在字符和当前光标所在字符之间跳转

【Alt】+【F】跳到光标所在位置单词尾部

**替换**

【Ctrl】+【T】将光标当前字符与前面一个字符替换

【Alt】+【T】交换两个光标当前所处位置单词和光标前一个单词

【Alt】+【U】把光标当前位置单词变为大写

【Alt】+【L】把光标当前位置单词变为小写

【Alt】+【C】把光标当前位置单词头一个字母变为大写

【^oldstr^newstr】替换前一次命令中字符串  

**历史命令编辑**

【Ctrl】+【P】返回上一次输入命令字符

【Ctrl】+【R】输入单词搜索历史命令

【Alt】+【P】输入字符查找与字符相接近的历史命令

【Alt】+【>】返回上一次执行命令

**其它**

【Ctrl】+【S】锁住终端

【Ctrl】+【Q】解锁终端

【Ctrl】+【L】清屏相当于命令clear

【Ctrl】+【C】另起一行

【Ctrl】+【I】类似TAB健补全功能

【Ctrl】+【O】重复执行命令

【Alt】+【数字键】操作的次数

