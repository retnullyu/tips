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

