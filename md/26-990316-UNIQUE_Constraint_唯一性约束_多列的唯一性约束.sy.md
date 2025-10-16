---
show: step
version: 1.0
enable_checker: true
---

# 序列sequence

###  回忆
- 上次了解了id的来源
	- id 就是identification
		- 是一种唯一性的标识
- 需要给id列添加约束(Constraint)
	- 唯一性约束 UNIQUE
- 但是在添加约束的过程中报了错

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686278976208)

- 这怎么办呢？🤔

### 去除重复id

- 主要是刘备和赵云id已经重复了
	- 所以无法设置本列为唯一(UNIQUE)列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686279485457)

- 将赵云这条记录删除之后
	- 再设置id的属性

```
DELETE FROM heroes WHERE name = '赵云';
```

### 设置

```
ALTER TABLE 
    heroes
ADD UNIQUE(id)
;
```

- 这回可以设置id列为UNIQUE

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686279642744)

- 然后\d heroes
	- 查看heroes表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686279623326)

- 确实添加了一条唯一约束

### 再尝试

```
INSERT INTO heroes(id,name,fight,intelligence)
VALUES(1,'赵云',96,96);
```

- 再次尝试插入赵云
	- 注意赵云id与刘备id相同

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686296332295)

- 由于id列上有UNIQUE约束
	- 造成了插入失败
- 如何理解UNIQUE约束呢？

### UNIQUE

- https://www.postgresql.org/docs/16/sql-createtable.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686296620870)

- UNIQUE 约束下的列	
	- 必须是不同的值
- 可以删除UNIQUE约束吗？

### 删除约束

```
\h ALTER TABLE
```

- 先查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686297165356)

- 然后找到约束的名字(constraint_name)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686297266924)

- 观察约束的名字
	- heroes_id_key

### 尝试删除约束

```
ALTER TABLE
    heroes
DROP CONSTRIANT
	heroes_id_key
;
```

- 运行成功

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686297307387)

- 再观察表格

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686297468889)

- 约束消失了

### 再观察文档

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686296764623)

- 好像不光可以对于单个列设置UNIQUE
	- 还可以对几个列设置UNIQUE
	- 这如何理解？

### 对两个列设置UNIQUE

```
ALTER TABLE
    heroes
ADD
    UNIQUE(id,fight)
```

- 对两列设置UNIQUE

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686297601603)

- 设置结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686297639153)

- 产生了两列的UNIQUE

### 验证约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686297907813)

- 只有id和fight都同时相同的的时候
	- 才会 插入失败
	- 否则 会插入成功
- 我们先试试
	- 如果只有id相同
	- 但是武力不相同

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686298220201)

```
INSERT INTO 
    heroes(id,name,fight,intelligence)
VALUES
    (1,'赵云',95,95);
```

- 插入成功

### id不同，但武力相同

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686298251722)

- 武力与关羽相同
- id与刘备相同
- 但是武力、id不同时相同

```
INSERT INTO 
    heroes(id,name,fight,intelligence)
VALUES
    (1,'赵云',96,96);
```

### 如果武力、id都相同

- 如果两项同时相同
	- 数据是无法插入的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686298353549)

- 这就是多个列上的UNIQUE约束的定义
- 一般会用到什么地方呢？

### 具体应用场景

- 比如说下图是一个ER图
	- Entity-relationship model

- 图形的含义如下
	- 矩形的是实体表
	- 圆形的是实体表的字段
	- 菱形的是关系表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686300100064)

- 在学习关系中
	- 学生和课程都相同的话
	- 就算重复
- 在课程所属关系表中
	- 课程和老师都相同的话
	- 就算重复
- 这两个地方
	- 应该有相应的约束

### 建表细节

- https://www.postgresql.org/docs/12/ddl-constraints.html#DDL-CONSTRAINTS-UNIQUE-CONSTRAINTS

- 如果是单列的唯一性约束
	- 用下图中前两种

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304334283)

- 如果是多列的唯一性约束
	- 用上图中最后一种

## 总结

- 这次了解了 在两个列上的UNIQUE约束
	- 只有两列都相同的时候
	- 才会拒绝插入
- 继续看文档
	- https://www.postgresql.org/docs/16/sql-createtable.html 

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686300401457)

- 什么是NULL呢？
	- 如何使用呢？
- 下次再说？👋🏻