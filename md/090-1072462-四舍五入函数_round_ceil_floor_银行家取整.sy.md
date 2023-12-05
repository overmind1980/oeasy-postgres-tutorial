---
show: step
version: 1.0
enable_checker: true
---

#   时间日期类型_date_time_数据类型 
 

##  回忆

- 上次使用了 日期类型的运算
	- date 还可以加 interval
		- year
		- month
		- week
		- day
- date - date 得到一个 int 类型的数字
	- 应该如何计算年份呢？
	- 可以对结果进行四舍五入呢？🤔

### 搜索 

- 搜索 round
	- https://www.postgresql.org/docs/15/functions-math.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693625016615)

- 先试试 四舍五入
	- round

### round
```
\c sanguo

SELECT 
	round(3.1415926),
	round(3.1415926,2)
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693625296510)

### 如何理解 四舍五入

```
\c sanguo

SELECT 
	round(3.14,1),
	round(3.149999999,1),
	round(3.15,1)
;
```

- 结果确实是四舍五入

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693625860918)

### 细看帮助

- round 函数
	- 对于 一般的浮点型 
		- 使用 round to nearest integer
	- 对于 双精度浮点型 
		- 使用round to nearest even

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693626037806)

- 这是什么意思？

### 搜索 

- 不清楚就去搜

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693626124478)

- 总共有 六种取整方式
	1. 向零舍入 round towards zero (round down)
		- 向零舍入是指直接截去小数点后的数字
		- 不进行四舍五入
		- 3.1415926
			- 向零舍入后为3.0
	2. 向上舍入 round up
		- 向上舍入是指将小数点后的数字全部进位
		- 不进行四舍五入
		- 3.1415926
			- 向上舍入后为4.0
	3. 四舍五入 round to nearest
		- 四舍五入是指将小数点后的数字进行四舍五入
		- 如果小数点后的数字大于等于5，则进位
		- 否则舍去
		- 对于3.1415926
			- 四舍五入后为3.14
	4. 四舍五入 round to nearest
		- 四舍五入是指将小数点后的数字进行四舍五入
		- 如果小数点后的数字大于等于5，则进位
		- 否则舍去
		- 对于3.1415926
			- 四舍五入后为3.14
	5. 向偶数舍入（银行家舍入） round to nearest even
		- 向偶数舍入是指将小数点后的数字进行四舍五入
			- 并且如果小数点后的数字等于5
			- 则将前一位数字进行奇偶性判断
				- 如果前一位数字为偶数，则舍去5
				- 如果前一位数字为奇数，则进位
			- 对于3.1450，向偶数舍入后为3.14
			- 对于3.1550，则向偶数舍入后为3.16
			- 向偶数舍入也被称为银行家舍入
			- 因为许多银行机构使用这种舍入方式
	6. 向奇数舍入 round to odd
		- 逻辑与5 相对
		- 不常用

### 实验

```
\c sanguo

SELECT 
	round(3.1450,2),
	round(3.1550,2)
;
```

- 好像并没有效果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693627787172)

- 因为使用的是
	- 单精度浮点数
- 再次观察 帮助

### cast

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693628071134)

- 双精度 银行家取整
	- 后面不能跟小数位数

### 银行家取整的验证

```
\c sanguo

SELECT 
	round(314.50::double precision),
	round(315.50::double precision)
;
```

- 验证成功

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693628245593)

- 可以使用 
	- roundup 
	- rounddown
	- 吗？

### round up down

```
\c sanguo

SELECT 
	ceil(0.01),
	floor(0.99)
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230902-1693628491855)

###  总结

- 这次研究了 postgres的取整
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

- 下次再说？👋🏻
