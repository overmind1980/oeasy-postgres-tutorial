---
show: step
version: 1.0
enable_checker: true
---

# NOT NULL 是否可以为空

###  回忆
- 上次尝试了空值
	- 不向列中插入数据
	- 列中的数据就会是空值
	- 英文名称是NULL
- 也可以在INSERT的时候直接使用空值
- 查询的时候
	- 空值是可以通过DISTINCT去重的
- 多列的UNIQUE约束中
	- 空值默认是不同的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686303617459)

- 在查看表格的过程中
	- 也发现了NULL
	- 这是什么意思呢？

### 查询文档

- https://www.postgresql.org/docs/12/ddl-constraints.html#id-1.5.4.6.6

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304465762)

- 可以设置某一列
	- 必须是非空的
- 如果现在要在当前heroes库里面修改呢？

### 查询文档

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304600063)

- 尝试编写SQL语句

### 修改字段属性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304717635)

- 表中已经插入了fight值为空的记录

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304754039)

- 先删再改

### 修改列属性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304861747)

- 观察属性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304914059)

- 这样还可以往fight里面插空值吗？

### 再插数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686304994180)

- 无法插入空值数据
	- 而且还会浪费一个索引值

- 能把这个列再设置回可以为NULL吗？

### 查询文档

- 把NOT去掉好像就可以

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305078899)

- 实践失败

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305266167)

- 去查询ALTER TABLE

### 查询文档

- 可以把NOT NULL 这条约束
	- DROP掉

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305312843)

- 试验成功

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305332266)

### 查看表格

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305347641)

- fight列上的NOT NULL约束消失了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305418414)

- 可以插空数据了

## 总结🤔
- 这次了解了在列上的约束NOT NULL
	- 可以要求某列数据必须非空
	- 也可以DROP这条约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686305591750)

- 通过文档
	- https://www.postgresql.org/docs/12/ddl-constraints.html#id-1.5.4.6.6
- 我们已经了解了
	- 非空约束 NOT NULL 
	- 唯一性约束 UNIQUE
	- 第一种约束 CHECK是什么意思呢？🤔
- 下次再说？👋🏻