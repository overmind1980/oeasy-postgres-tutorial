---
show: step
version: 1.0
enable_checker: true
---

# 序列sequence

### 回忆

- 上次了解了serial的词源

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685882881510)

- serial 是一种数据类型
- 应该如何理解这种数据类型呢？🤔

### 查看文档

- https://www.postgresql.org/docs/16/datatype-numeric.html#DATATYPE-SERIAL

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685885164353)

- SERIAL类型 并不是真实的类型
	- 而是一种标记法
		- 为的是明确产生一个自增的唯一标记

- 建立一个SERIAL类型的变量
	- 相当于执行三句话

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685885411838)

- 第一句话就是CREATE SEQUENCE
	- 这如何理解呢？

### 查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685885423089)

- https://www.postgresql.org/docs/16/sql-createsequence.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685885439255)

- 照着第一句话原样执行一下会如何？

```
CREATE SEQUENCE  my_seq AS integer;
```

### 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686054783921)

- 这个序列有什么细节呢？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686054854845)

- 有很多属性
	- 起始值
	- 最小值
	- 最大值
	- 步长
	- 循环
	- 缓存

### 操作序列的函数

- https://www.postgresql.org/docs/16/functions-sequence.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686055517092)

- 序列本质上是单行的表格
	- 一般用来产生唯一标记列的值

- 使用一些方法
	- 可以得到序列的值
- 序列的操作函数
	- nextval
	- setval
	- currval
	- lastval

### nextval

- nextval 就是下一个值

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056049364)

- 每次执行都会将序列这个单行表的记录更新

### 当前值

- currval

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056124677)

- 当前值函数不向后推进
	- 只是得到当前的一个值

### 设置值

- setval

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056248272)

- 可以设置序列的值

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056370408)

### lastval

- 返回最近返回一次的序列值
	- 可以不带序列名

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056459807)

- 以上就是序列的四个方法
	- currval
	- nextval
	- setval
	- lastval

- 其中nextval最为常见

### 列上的序列

- 在heroes表中
	- id字段绑定一个序列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056641201)

- 在items表中
	- id字段绑定另一个序列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056723730)

- 列和字段是如何绑定的呢？


### 绑定过程

- SERIAL关键字	
	- 当我们声明列的数据类型为SERIAL时
	- 做了三件事
		1. 建立序列
		2. 将序列与列绑定
		3. 将序列的所有者设置为列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056821384)

- 每次都要找到nextval
- 如何理解序列呢？

### 序列

- sequence 这个单词来自于*sekw-
	- 意思是跟着的to follow
- 跟着第一个的是第二个
	- second
	- 时间是一秒秒(second)过去的
	- sub 往下 
		- 随后而来的 subsequent
	- con 共同的
		- 一步步最终的结果 consequence
- 结局,后果; 续集;余波 sequel
- 跟着的这一堆人
	- 构成一个团伙 society
	- 构成一个门派 sect
	- 彼此关联 associate
	- 彼此之间要 social
	- 这些人彼此是同类suit	
		- 穿的都是那套衣服

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230115-1673765152074)

- 序列既然可以CREATE
	- 是否可以
		- DROP
		- ALTER呢？
- 是否和DATABASE、TABLE一样
	- 都有增删改三种操作呢？

### 删除序列

- https://www.postgresql.org/docs/16/sql-dropsequence.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686057531686)

- 具体删除

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686057547810)

- 这里确实和DATABASE、TABLE一样
	- 都可以
		- CREATE 新建
		- DROP 删除
- SEQUENCE 是否 可以
	- 通过ALTER进行修改呢?

### 修改序列

- https://www.postgresql.org/docs/16/sql-altersequence.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056917171)

- 具体例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686056957433)

- 重启序列
	- 可以试试吗？

### 重启序列

- 目前有三名武将

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686057168048)

- 尝试重启序列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686057132473)

- 貌似重启序列成功
- 如果再插一名武将会如何呢？

### 插入武将

- 向heroes插入武将成功了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686057383673)

- 但是关羽和赵云的id都是2
	- 这显然和id的定义不符合


## 总结

- 这了解了序列SEQUENCE
	- sequence 就是一个挨着一个的序列
	- 就像过完一秒(second)
		- 就是下一个second (第二个秒)
- SEQUENCE可以有很多自己的参数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686057870514)

- SEQUENCE和DATABASE、TABLE一样
	- 都可以
		- CREATE 新增
		- ALTER 修改
		- DROP 删除
- 但是修改序列之后
	- 可能造成表中的一些错误

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230606-1686057915646)

- 比如关羽赵云id相同
	- id是什么意思呢？
	- 可以相同吗？
- 下次再说？👋🏻