---
show: step
version: 1.0
enable_checker: true
---

# 查询数据 SELECT

## 回忆

- 整个的结构
  - postgres是生成数据宝库的法宝
  - 法宝可以生成的数据宝库(database)
  - 数据宝库里面有宝箱(table)
  - 宝箱里面有格子
	- 也就是列(column)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650453524590)

- table可以进行增删改查
  - 新建表格
    - CREATE TABLE
  - 删除表格
    - DROP TABLE
  - 修改表格
    - ALTER TABLE
  - 表格描述
    - \d
    - \d oeasy*
- 有了宝箱
  - 如何看宝箱(table)里面有些什么宝贝呢？🤔

### 先搜索

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650162952918)

- 这次的关键字应该是 SELECT

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163427767)

- 上面这个应该是有一个表叫做 pg_tables 
	- pg_tables 记录着所有的表

### 在本机查询

- 在本机查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163583401)

- 找到最后的url网址
	- 看看例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163603483)

- 这个例子好简单

### 试练

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163662967)

- 查询到一行
	- 列名?column?
	- 结果为 2
- 可以把 pg 当做计算器来用了😄
	- 可以做大数计算么？

### 大数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804636563)

- 好像可以计算很大的整数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804682395)

- 支持更大的吗？

### 超级大

- 超级大的也可以

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804743138)

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804754718)

- 处理得挺好的
- 如何理解 SELECT 呢？

### 理解 SELECT

- SELECT 这个命令
  - 既不新建删除宝库
  - 也不新建删除表
- 只是发出一个问题
  - 只求一个返回结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650455817337)

- 发送的这个东西就叫做 query
	- query 什么意思呢？

### Query

- 提出一个询问(question)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650455860353)

- 专业术语叫做
	- 发出一个查询(query)
- 就是去问个事情

### 继续提问

- 查询当前 pg 的版本号

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163928050)

- 软件
	- 版本号为 12.9
	- 架构为 x86-64
	- 系统为 linux 20.04
	- 使用的编译器为 gcc (Ubuntu 9.3.0-17ubuntu1~20.04)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163936733)

- 有问必有答

### 第三问

- 查询表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163427767)

- 首先要确认
  - 新建了库
  - 进入了库
  - 新建了表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650164321749)

- 准备提问

### 进行查询

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650456276581)

- SELECT \* FROM pg_tables;
  - SELECT 是命令
  - 代表所有的列
  - FROM 是指定从哪个表查询
  - pg_tables 是表的名字

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650166533784)

- 返回的结果是结果集(result set)
- pg_tables
  - 是系统表
  - 里面存储着有些什么样的表
- 可以更细致地描述一下pg_tables吗？

### 先描述

- d(escribe)一下 
	- pg_tables 这个表
- pg_tables 
	- 是一个关于 table 的 table

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650164441524)

- pg_tables 表有 8 列
  - 方案名
  - 表名
  - 所有者
  - 表空间
  - 是否有索引
  - 是否有规则
  - 是否有触发器
  - 行的安全性
- 可以查询自己新建的 login 表么？

### 查询 login

- login 确实有 2 列	
	- 但是表中 0 行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650166684619)

- 也就是说没有数据
- 宝箱结构再好也没有意义
  - 空宝箱啥也没有

### 空箱子

- 我们想要查询到记录
  - 必须往宝箱里面放东西
	- 也就是向 login 表中插入数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650456557774)

- 可以么？
- 有了宝物
- 就可以让宝库将宝物呈现了！！！😄

### 总结

- SELECT 是查询命令
  - 可以计算 2+2
  - 可以查询版本号
  - 还可以查询有哪些表
    - SELECT \* FROM pg_tables;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650456766122)

- 但是新建的 login 表中
  - 没有数据
- 就像
  - 数据宝库的宝箱里面没有宝贝一样
- 如何把宝贝放到格子里？🤔
- 或者说把数据插到表里面？🤔
- 下次再说 👋
