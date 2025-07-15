---
show: step
version: 1.0
enable_checker: true
---

#  分分合合_拆表_合表_减少冗余_表格连接     
 
##  回忆

- 上次把拆开的了两个表 
	- 换源成了一个表
	- 可以说是 完全还原
	- 一模一样
	- 仿佛没有拆过一样
- 既然如此
	- 为什么又要拆表呢？

### 1NF
- 先回忆第一范式

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527097210)

- 完整定义

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527116407)

### 1NF概括

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527138510)

- 一列就是一个原子数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230901-1693566271368)

- 不能有两个宝物
	- 赤兔马、青龙偃月刀

### 2NF

- 2NF 有两个条件
	1. 首先得是第一范式
	2. 不能有非主属性 函数依赖于 任何候选键的子集

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527347889)

- 什么是 函数依赖 呢？

### 函数依赖

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527547146)

- 函数依赖
	- functional dependency

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527640816)

### 举例

- 在原始表中
	- dk_id 能够 决定
		- shop
		- shop_owner

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695526535688)

- shop、shop_owner 
	- 函数依赖于 dk_id

> shop and shop_owner		
>> are functional depend on dk_id

##  总结🤔

- 这次了解到了2NF的定义

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527347889)

- 还了解了函数依赖关系

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687432218520)

- 在 宝物表中
	- 有什么函数依赖关系吗？
- 下次再说？👋

