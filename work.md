1、请写出地址FEC0:0000:0000:0001:02AA:0000:0000:007A更简洁的表达方式。

2、对于一个全局管理的单播IEEE 802地址0C-1C-09-A8-F9-CE，写出其基于EUI-64的IPV6接口标识符、对应的本地链路地址和对应的请求节点组播地址。

扩充到64 

UL取反

3、对于本地管理的单播EUI-64地址02-00-00-00-00-00-00-09，写出其对应的IPVv6接口标识符和对应的链路本地地址。

77

在IPV6中，是否存在与IPV4头部的IHL 字段等价的字段？

![image-20200228140729892](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200228140729892.png)

![image-20200228141224826](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200228141224826.png)

![image-20200228144304868](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200228144304868.png)

![image-20200228144839810](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200228144839810.png)

![image-20200228145200498](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200228145200498.png)

![image-20200228145440489](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200228145440489.png)

![image-20200303140446359](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200303140446359.png)

***DFA NFA***

![image-20200303142512959](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200303142512959.png)

![image-20200303143304493](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200303143304493.png)

***

右边的最左边是终结符

![image-20200306161907167](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200306161907167.png)

![image-20200306162715070](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200306162715070.png)

![image-20200306163341486](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200306163341486.png)

![image-20200310150025401](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200310150025401.png)

![image-20200310152449266](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200310152449266.png)

![image-20200310152628981](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200310152628981.png)

![image-20200314155655775](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200314155655775.png)

![image-20200314155939021](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200314155939021.png)

可归前缀是以句柄结尾的前缀

![image-20200317150521802](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200317150521802.png)

移入项目：点后面是终结符

归约项目：点后没有东西

待约项目：点后是非终结符

LR（0）：要么移入要么规约 无需考虑后继 归约时候不需要考虑了follow集合直接全部填r

构建自动机步骤：

1. 引入开始符 得到增广文法
2. 编号
3. 构建自动机 表or图 状态数少用图 状态多用表

![image-20200321164901428](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321164901428.png)



​				4.分析表

​       例子：
![image-20200321165715714](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321165715714.png)

![image-20200321165735254](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321165735254.png)

![image-20200321165804537](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321165804537.png)

***SLR(自动机)***

1. 变为增广文法

2. 编号 求FOLLOW集合

3. 图

   

![image-20200321170838589](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321170838589.png)

![image-20200321170858619](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321170858619.png)

![image-20200321171107480](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321171107480.png)

![image-20200321171118629](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200321171118629.png)

有直接左递归的不是ll1自动机

![image-20200324142930051](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200324142930051.png)

![image-20200324144217519](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200324144217519.png)

![image-20200324150647735](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200324150647735.png)

移入规约冲突（合并同心集不会出现）

![image-20200324150755096](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200324150755096.png)

![image-20200404141150019](work.assets/image-20200404141150019.png)

第一次进是继承属性 第二次是综合属性

