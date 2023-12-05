---
show: step
version: 1.0
enable_checker: true
---

#   时间日期类型_date_time_数据类型 
 

##  回忆

- 上次研究了 postgres的取整
	- round
		- 一般是最近数取整 四舍五入
		- 对于 双精度取整
			- 使用 nearest to even
			- 银行家取整
	- ceil 
		- 天花板
	- floor
		- 地板
- 对于 日期类型数据的差
	- 可以直接 得到年份吗？

```
\c sanguo

SELECT 
	'160/7/16'::date
;
```

###  查询帮助

- https://www.postgresql.org/docs/15/functions-datetime.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693629771546)

- 可以将 datetime 类型中
	- 某个日期单位 解压出来

### 尝试释放

```
SELECT 
	EXTRACT(YEAR FROM TIMESTAMP '2001-02-16 20:38:40');
```

- 确实可以释放 年份

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693630011553)

- 想要查询出 刘备的出生日期
	- 然后 得到 出生年份 可以吗？

### 构造环境

```
\c sanguo

CREATE TABLE bro(
	id SERIAL,
	name VARCHAR(20),
	birth_day date
)
;

INSERT INTO
	bro(name,birth_day)
VALUES
	('刘备','160/7/16'),
	('关羽','161/5/13'),
	('张飞','162/4/19'),
	('赵云','168/10/23')
;
```

-  准备开始查询

### 查询

```
\c sanguo

SELECT 
	birth_day
FROM 
	bro
WHERE
	name = '刘备'
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693630281845)

### 解压出年份
```
\c sanguo

SELECT 
	EXTRACT(
		YEAR FROM (
			SELECT 
				birth_day
			FROM 
				bro
			WHERE
				name = '刘备'
		)
	)
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693630493917)

### 更多思考

- 能否 找到
	- 刘备 活到今天 到底几岁
	- 刘备 与 赵云之间 相差几岁
	- 刘备 诞辰2000周年 到底是哪天？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693630667169)

###  总结

- 在日期时间函数中
	- 找到了 EXTRACT 
		- 可以解压出 年月日
	- EXTRACT 不仅 postgres 支持
		- oracle、mysql 都支持
		- 是sql 标准的一部分

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230901-1693573150061)

- 日期类型 也是 sql标准的一部分
	- 列 使用 这种类型
	- 就可以使用针对这种类型的 运算和函数
	- 相对 纯字符串 有很大进步
	- 也实现了1NF

- 1NF 还有什么 应用的场景吗？🤔
- 下次再说？👋🏻
