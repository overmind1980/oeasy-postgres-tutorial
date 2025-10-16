---
show: step
version: 1.0
enable_checker: true
---

#    升序降序_ASC_DESC_ascend_descend_词源词根  

##  回忆

- 上次我们理解了字符串类型变量排序的逻辑
	- 首先要能对字符串类型变量进行比较
	- 方法是
		- 先比较字符串的第0个元素 
			- 如果不同 就得出结论
			- 如果相同 
				- 就比较字符串的第1个元素
				- 以此类推
	- 这方法和python中比较序列类变量是一致的
- 字段 比较了之后 有什么意义吗？🤔

### 智勇

- 如果 智力 大于 武力
	- 人物属性 为 智
- 否则
	- 人物属性 为 勇

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692231986979)

- 我想要 把这个 
	- 智 或者 勇
	- 显示出来 可以吗？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692231629390)

### 创造环境

- vi test.sql

```
\c sanguo

SELECT 
    name,
    fight,
    intelligence
FROM 
    heroes
;
```

- w|!sudo -u postgres psql -f %

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692232416732)

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692232479561)

- 在此基础上 判断 
	- 智勇 

### 查询

- https://www.postgresql.org/docs/15/functions-conditional.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692233075902)

### 条件判断
```
\c sanguo

SELECT 
    name,
    fight,
    intelligence,
    CASE
    	WHEN fight<intelligence THEN '智'
    	ELSE '勇'
    END 
    AS character 
FROM 
    heroes
;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692233214942)

- 可以 做出 更多分支判断吗？

### 优良中差

- 想对于 武力 进行四档分级

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692233381863)

- 这应该怎么办呢？

### 四档分支

```
\c sanguo

SELECT 
    name,
    fight,
    CASE
    	WHEN fight>=90 THEN '优'
    	WHEN fight>=80 THEN '良'
    	WHEN fight>=60 THEN '中'
    	ELSE '差'
    END 
    AS fight_level 
FROM 
    heroes
;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692233594149)

- 可以按照 武力等级 进行排序吗？

### 排序

```
\c sanguo

SELECT 
    name,
    fight,
    CASE
    	WHEN fight>90 THEN '优'
    	WHEN fight>80 THEN '良'
    	WHEN fight>90 THEN '中'
    	ELSE '差'
    END 
    AS fight_level 
FROM 
    heroes
ORDER BY
	fight_level DESC
;
```

- 搜索结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692236302082)

- 可以筛选出 所有武力差的人吗？

### 筛选

```
\c sanguo

SELECT 
    name,
    fight,
    CASE
    	WHEN fight>90 THEN '优'
    	WHEN fight>80 THEN '良'
    	WHEN fight>90 THEN '中'
    	ELSE '差'
    END 
    AS fight_level 
FROM 
    heroes
WHERE
    fight_level = '差'
ORDER BY
	fight_level DESC

;
```

- 执行失败了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692236561340)

- 就想用新的一列 进行筛选 
	- 应该 怎么办呢？

## 总结
- 这次 研究了 条件表达式
	-  Conditional Expressions
	- 具体来说就是 CASE WHEN
- 可以分类
	- 将人物分为 
		- 智
		- 勇
	- 可将 武力分成
		- 优良中差
	- 但是无法根据 武力等级 
		- 进行筛选
- 想要筛选 应该怎么办呢？🤔
- 下次再说？👋🏻