---
show: step
version: 1.0
enable_checker: true
---

# 主键约束 Primary key 词源

###  回忆
- 上一次我们研究了CHECK约束
	- 可以控制列中的字段满足一些条件
		- 数字字段 大于零
		- 文本字段长度 大于三个字符
		- 开始时间 小于 结束时间
- 可以对于这个CHECK约束
	- DROP 删除
	- ADD 添加 
- 现在我们学了三类约束
	- 非空 NOT NULL
	- 唯一 UNIQUE
	- 检查 CHECK
- 还有什么其他的约束吗？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687256220831)

### 观察文档

- 主键约束(primary key constraint)
	- 暗示着一列或者若干列应该同时是
		- 非空的 NOT NULL
		- 唯一的 UNIQUE

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687257782178)

- 去做一个具体实验

### 具体验证

```
CREATE TABLE products (
    product_no integer UNIQUE NOT NULL,
    name text,
    price numeric
);
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687257898189)

- 那么添加一个主键是什么效果呢？

### 主键约束
```
CREATE TABLE products2 (
    product_no integer PRIMARY KEY,
    name text,
    price numeric
);
```

- 如此就声明了一个主键约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687258009826)

- products2表中的product_no字段
	- 可以是空的吗？

### 非空的 NOT NULL

- 尝试插入数据

```
INSERT INTO
    products2(name,price)
VALUES
    ('book',15)
;
```

- 插入结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687258168827)

- products2表中的product_no字段
	- 可以是重复的吗？

### 唯一的 UNIQUE

```
INSERT INTO
    products2(product_no,name,price)
VALUES
    (1,'book',15)
;

INSERT INTO
    products2(product_no,name,price)
VALUES
    (1,'toy',10)
;
```

- 插入结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687258290582)

- 插入失败

### 主键约束的总结

- 主键约束(primary key constraint)
	- 暗示着一列或者若干列应该同时是
		- 非空的 NOT NULL
		- 唯一的 UNIQUE

- 主键可以是若干列的一个组合吗？

### 复合主键

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687258613430)

- 代码

```
CREATE TABLE example (
    a integer,
    b integer,
    c integer,
    PRIMARY KEY (a, c)
);
```

- 复合主键什么效果呢？

### 复合主键应用

- 可以在 列组合 上
	- 建立 复合主键

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687258785747)

- 如何理解 列组合 的 
	- 非空 NOT NULL
	- 唯一 UNIQUE

### 复合主键 非空效果

```
INSERT INTO
    example(a,b,c)
VALUES
    (null,2,3);
```

- a、c两列都声明了NOT NULL
	- 都不能是空的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687259004430)

### 复合主键 唯一效果
```
INSERT INTO
    example(a,b,c)
VALUES
    (1,2,3)
;

INSERT INTO
    example(a,b,c)
VALUES
    (2,2,3)
;

INSERT INTO
    example(a,b,c)
VALUES
    (1,2,1)
;

SELECT * FROM example;
```

- a、c两列上声明了唯一性UNIQUE
	- 两列可以有重复
	- 但不可以同时重复

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687259166304)

- 如果同时重复如何呢?

### 同时重复

- 如果同时重复了
	- 就违反了UNIQUE约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687259273742)

- 会报错！
- 那既然有了
	- 非空约束 NOT NULL
	- 唯一约束 UNIQUE 
- 为什么还需要有一个
	- 主键约束 PRIMARY KEY呢？

### 主键的意义

- 非空约束 NOT NULL 和 唯一约束 UNIQUE 可以有很多
	- 但是主键只有一个！

>A table can have at most one primary key. (There can be any number of unique and not-null constraints, which are functionally almost the same thing, but only one can be identified as the primary key.) Relational database theory dictates that every table must have a primary key. This rule is not enforced by PostgreSQL, but it is usually best to follow it.

- 这是基于
	- 关系数据库理论 的
	- Relational databae theroy

### 理论源头

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687259675666)

- CODD当时那篇1970年的论文里面
	- 提到了Primary Key

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687259730443)

- 如何理解
	- 约束很多
	- 但是主键只有一个呢？

### 员工表

- 工作证号满足唯一非空
- 身份证号也满足唯一非空

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687259778171)

- 最终选择工作证号作为
	- 主键 Primary Key
- 身份证号 作为
	- 替代键 Alternate Key

## 总结🤔
- 我们这次了解了主键
	- Primary Key

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687261961254)

- 主键包含两个约束CONSTRAINT
	- 非空约束 NOT NULL CONSTRAINT
	- 唯一约束 UNIQUE CONSTRAINT
- 主键
	- 可以是一列
	- 也可以是若干列的组合
- 我们可以给sanguo表中的heroes表
	- 添加主键约束吗?🤔
- 下次再说？👋🏻