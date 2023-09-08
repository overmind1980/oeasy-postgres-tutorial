---
show: step
version: 1.0
enable_checker: true
---

#  嵌套查询_根据聚合函数结果_进行查询
 

##  回忆

- 上次了解了 嵌套查询
	- 将查询的结果 作为 筛选的依据
	- 就可以进行 嵌套查询
		- 张飞宝物的所在城市
		- 张飞出生城市的所有宝物
		- 张飞所在政权的所有武将

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692929262150)

- 但是有个问题
	- 如果 我想查的是
		- 曹操所在政权的 所有武将的
			- 所有出生地
- 这又应该如何查询呢？

### 一步步来

- 曹操所在政权的 所有武将的
	- 所有出生地

```
\c sanguo

SELECT
    nation
FROM
	heroes
WHERE
    name = '曹操'
;
```

- 先查询 曹操所在政权

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692932628180)

### 查询所有武将

```
\c sanguo

SELECT 
	name
FROM
	heroes
WHERE
	nation =(
		SELECT
			nation
		FROM
			heroes
		WHERE
			name = '曹操'
	)
;
```

- 根据政权 查询所有 英雄

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692932739300)

- 有好多英雄
	- 如何查询 他们 `所有的` 出生地呢？

### 查询出生地

```
\c sanguo

SELECT 
    city
FROM
    heroes
WHERE
    name IN (
		SELECT 
			name
		FROM
			heroes
		WHERE
			nation =(
				SELECT
					nation
				FROM
					heroes
				WHERE
					name = '曹操'
			)
	)
;
```

- 注意 对于集合 
	- 使用的是 IN
	- 而不是 等号=

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692933098131)

- 显然数据集有重复

### 去重

```
\c sanguo

SELECT 
    DISTINCT city
FROM
    heroes
WHERE
    name IN (
		SELECT 
			name
		FROM
			heroes
		WHERE
			nation =(
				SELECT
					nation
				FROM
					heroes
				WHERE
					name = '曹操'
			)
	)
;
```

- 去重结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692933194895)

- 如果想要查询的是 
	- 曹操所在政权 武将的所有宝物呢？

### 查询宝物

- postgres 是数据库
	- 也是 各种数据的 大宝库

```
\c sanguo

SELECT 
    DISTINCT items
FROM
    heroes
WHERE
    name IN (
		SELECT 
			name
		FROM
			heroes
		WHERE
			nation =(
				SELECT
					nation
				FROM
					heroes
				WHERE
					name = '曹操'
			)
	)
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692933386316)

## 总结🤔

- 这次深入了 SELECT 查询
	- 嵌套
		- 不止 一层嵌套
		- 可以是 多层嵌套
		- 查询 总是从 内层嵌套开始
		- 一层层 向外 最后得到 想要的结果
	- IN 关键字 
		- 查询的结果 可能是 元组集合
		- 可以使用IN 替代 = 完成查询
- heroes 表里面 有宝物
	- 这些宝物 是否都在 宝物表 里面呢？🤔
- 下次再说？👋🏻
