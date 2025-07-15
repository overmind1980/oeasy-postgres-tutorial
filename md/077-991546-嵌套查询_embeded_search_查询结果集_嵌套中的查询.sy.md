---
show: step
version: 1.0
enable_checker: true
---

#   嵌套查询_embeded_search_查询结果集_嵌套中的查询 

###  回忆

- 上了解了 聚合函数 
	- aggregate function 中
	- aggregate 的 词根词源

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230824-1692883923363)

- 这种嵌套查询的方法
	- 还有什么样的妙用吗？

### 观察表格

- 武将表 加了三列
	- city 出生地 籍贯
	- nation 所属政权名
	- items 持有宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687493693326)

- 能否看看刘备持有的宝物呢？

### 一层筛选

```
SELECT 
    items
FROM 
    heroes
WHERE
    name = '刘备'
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687494020258)

### 另一种筛选

```
SELECT 
    *
FROM 
    items
WHERE
    name = '双股剑'
;
```

- 筛选结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687494129294)

- 能不能把这两个查询合在一起呢？

### 嵌套查询

```
\c sanguo

SELECT 
    *
FROM 
	items
WHERE 
	name = 
		(
	    SELECT 
	        items
		FROM 
	    	heroes
		WHERE
	    	name = '刘备'
	    )
;
```

- 这查询是
	- 查询 刘备所拥有的 宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692968968055)

- 那是否能查询
	- 持有 双股剑 的英雄呢？ 

### 持有 双股剑 的英雄

```
\c sanguo

SELECT 
    *
FROM 
	heroes
WHERE 
	items = '双股剑'
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692969207251)

- 可以查询 
	- 比 双股剑 持有者 武力 高的英雄吗？

### 比 双股剑 持有者 武力 高的英雄

```
\c sanguo

SELECT 
    *
FROM 
	heroes
WHERE 
	fight > (
		SELECT
			fight
		FROM
			heroes
		WHERE
			items = '双股剑'
	)
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230825-1692969515527)

- 确实武力都大于60

## 总结🤔
- 这次 使用 嵌套形式 进行sql查询
	- 将查询出的结果 作为 筛选的条件 
	- 再 进行查询
- 可以使用 聚合函数的结果
	- 作为 筛选的条件吗？🤔
- 下次再说？👋🏻