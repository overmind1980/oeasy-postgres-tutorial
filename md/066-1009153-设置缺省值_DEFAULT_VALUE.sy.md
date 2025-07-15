---
show: step
version: 1.0
enable_checker: true
---

#  设置缺省值_DEFAULT_VALUE 

##  回忆

- 上次了解了count函数
	- count函数的作用是 计数
- 只要不是NULL的字段
	- 都会被计数
- 需要特别注意的是
	- 空串并不是真的空
	- NULL 才是真的空
		- 无法计数的那种
- 列可以被设置为
	- NOT NULL 
	- 不接受NULL这个值
- 但是空串和NULL
	- 还是容易混淆
	- 有什么办法可以避免吗？

### 观察heroes表

- 只有id列设置了
	- 非空
	- NOT NULL

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688826879393)

- 希望为宝物列
	- 设置一个默认值
		- `无`
- 如何修改呢?

### 观察文档

- 应该修改列
	- https://www.postgresql.org/docs/15/ddl-default.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688827034335)

- 设置列的默认值

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688827179244)

### 修改

```
ALTER TABLE
    heroes
ALTER COLUMN
    items
SET DEFAULT
    '无'
;
```

- 修改结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688827293102)

### 插入数据

```
INSERT INTO
    heroes(name)
VALUES
    ('张三')
;

SELECT 
    id,name,items
FROM 
    heroes
WHERE
    name = '张三'
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688827559876)

- 如果我就想在items列中
	- 插入空串或者空值呢？

### 插入空串
```
INSERT INTO
    heroes(name,items)
VALUES
    ('李四','')
;

SELECT 
    id,name,items
FROM 
    heroes
WHERE
    name = '李四'
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688827650219)

### 插入NULL值

```
INSERT INTO
    heroes(name,items)
VALUES
    ('王五',NULL)
;

SELECT 
    id,name,items
FROM 
    heroes
WHERE
    name = '王五'
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688827729684)

### 区分

```
SELECT 
    id,
    name,
    items,
    items = '' AS 是否为空串,
    items IS NULL AS 是否为空
FROM 
    heroes
WHERE
    id >=33
;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230708-1688827947642)

### 练习

- 将武将表
	- 武力、智力默认值设置为60
- 将宝物表
	- 默认城市设置为位置
- 在尝试
	- 将上述默认值去除

## 总结🤔
- 这次研究了默认值
	- DEFAULT VALUE 默认值
	- 默认值 是列上面的属性
	- 当没有明确的插入值时
	- 默认值起作用
		- '无' 是 具体的字符串
		- '' 是 空字符串
		- NULL 是 真空 不是字符串
- 只有NULL
	-	count函数 中不会被计数 
- count这个词 怎么来的呢？？🤔
- 下次再说？👋🏻