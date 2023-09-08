---
show: step
version: 1.0
enable_checker: true
---

# 数据筛选_WHERE子句_clause_筛选数据 

###  回忆

- 东西方从古至今都有统计的习惯和方法
	- 封建帝王和领主为了收税和管理
		- 进行财产和人员的统计	 
		- 这些当年的大数据有助于封建主决策
- 不过这些数据大多是以文字方式存储的
- 由记录员可以实时对于数据进行一些筛选	
	- 比如汉代发现这家里面有年龄合适的妹子
	- 或者《末日审判书》发现这家领主需要交更多的税金
- 我们使用的SQL语言是如何进行数据筛选的呢？

### 准备环境

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687430281438)

```
SELECT 
    * 
FROM
    heroes
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687430369054)

### 进行数据筛选

```
SELECT 
    * 
FROM
    heroes
WHERE
    fight > 90
;
```

- 筛选结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687430460469)

- fight > 90 
	- 到底意味着什么呢？

### 筛选意味

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230701-1688212890646)

- 构造列

```
SELECT 
    *,fight>90
FROM
    heroes
;
```

- 观察效果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687430592790)

- 可以看到
	- 多了一列
	- 结果为
		- f 假的 False
		- t 真的 True
- 根据布尔值的真假
	- 然后再进行筛选
- 可以把智力值大于90的武将筛选出来吗？

### 进行筛选

```
SELECT 
    *,intelligence>90
FROM
    heroes
;
```

- 从结果来看

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687430854450)

- 只有关羽一人
	- 为真True
	- 真的智力大于90
- 是否会只筛选出关羽呢？

### 进行筛选

```
SELECT 
    * 
FROM
    heroes
WHERE
    intelligence > 90
;
```

- 筛选结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687431041214)

- 如何理解 WHERE子句呢？

### WHERE 子句

- WHERE子句就像一把筛子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687431083246)

- 将满足条件的记录筛了出来
	- 筛选出来的结果是原关系的子集
	- 投影的结果
		- 也是关系的子集
- 筛选 和 投影 有什么不同呢？

### 筛选和投影

- 投影是对于列进行选择

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650166146041)

- 而筛选是对于行进行选择

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687431736868)

- 这种大于小于生成布尔值的方式
	- 我们上次在CHECK约束的时候曾经见过

### 回顾CHECK约束

```
ALTER TABLE
    heroes
ADD CONSTRAINT
    fight_positive
CHECK
    (fight > 0)
;
```

- 添加约束之后的heroes表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687431970193)

- 无论插入还是更新
	- fight字段一定是大于0的
- 可以对于人名进行查找吗？

### 查找人名

```
SELECT 
    * 
FROM
    heroes
WHERE
    name = '张飞'
;
```

- 可以直接筛选出来

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432079184)

### 宝物筛选

- 我们还有另一个表 
	- 宝物表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432201726)

- 可以对于宝物进行筛选吗？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432218520)

### 筛选要求

- 筛选出所有北海的宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432361119)

- 这个要求你自己改写SQL语句

```
SELECT 
    * 
FROM
    heroes
WHERE
    name = '张飞'
;
```

### 按效果筛选

- 筛选出所有寿命延长的宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432408250)

### 按价值筛选

- 筛选出所有价值大于等于50的宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432455267)

### 按名字筛选

- 筛选出名为资治通鉴的宝物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432545300)

- ❌
	- 写资治通鉴的司马光出生于宋代
	- 三国数据库中没有记载

## 总结
- 这次我们讲了筛选(Selection)
	- 筛选靠的是WHERE子句
	- WHERE子句后面跟一个条件
		- 条件在每一行返回一个布尔类型的数值
		- 根据布尔值的真假
		- 对于数据进行筛选

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687481739853)

- 但是 这个布尔类型的列的列名
	- 很奇怪
	- 可以给他一个更明确的列名吗？
- 下次再说？👋🏻	- 可以给他一个更明确的列名吗？

