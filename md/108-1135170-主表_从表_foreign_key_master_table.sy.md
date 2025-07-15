---
show: step
version: 1.0
enable_checker: true
---

#    主键_外键_主表_从表_foreign_key_master_table       
 
##  回忆

- 上次了解了
	- 主属性
		- 任何候选键中的属性
	- 非主属性
		- 不在任何候选键中的属性
- 2NF 有两个条件
	1. 首先得是第一范式
	2. 不能有非主属性 函数依赖于 任何候选键的子集
- 美食城 拆表得到的两个表
	- 符合了2NF的定义
	- 这两个表之间有什么关系吗？

### 生成ER图

- 打开网站
	- https://www.freedgo.com

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695887406985)

- 新建图形

### 建立模型

- 选择 从数据库
	- 从sql生成er图

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695887464696)

- 点击后 准备输入sql语句

### 输入语句

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695887564827)

- 输入sql语句

```
CREATE TABLE bill(
	ic_id VARCHAR(10),
	dk_id VARCHAR(10),
	deal_time timestamp without time zone,
	price NUMERIC
)
;

CREATE TABLE stall(
	dk_id VARCHAR(10),
	shop VARCHAR(20),
	shop_owner VARCHAR(20)
)
;
```

### 生成ER图

- ER图就是
	- Entity 实体
	- Relation 关系
	- Diagram 图

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695887607841)

- 这两个表
	- 谁是实体？
	- 谁是关系？

### 实体关系

- stall 是 档口实体

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695887805244)

- bill 是 档口实体的关系

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695891815564)

- 到底是什么关系？

### 一对多的关系

- 一个档口id可以有多个账单关系

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695887976128)

- 可以在他们之间添加
	- 一对多连线
	- 一个档口 对应 多个账单 

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695891879175)

- 他们两个表之间什么关系呢？

### 主表 和 从表

- stall 是 主表
	- Master Table
	- 主表的主键dk_id被从表引用

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695891879175)

- bill是从表
	- Slave Table
	- 从表中的dk_id 
		- 引用着主表stall的主键dk_id
- dk_id 是 表bill 的外键
	- foreign key

##  总结🤔

- 这次了解了 
	- 主表 master table
	- 从表 slave table
- 主表的主键 是从表的外键
	- 究竟什么是外键
	- foreign key？
- 下次再说？👋

