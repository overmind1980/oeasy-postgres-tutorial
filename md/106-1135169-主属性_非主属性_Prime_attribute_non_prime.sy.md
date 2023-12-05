---
show: step
version: 1.0
enable_checker: true
---

#   超键_候选键_主键_key      
 
##  回忆

- 上次研究了候选键
	- candidate key
- 候选键 
	- 被选择 成为主键
		- Primary Key
	- 没被选择 成为候选键 Alternative Key
- 候选键的超集 是不是 候选键呢？

### 候选键的超集 

- 候选键的超集
	- 叫做 超键

- 候选键属于超键
	- 是最小的超键

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695871968141)

- 候选键
	- 如果再去掉候选键中的任何一个属性
	- 就不再是超键了
	- 这样的超键 就是 候选键

- 候选键 有什么用呢？

### 2NF

- 候选键 是2NF定义当中的一个关键属性
	- 如下图红框中 所示

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695872443909)

- 上图紫框中 的
	- 非主属性是什么意思呢？

### 主属性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695872252672)

- 在一个关系中
	- 如果一个属性是
		- 构成某一个候选键中的一个属性
	- 则称它为主属性（Prime attribute）

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695872311450)

### 非主属性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695885435799)

- 所谓非主属性
	- 就是 不在任何候选键 中的属性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695885413019)

### 2NF

- 2NF 有两个条件
	1. 首先得是第一范式
	2. 不能有非主属性 函数依赖于 任何候选键的子集

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695527116407)

- 我们具体来看一下 美食城

### 美食城

- 候选键
	- {ic_id,dk_id,deal_time}
- 主属性
	- ic_id
	- dk_id
	- deal_time
- 非主属性
	- price
	- shop
	- shop_owner

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230924-1695526535688)

- 非主属性{shop,show_owner}
	- 函数依赖于
		- 候选键{ic_id,dk_id,deal_time}中的{dk_id}
- 于是不满足2NF

### 拆表

- 拆出来的两个表
	- stall
	- bill

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230906-1694008210314)

### stall表

- stall表
	- 候选键 {dk_id}
	- 主属性 dk_id
	- 非主属性 shop,shop_owner

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695886024268)

- 不存在非主属性 
	- 依赖于 候选键中的一部分
- 符合2NF

### bill表

- bill表
	- 候选键 {dk_id,ic_id,deal_time}
	- 主属性 dk_id,ic_id,deal_time
	- 非主属性 price

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695886080626)

- 不存在非主属性 
	- 依赖于 候选键中的一部分
- 符合2NF
- 经过拆表之后
	- 现在的数据库关系符合2NF

##  总结

- 这次了解了
	- 主属性
		- 任何候选键中的属性
	- 非主属性
		- 不在任何候选键中的属性
- 2NF 有两个条件
	1. 首先得是第一范式
	2. 不能有非主属性 函数依赖于 任何候选键的子集
- 美食城 拆表得到的两个表
	- 符合了2NF的定义
	- 这两个表之间有什么关系吗？🤔
- 下次再说？👋

