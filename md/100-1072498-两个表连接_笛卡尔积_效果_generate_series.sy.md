---
show: step
version: 1.0
enable_checker: true
---

#    表格去除冗余_提取其中的数据_一个表变两个表    
 
##  回忆

- 上次从一个表bill
	- 变成了 两个表
		- bill
		- stall

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694008210314)

- 去除了冗余
	- 但是能将这个数据恢复成一个表吗？

### 表的连接

```
\c chinese_food_city

SELECT
	ic_id,
	shop
FROM
	bill,
	stall
;
```

- 结果 共28条记录

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694009689458)

- 如何理解 FROM 后面 
	- 有两个表呢？

### 了解函数generate_series

- generate_series
	- https://www.postgresql.org/docs/current/functions-srf.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694010747810)

- 通过 这个应该可以得到一些系列

### 得到 奇数系列

```
SELECT	
	* 
FROM 
	generate_series(1,5,2);
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694010856107)

### 得到 偶数序列

```
SELECT	
	* 
FROM 
	generate_series(2,4,2);
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694010908997)

### 两系列连接

```
SELECT
	odd,
	even
FROM	
	generate_series(1, 5, 2) AS odd, 
	generate_series(2, 4, 2) AS even
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694011310950)

- 这如何理解？

### 表的乘积

- 3条奇数的表 
	- 逗号(,) 
		- 2条 偶数记录的表 
	- 得到 6条记录

- 7条消费记录
	- 逗号(,)  
		- 4条 档口记录
	- 得到28条记录

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230907-1694059000559)

- 这个东西能否筛选呢？

### 筛选

```
\c chinese_food_city

SELECT
	*
FROM
	bill,
	stall
WHERE
	bill.dk_id = stall.dk_id
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230907-1694088334993)

- 基本还原到最初表的状态
	- 但是多了一行dk_id
	- 能否完全还原到 最初表的状态呢？

### 投影

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
	bill.dk_id = stall.dk_id
;
```

- 表完全 还原到最初的状态了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230907-1694088489062)

- 绕这么一大圈
	- 为什么呢？

### 分表的意义

1. 去除冗余
	- 将数据量降低

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694008210314)

2. 便于修改
	- 档口所属门店 和 所有者 如果修改
	- 只需要修改一次

##  总结🤔

- 这次 将分开的两个表
	- 进行了逗号运算

```
\c chinese_food_city

SELECT
	*
FROM
	bill,
	stall
;
```

- 得到了一个两者乘积大的结果集
	- 又通过筛选 得到了最初原来的结果集
- 这个逗号运算
	- 应该如何理解呢？
- 下次再说？👋🏻
