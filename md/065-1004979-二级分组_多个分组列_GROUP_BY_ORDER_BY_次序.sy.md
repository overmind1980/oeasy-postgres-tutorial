---
show: step
version: 1.0
enable_checker: true
---

#   count_计数函数_统计汇总 

##  回忆

次使用了GROUP BY关键字
	- 对于数据进行了分类统计的操作
		- 可以对 武将表中的武将的所属国 进行计数
		- 也可以对 宝物表中的城市 进行计数
- 可以
	- 对武将
		- 按出生城市
			- 进行汇总吗？🤔

### 回忆按照政权名汇总

```
\c sanguo

SELECT 
	nation,
    count(id) 
FROM 
    heroes
GROUP BY
	nation
;
```

- 按政权汇总结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230821-1692607648810)

- 将nation 换成city

### 按出生地进行汇总

```
:%s/nation/city/
```

- 替换后再执行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230821-1692607773561)

- 可以按照 
	- 政权名、出生地 两个字段
	- 进行汇总吗？

### 两个汇总列

```
\c sanguo

SELECT 
    city,
	nation,
    count(id) 
FROM 
    heroes
GROUP BY
	city,
	nation
;
```

- 汇总 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230821-1692613633506)

- 这样就可以 
	- 按照 所在政权 和 出生城市 两列
	- 进行汇总了
- 可以对汇总结果排序吗？

### 排序


```
\c sanguo

SELECT 
    city,
	nation,
    count(id) 
FROM 
    heroes
GROUP BY
	city,
	nation
ORDER BY
	city,
	nation
;
```

- 第一排序关键字 是 出生城市

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230821-1692613777772)

- 可以先按照 所在政权 排序吗？

### 修改 排序次序

```
\c sanguo

SELECT 
	nation,
    city,
    count(id) 
FROM 
    heroes
GROUP BY
	nation,
	city
ORDER BY
	nation,
	city
;
```

- 先按照 所在政权 进行排序

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230821-1692613911388)

- 交换 分组关键字次序
	- 会对结果产生影响吗？

### 交换分组 次序


```
\c sanguo

SELECT 
	nation,
    city,
    count(id) 
FROM 
    heroes
GROUP BY
	city,
	nation
ORDER BY
	nation,
	city
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230821-1692613911388)

- 不会产生变化

## 总结🤔

- 这次了解了二级分组
	- 不但有一个分组列
		- GROUP BY 的列
- 使用两个分组列
	- 就可以 产生 二级分组效果
- 如果使用多个列
	- 就可以 产生 多级分组效果
- 分组汇总的结果 
	- 可以使用 排序 来控制次序
- 是否可以 不用 分组列
	- GROUP BY 子句
	- 直接对整个结果集 进行计数呢？🤔
- 下次再说？👋🏻