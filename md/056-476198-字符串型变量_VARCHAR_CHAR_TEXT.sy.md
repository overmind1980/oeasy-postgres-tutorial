---
show: step
version: 1.0
enable_checker: true
---

# 字符串型变量_VARCHAR_CHAR_TEXT   

##  回忆

- 上次研究的是类型转化
	- 数值型
		- 整数
		- 浮点数
		- 高精度十进制
	- 字节序列
	- 字符串
- 字符串中的长度设置有什么意义吗？🤔

### 字符串类型

- https://www.postgresql.org/docs/16/datatype-character.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688029065162)

- 具体类型总共三种
	- 可变长 VARCHAR(n)
	- 固定长度 CHAR(n)
	- 无限长度 TEXT
- 先来看看可变长

### 可变长 VARCHAR

```
CREATE TABLE test1 (a VARCHAR(4));
INSERT INTO test1 VALUES ('ok');
SELECT a, char_length(a) FROM test1; 
```

- 插入正常

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688029402291)

- 如果插入的字符串超过可变长的范围4呢？

### 超过限度

```
INSERT INTO test1 VALUES ('oeasy');
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688029472064)

- 直接报错
- 可以先截取字符串吗？

### 先截取 再插入

```
INSERT INTO test2 VALUES ('oeasy'::varchar(4)); 
-- explicit truncation
SELECT a, char_length(a) FROM test1; 
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688029654397)

- 截取之后
	- 确实是可以插入的
- 如果被插入字符串
	- 结尾处都是空格
	- 且超过了限度
	- 会如何呢？

### 超过限度

```
INSERT INTO test1 VALUES ('oea    ');
SELECT a, char_length(a) FROM test1; 
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688029912166)

- 以上是不定长的列
- 定长的列什么效果呢？

### 定长的列

```
CREATE TABLE test2 (a CHAR(4));
INSERT INTO test2 VALUES ('ok');
SELECT a, char_length(a) FROM test2; 
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688030205668)

- 插入、查询方式和VARCHAR一样
- 溢出的效果呢？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688030328921)

- 溢出效果也一样
- 这两种类型有什么不一样吗？

### VARCHAR 和 CHAR 的不同

- test1中类型为VARCHAR(4)
- test2中类型为CHAR(4)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688030387883)

- 定长就直接存储
- 可变长会自动加上空格

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688030898210)

- 但是在 char_length 的时候
	- 又会去掉结尾部分的空格
- 对于char_length 函数
	- 如果非ASCII字符
		- 究竟是按照字符数还是字节数呢？

### 字节还是字符？

- 构造环境

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688031505077)

- 是按照字符数来的
- 可以在帮助文件中查到吗？

### 帮助手册

- https://www.postgresql.org/docs/15/functions-string.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688031774832)

| 函数名 |函数功能 |
|---|---|
| bit_length | 返回字符串共多少位 |
| char_length | 返回字符串共多少字符 |
| octet_length | 返回字符串共多少字节 |

### 尝试使用

```
SELECT 
    a, 
    char_length(a),
    bit_length(a),
    octet_length(a)
FROM 
    test2; 
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688032242527)

- 以上两种列的数据类型
	- VARCHAR 和 CHAR
	- 都是SQL语言规定好的
		- 列的数据类型

### TEXT

- TEXT 是postgres自定义的列的类型
	- 无限长度的字符串
	- 最大可达1G

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688031330724)

- 尝试使用


```
CREATE TABLE test3 (a TEXT);
INSERT INTO test3 VALUES ('oeasy    ');
SELECT a, char_length(a) FROM test3; 
```

- TEXT本质上是长度几乎为无限的
	- 可变长的字符串类型

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688032539791)

- 还有两种定长字符串

### 名字和单字

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230629-1688032608034)

- 这是两种字符串类型
	- 64 bytes 的 Name
	- 1 byte 的 char
- 在IBM读卡器的时代
	- 究竟是如何存储字符串的呢？

## 总结🤔
- 这次我们研究了字符串类型的变量
	- CHAR(n) 定长度
	- VARCHAR(n) 有限可变长度
	- TEXT 无线可变长度
- 字符串变量可以进行模糊匹配吗？
- 下次再说？👋🏻