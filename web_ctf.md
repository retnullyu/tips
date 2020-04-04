# web_ctf

## tips

PHP备份文件：*.php.bak *.php~



**xff:X-Forwarded-For（XFF）是用来识别通过HTTP代理或负载均衡方式连接到Web服务器的客户端**最原始的IP地址**的HTTP请求头字段。**



HTTP来源地址（referer，或HTTPreferer）
是HTTP表头的一个字段，用来表示从哪儿链接到当前的网页，采用的格式是URL。换句话说，借着HTTP来源地址，当前的网页可以检查访客从哪里而来，这也常被用来对付伪造的跨网站请求。



php中的include对文件后缀无要求，只需要文件内容是PHP的语法格式

### 文件包含漏洞

### LFI(Local File Inclusion)

本地文件包含漏洞，顾名思义，指的是能打开并包含本地文件的漏洞。大部分情况下遇到的文件包含漏洞都是LFI。简单的测试用例如前所示。

### RFI(Remote File Inclusion)

远程文件包含漏洞。是指能够包含远程服务器上的文件并执行。由于远程服务器的文件是我们可控的，因此漏洞一旦存在危害性会很大。
但RFI的利用条件较为苛刻，需要php.ini中进行配置

- allow_url_fopen = On
- allow_url_include = On

两个配置选项均需要为On，才能远程包含文件成功

### php://input

利用条件：

- allow_url_include = On。
- 对allow_url_fopen不做要求。

```php
data:image/png;base64,base64编码的内容
data:,文本数据
data:text/plain,文本数据
data:text/html,HTML代码
data:text/html;base64,base64编码的HTML代码
    
```

### php反序列

***（CVE-2016-7124），即当序列化字符串中表示对象属性个数的值大于真实的属性个数时会跳过__wakeup的执行。***

#### CVE-2016-7124

说到PHP反序列化漏洞 , 那就不得不提 **CVE-2016-7124** , 该漏洞使得攻击者可以成功的绕过 `__wakeup()` 函数 .

影响版本:

> PHP5 < 5.6.25
>
> PHP7 < 7.0.10

简单的说 , **当序列化字符串中的设置的属性个数大于实际的属性个数时 , 对象属性检测就会出现异常 , 那么`process_nested_data()`就会返回0 , 反序列化产生异常 , 从而不执行 `__wakeup()` 函数 . 在此之前对象和它的属性已经被创建 , 但紧接着对象将被破坏 , 从而执行 `__destruct()` 函数 , 从而产生漏洞**

 private变量 在序列化后两侧会有 \00 的特殊字符  protected类型的变量，序列化之后字符串首部会加上%00*%00。

**private**
`数据类型:属性名长度:"\00类名\00属性名";数据类型:属性值长度:"属性值"`

**protected**
`数据类型:属性名长度:"\00*\00属性名";数据类型:属性值长度:属性值`

**public**
`数据类型:属性名长度:属性名;数据类型:属性值长度:属性值`

**属性名上的区别在构造POC时十分关键!**

### SSTI模板注入：

https://www.jianshu.com/p/aef2ae0498df

### php伪协议

https://segmentfault.com/a/1190000018991087

PHP支持的伪协议如下：

```
file:``// — 访问本地文件系统``http:``// — 访问 HTTP(s) 网址``ftp:``// — 访问 FTP(s) URLs``php:``// — 访问各个输入/输出流（I/O streams）``zlib:``// — 压缩流``data:``// — 数据（RFC 2397）``glob``:``// — 查找匹配的文件路径模式``phar:``// — PHP 归档``ssh2:``// — Secure Shell 2``rar:``// — RAR``ogg:``// — 音频流``expect:``// — 处理交互式的流
```

**PHP.ini**

在php.ini里有两个重要的参数allow_url_fopen和allow_url_include

allow_url_fopen:默认值是ON，允许url里的封装协议访问文件

allow_url_include:默认值是OFF,不允许包含url里的封装协议包含文件

**php://filter**

经常使用的伪协议，一般用于任意文件读取，有时也可以用于getshell.在双OFF的情况下也可以使用.

