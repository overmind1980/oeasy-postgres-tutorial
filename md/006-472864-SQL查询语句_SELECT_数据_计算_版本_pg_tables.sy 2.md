---
show: step
version: 1.0
enable_checker: true
---

# 查询数据 SELECT

## 回忆

- 整个的结构
  - postgres是 生成数据宝库的 
  - 法宝
- 法宝 
	- 可以生成 
	- 数据大宝库(database)
- 数据大宝库里面
	- 有宝箱(table)
- 宝箱里面有格子
	- 也就是列(column)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650453524590)

- table可以进行增删改查

|功能|作用|
|---|---|
|新建表格 |CREATE TABLE |
|删除表格| DROP TABLE |
| 修改表格 | ALTER TABLE |
|表格描述 | \d <br/> \d oeasy* <br/>\d ?? <br/>|
- 有了宝箱
  - 如何看宝箱(table)里面
  - 有些什么`宝贝`呢？🤔

### 先搜索

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650162952918)

- 这次的关键字应该是 
	- SELECT

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163427767)

- 上面这个应该是有一个表
	- 叫做 pg_tables 
- pg_tables 
	- 记录着所有的表

### 在本机查询

- 在本机查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163583401)

- 找到最后的url网址
	- 看看例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163603483)

- 这个例子好简单

### 试练

```sql
SELECT 1 + 1;
```

- 查询到一行
	- 列名?column?
	- 结果为 2

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163662967)

- 这有什么意义吗？
	- 比如说综合排序
		- 其实本质上就是计算
- 可以把 pg 当做计算器来用了😄
	- 可以做大数计算么？

### 大数


```sql
SELECT 100000000 + 10000000000;
```

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804636563)

- 好像可以
	- 计算很大的整数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804682395)

- 支持
	- 更大数的运算吗？

### 超级大

- 超级大的
	- 也可以！！！

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804743138)

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657804754718)

- 处理得挺好的
	- 如何理解 SELECT 呢？

### 理解 SELECT

- SELECT 这个命令
  - 既不 
	- 新建删除宝库
  - 也不
	- 新建删除表
- 只是 
	- 发出一个问题
- 只求
	- 返回一个结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650455817337)

- 发送的这个东西就叫做 query
	- query 什么意思呢？

### Query

- 提出一个
	- 询问
	- question

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650455860353)

- 专业术语叫做
	- 发出一个查询(query)
	- 就是去问个事情

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678368658131)

- 我们用的语言就是SQL
	- Structured `Query` Language
	- 结构化`查询`语言

### 继续提问

```sql
SELECT 
	version();
```

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

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650163427767)

```sql
SELECT 
	*
FROM
	pg_tables
;
``` 

- 切换到 postgres数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678368749884)

- 然后查询

### 70行数据

- 返回的是结果集(result set)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678368796483)

- 可以逐条记录进行展示吗？

### 逐个记录 \x

- \?
	- 查询psql命令

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678368875737)

- \x
	- 可以将表格展示
		- 切换为逐条记录展示

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678369019237)

- 再次按下\x可以切换回来

### \t 开关

- 除了\x开关之外
	- 还有个\t开关

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678369196138)

- 开了之后只显示记录
	- 不显示标题

### \t 只显示记录 不显示标题

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678369283302)

- 上面的 开了tuple
- 下面的 关了tuple

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230309-1678369309088)

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

```
SELECT 
	*
FROM
	login
;
```

- login 确实有 2 列	
	- 但是表中 0 行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650166684619)

- 也就是说
	- 没有数据
	- 宝箱结构再好
	- 也 没用
- 空宝箱 
	- 啥也没有

### 空箱子

- 想要 查询记录
    - 必须 往宝箱里面 放东西
	- 也就是 向login表里
	- 插数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650456557774)

- 可以么？
	- 有了宝物
- 就可以用SELECT
	- 要求 将宝物呈现了！！！😄

### 总结

- SELECT 是查询命令
  - 可以计算 2+2
  - 可以查询版本号
  - 还可以查询有哪些表
    - SELECT \* FROM pg_tables;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650456766122)

- 但是
	- 新建的 login 表中
	- 没有数据
- 就像
  - 数据宝库的宝箱里面
  - 没有宝贝一样
- 如何 
	- 把宝贝放到格子里？🤔
- 或者说
	- 把数据插到表里？🤔
- 下次再说 👋
