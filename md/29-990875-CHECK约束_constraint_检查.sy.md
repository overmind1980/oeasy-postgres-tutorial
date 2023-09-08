---
show: step
version: 1.0
enable_checker: true
---

# CHECK约束

###  回忆
- 上次了解了在列上的约束NOT NULL
	- 可以要求某列数据必须非空
	- 也可以DROP这条约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305591750)

- 通过文档
	- https://www.postgresql.org/docs/12/ddl-constraints.html#id-1.5.4.6.6
- 我们已经了解了
	- 非空约束 NOT NULL 
	- 唯一性约束 UNIQUE
	- 第一种约束 CHECK是什么意思呢？

### 理解约束

- pg中的数据类型还是比较粗糙的
	- 比如价格 应该只能接受正数
	- 但是没有这样一个数据类型

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687231356020)

- 于是就有了约束
	- 可以给列加上约束条件
	- 如果插入或者修改数据的时候
		- 不满足约束条件
		- 就会报Error

### CHECK 约束

```
CREATE TABLE products (
    product_no integer,
    name text,
    price numeric CHECK (price > 0)
);
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687231768897)

### 分析CHECK约束

- check约束是最常见的约束
- 想要插入或修改记录
	- 就要满足CHECK约束
		- 就必须让约束对应的布尔运算值为True

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687232001500)

- 约束定义位于数据类型之后

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687232031349)

- 每个约束都可以有个名字
- 我们去试试

### 约束的名字

```
DROP TABLE
    products;

CREATE TABLE products (
    product_no integer,
    name text,
    price numeric CONSTRAINT positive_price CHECK (price > 0)
);
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687232125158)

- 明确约束的名字

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687232138853)

- 明确约束的名字有什么好处呢？

### 约束名字的作用

- 可以用来删除约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687232575335)

- 删了之后还可以再添加吗？

### 添加CHECK约束

- 可以再添加

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687232767753)

- CHECK约束还有什么好玩的吗？

### 列间比较

```
DROP TABLE
    products;

CREATE TABLE products (
    product_no integer,
    name text,
    price numeric CHECK (price > 0),
    discounted_price numeric CHECK (discounted_price > 0),
    CHECK (price > discounted_price)
);
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687233054974)

- 这种CHECK约束
	- 在开始日期和结束日期中很常见

### 小任务

- 我们要进入sanguo库
	- 对heroes表中的武力、智力字段
		- 添加CHECK约束
			- 要求他们都要大于90

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687233818330)

- 已经存在的数据不满足CHECK约束的话
	- 就无法添加约束

### 继续设置

```
ALTER TABLE
    heroes
ADD CONSTRAINT
    fight_positive
CHECK
    (fight > 0)
;
```

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687233588275)

- 这样就对武力这一列设置了CHECK约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687233619035)

- 还需要你对于智力这一列
	- 设置CHECK约束噢！

## 总结🤔

- 这一次我们研究了CHECK约束
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

- 下次再说？👋🏻