php://filter是一种元封装器，用于数据流打开时筛选过滤应用。这对于一体式（all-in-one）的文件函数非常有用。类似readfile()、file()、file_get_contents(),在数据流读取之前没有机会使用其他过滤器。

php://filter参数

| 名称                      | 描述                                                         |
| ------------------------- | ------------------------------------------------------------ |
| resource=<要过滤的数据流> | 这个参数是必须的。它指定了你要筛选过滤的数据流。             |
| *read=<读链的筛选列表>*   | 该参数可选。可以设定一个或多个过滤器名称，以管道符(\|)分隔   |
| *write=<写链的筛选列表>*  | 该参数可选。可以设定一个或多个过滤器名称，以管道符(\|)分隔   |
| *<；两个链的筛选列表>*    | 任何没有以 *read=* 或 *write=* 作前缀 的筛选器列表会视情况应用于读或写链。 |

```
php://filter/[read/write]=string.[rot13/strip_tags/…..]/resource=xxx
```

filter和string过滤器连用可以对字符串进行过滤。filter的read和write参数有不同的应用场景。read用于include()和file_get_contents(),write用于file_put_contents()中。

```
php://filter/convert.base64-[encode/decode]/resource=xxx
```

这是使用的过滤器是convert.base64-encode.它的作用就是读取upload.php的内容进行base64编码后输出。可以用于读取程序源代码经过base64编码后的数据

**php://input**

php://input可以访问请求的原始数据的只读流，将post请求的数据当作php代码执行。当传入的参数作为文件名打开时，可以将参数设为php://input,同时post想设置的文件内容，php执行时会将post内容当作文件内容。

需要开启allow_url_include

注：当enctype=”multipart/form-data”时，php://input是无效的。

**file://**

file://伪协议在双OFF的时候也可以用，用于本地文件包含

注：file://协议必须是绝对路径

**phar://**

PHP 归档，常常跟文件包含，文件上传结合着考察。说通俗点就是php解压缩包的一个函数，解压的压缩包与后缀无关。

```
phar://test.[zip/jpg/png…]/file.txt
```

其实可以将任意后缀名的文件(必须要有后缀名)，只要是zip格式压缩的，都可以进行解压，因此上面可以改为phar://test.test/file.txt也可以运行。

**zip://,bzip2://, zlib://**

在双OFF的时候也可以用，

```
zip://test.zip%23file.txt
```

和phar://一样用于读取压缩文件，不过对于"zip://test.zip#file.txt"中的"#"要编码为"%23".因为url的#后的内容不会被传送

**data://text/plain;base64,base编码字符串**

很常用的数据流构造器，将读取后面base编码字符串后解码的数据作为数据流的输入

### mysql handler语句

https://blog.csdn.net/JesseYoung/article/details/40785137

```mysql
handler handler_table open;
handler handler_table open as p;
handler handler_table read first;
handler handler_table read next;
handler handler_table read first limit 3;
handler handler_table read next limit 3,3;
handler handler_table read first where c1 > 2 limit 2;
handler handler_table read next where c1 >2 limit 1,2;
 
create index handler_index on handler_table(c1);
handler handler_table open;
handler handler_table read handler_index first;
handler handler_table read handler_index next limit 3;
handler handler_table read handler_index PREV limit 3,3;
handler handler_table read handler_index LAST where c1 > 2 limit 2;
handler handler_table read handler_index LAST where c1 > 2 limit 1,2;
handler handler_table read handler_index = (3);
handler handler_table read handler_index <= (3) limit 2;
handler handler_table read handler_index >= (3) limit 1,2;
handler handler_table read handler_index < (4)  where c1 > 0 limit 2;
handler handler_table read handler_index > (1)  where c1 < 6 limit 2,2;
handler handler_table close;
drop index handler_index on handler_table;
```

### 堆叠注入

***mysql预编译***

```mysql
mysql> prepare ins from 'insert into t select @a,@b'; --编译


mysql> set @a=999,@b='hello';
mysql> execute ins using @a,@b;--执行
mysql> deallocate prepare ins;
Query OK, 0 rows affected (0.00 sec) --释放


```

