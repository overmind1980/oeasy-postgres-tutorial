---
show: step
version: 1.0
enable_checker: true
---

#  max_最大值_min_最小值_聚合函数_aggregate_functions  

##  回忆

- 上次 小沃森 将IBM 
	- 从 精密机械 公司
	- 带到了 机电一体化 时代
	- 并且 成功研制出了 电子计算机
- 当时的 信息产业 还是一片无主之地
	- IBM 一骑绝尘
	- 小沃森 成为 时代弄潮儿
- 这一切 起源于 人口统计
	- 自动分拣 统计计数
	- 今天被称为count函数
- 除了count之外
	- 还有什么样的函数吗？🤔
### 查询

- 搜素count
	- https://www.postgresql.org/docs/15/tutorial-agg.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692432590981)

- 找到温度最高的温度
	- 然后根据温度找到相关记录
- 我们先试试查询最高值

### max

```
\c sanguo

SELECT 
    max(fight)
FROM
    heroes
;
```

- 查找 武力最大值

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692434355261)

- 最大值为100
- 到底是谁呢？

### 嵌套查询

```
\c sanguo

SELECT 
    name,
	fight
FROM 
    heroes
WHERE
    fight = (
		SELECT 
			max(fight)
		FROM
			heroes
	)
;
```

- 这里面有个嵌套查询
	- 括号中查询的结果就是100
	- 那 为什么 
		- 不硬编码为100
		- 直接写死呢？
- 如果有一个新武将 
	- 武力为101
	- 那么括号中的结果为101
	- 这个最大值是动态的
	- 是根据记录来的

### 结果

- 果然是吕布

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692434499880)

- 人中吕布
- 马中赤兔

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230820-1692501234651)

- 谁的武力最低呢？

### min

```
\c sanguo

SELECT 
    name,
	fight
FROM 
    heroes
WHERE
    fight = (
		SELECT 
			min(fight)
		FROM
			heroes
	)
;
```

- 总共有4位

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692434575683)

- 可以据此查询出 
	- 智力 最高 和 最低 的 人员吗？

### 宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692436677962)

- 可以查询 宝物表(items)中
	- 价值最高的宝物吗？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692436638161)

### 先查最高价值

```
\c sanguo

SELECT 
	max(value)
FROM 
    items
;
```

- 价值最高的是70

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692435807475)

- 到底是哪条记录价值最高呢？

### 嵌套查询
```
\c sanguo

SELECT 
    *
FROM
    items
WHERE
    value = 
	(
		SELECT 
			max(value)
		FROM 
			items
    )
;
```

- 顶级宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692436246790)

- 可以查出价值最低的宝物吗？

### 修改代码

```
\c sanguo

SELECT 
    *
FROM
    items
WHERE
    value = 
	(
		SELECT 
			max(value)
		FROM 
			items
    )
;
```

- 价值最低

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692437225437)

- 这里价值最低的值为5
	- 是 所有记录中 价值的最小值
- 可以得到 每个城市中
	- 价值最低宝物的值吗？

### 按城市汇总

```
\c sanguo

SELECT 
    city,
    min(value)
FROM
    items
GROUP BY
    city
;
```

- 汇总结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692437563306)

- 可以将 汇总结果按照降序排列吗？

### ORDER BY

```
\c sanguo

SELECT 
    city,
    min(value) AS min
FROM
    items
GROUP BY
    city
ORDER BY
    min DESC
;
```

- 搜索结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692437695908)

- 可以对于 城市进行筛选吗？
	- 我只想对 以下城市 汇总
		- 长沙 
		- 永安
		- 长安
		- 江州
		- 洛阳

### 筛选
```
\c sanguo

SELECT 
    city,
    min(value) AS min
FROM
    items
WHERE
    city IN ('长沙','永安','长安','江州','洛阳')
GROUP BY
    city
ORDER BY
    min DESC
;
```

- 筛选结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692437846876)

- 可以对于结果进行分页操作吗？
	- 我只想查询前三名

### 分页LIMIT
```
\c sanguo

SELECT 
    city,
    min(value) AS min
FROM
    items
WHERE
    city IN ('长沙','永安','长安','江州','洛阳')
GROUP BY
    city
ORDER BY
    min DESC
LIMIT
	3
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230819-1692438043237)

### 更多 查询练习

- 根据 国家 汇总武力的最大值
	- 筛选 国家 只从魏蜀吴中选取
		- 第一个 国家

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230820-1692501367599)

- 根据 地域 汇总 智力的最小值
	- 筛选 宝物 不为空的 英雄

## 总结🤔

- 这次 学习了 两个聚合函数
	- max
	- min
- 这两个函数
	- 可以对整个结果集 汇总
	- 也可以 根据 不同的 GROUP 进行汇总
		- 按照国家
		- 按照城市
- 可以 对于 最大值 和 最小值 
	- 同时进行汇总吗？🤔
- 下次再说？👋🏻
