---
show: step
version: 1.0
enable_checker: true
---

# 投影运算

### 回忆

- 上次了解了distinct的词源

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685857257677)

- DISTINCT
	- 在SQL语句中的意思就是去重
- 如果DISTINCT之后接两个字段
	- 会如何呢？🤔

### 两个字段去重

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685845764012)

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685845779773)

- 如果只让其中一个字段去重
	- 但是投影两个字段
		- 应该如何呢？

### 查询文档

- https://www.postgresql.org/docs/16/sql-select.html#SQL-DISTINCT

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685858573067)

- 其他投影列
	- 好像只返回第一行

### 具体代码

- 去重字段为city
	- 投影字段为effects

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685858857365)

- 只取每个去重字段中的第一条记录
- 可以再增加投影字段吗？

### 增加投影字段

- 增加投影字段
	- 价值

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685858939815)

- 新增的投影字段价值
	- 也是只取第一行

- 如果换一个去重字段呢？

### 更换去重字段

- 将去重字段更换为
	- value

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685859077369)

- 去重字段是不会重复的
	- 投影字段是选择第一行记录
	- 投影字段中是可以有重复的

- 投影字段顺序可以修改吗？

### 修改投影字段顺序

- 修改投影字段展示次序

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685859249252)

- 展示记录不受影响

### 回忆数据表

- 宝物表中

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685845109548)

- 只有一列没有重复
	- 这一列的名字叫做id
	- id可以重复吗？

## 总结

- 我们这次了解了
	- 去重字段
	- 投影字段
- 去重字段
	- 不能重复
	- 投影字段选取其中的第一列
- 发现items表中
	- 只有一列没有重复
	- 为什么没有重复呢？🤔
- 下次试试？👋🏻