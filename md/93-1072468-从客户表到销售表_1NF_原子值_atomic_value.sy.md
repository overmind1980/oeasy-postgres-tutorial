---
show: step
version: 1.0
enable_checker: true
---

#   从客户表到销售表_1NF_原子值_atomic_value 
 

##  回忆

- 上次研究了 文本匹配中的
	- 英文字符大小写敏感性的 问题
		- LIKE 敏感
		- ILIKE 不敏感
	- 这些都是sql 语言 通用的规则

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693645175510)

- 将数据规范为1NF 
	- 可以做很多 计算
	- 比原来的方式 效率提高很多
- 1NF 是什么意思来着？
- 还有什么好玩的应用吗？🤔

### 现有表格

- 现有表格为客户购买记录表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693705692273)

### 修改

- 将销售表 
	- 转化为了销售记录表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693705756171)

- 目前表格满足1NF
	- 能否建成 表格 

### 建表 插数据

```
CREATE DATABASE crm;

\c crm

CREATE TABLE sales(
	customer VARCHAR(30),
	product VARCHAR(30),
	address VARCHAR(30),
	supplier VARCHAR(30),
	telephone VARCHAR(30),
	price NUMERIC
)
;

```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693706611959)

- 是否可以插入数据呢？

### 插入数据

```
\c crm

INSERT INTO 
	sales(
	customer,
	product,
	address,
	supplier,
	telephone,
	price)
VALUES
	('杨明','ps4','定福庄1号','sony','800-600-8888',3000),
	('李婉','ps5','梆子井1号','sony','800-600-8888',10000),
	('李婉','mac','梆子井1号','apple','800-666-1234',10000),
	('刘青','mac','定福庄1号','apple','800-666-1234',10000),
	('胡喵','ps5','中蓝1号','sony','800-600-8888',10000)
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693707149886)

### 目前存在问题

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693708143904)

- 如果有新产品 
	- 但是还没有顾客 
	- 如何在表中添加
- 或者有新的供应商 
	- 还没有产品 
	- 应该如何添加
- 如果关于ps4的销售记录都消失了 
	- 那么ps4就消失了
- 如果sony的产品都消失了 
	- sony就消失了 
- Sony电话换了 
	- 要修改好多地方 

### 分析表格列之间关系

- 顾客 可以决定 
	- 客户地址
- 商品 可以决定 
	- 供应商
	- 电话
	- 价格

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693706218525)

- 是否有办法优化呢？

##  总结🤔

- 这次了解了一个销售表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693705874990)

- 希望以此为基础 构成一个 
	- CRM
	- 客户资源管理系统

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230903-1693707427718)

- 怎么做呢？
- 下次再说？👋🏻
