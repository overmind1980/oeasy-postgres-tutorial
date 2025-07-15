---
show: step
version: 1.0
enable_checker: true
---

#    主键_外键_主表_从表_foreign_key_master_table       
 
##  回忆

- 上次研究了 外键约束
	- foreign key constraints

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695893212858)

- 外键的作用
	- 减少冗余
	- 便于修改
	- 约束 数据 内容 
- 通过 
	- 主表的主键 
	- 从表的外键
- 可以有什么好处吗？

### 自然连接

```
\c chinese_food_city

SELECT 
    bill.*,
	stall.shop,
	stall.shop_owner
FROM
	bill,
	stall
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695897432517)

- 这种连接模式叫做全连接
	- 这显然没有还原到最原始的状态
- 如何才能 回到最初状态呢？

### 筛选效果

```
\c chinese_food_city

SELECT 
    bill.*,
	stall.shop,
	stall.shop_owner
FROM
	bill,
	stall
WHERE
    stall.dk_id = bill.dk_id
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695526535688)

- 这种全连接 加筛选 
	- 有没有一个名字呢？

### 等值连接

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695892353963)

- 因为stall.dk_id 和bill.dk_id
	- 是连接两个表的关键
	- 这两个值相等
	- 得到的连接就是等值连接

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695897917690)

### 去除重复

```
\c chinese_food_city

SELECT DISTINCT
    bill.*,
	stall.shop,
	stall.shop_owner
FROM
	bill,
	stall
WHERE
    stall.dk_id = bill.dk_id
;
```

- 在等值连接的基础上
	- 去除重复 
	- 添加 DISTINCT 关键字
- 这样的连接有名字吗？

### 自然连接 

- 自然连接(Natural join)是一种特殊的等值连接
	- 要求两个关系中进行比较的分量必须是相同的属性组
	- 并且在结果中把重复的属性列去掉
	- 等值连接并不去掉重复的属性列

```
\c chinese_food_city

SELECT DISTINCT
    bill.*
FROM
	bill
NATURAL JOIN
	stall
;
```

### 结果

- 自然连接
	- 建立 主表主键 和 从表外键的 等值连接
	- 然后去重

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695898532457)

- 自然连接 这个词从什么时候有的呢？

### 原始论文

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695898795242)

- 1970年那篇论文
- 里面第一次提到
- 自然连接

### 原文内容

- 供应商表
	- 供应商
	- 部件id
- 项目表
	- 部件id
	- 项目
- 项目和供应商的关系
	- 是通过 连接得到的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695898825199)

- 图6是 笛卡尔积
	- 全连接
	- 但是被叫做自然连接
- 图7是 
	- 今天意义上的 自然连接

##  总结

- 这次 了解了 自然连接
	1. 自然连接 首先是 等值连接
	2. 等值连接 去重 得到自然连接
- 拆开 数据表 
	- 让数据库 符合2NF
	- 通过自然连接 可以查询出完整信息
- 拆表的目的
	1. 减少冗余
	2. 一改全改
- 真的可以一改全改吗？
- 下次再说？👋

