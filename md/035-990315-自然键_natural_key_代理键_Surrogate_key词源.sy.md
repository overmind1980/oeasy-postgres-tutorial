---
show: step
version: 1.0
enable_checker: true
---

# 自然键_natural_key_代理键_Surrogate

###  回忆
- 上次我们分析了姓名
	- 各种姓名的来历
	- 非常有趣
- 名字是否能做主键Primary Key？
	- 结论是不能做
	- 因为名字不满足唯一性约束
- 主键约束要求
	1. 唯一性约束
	2. 非空约束
- 一般我们都会给这个表格添加一个额外的列 
	- id
- 如何理解这个额外的列呢？

### 武将的属性

- 武将有三个属性
	- 姓名
	- 武力
	- 智力
- 这三列 `都`不能当Primary Key
	- 因为都不具有唯一性约束 
		- UNIQUE CONSTRAINT
- 这三列 的 组合 也不能 做 Primary Key
	- 因为可能有两个武将
		- 同名同姓 能力相同

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687348003564)

- 那怎么办？

### 唯一标记

- 需要有一个唯一的标记
	- 比如身份证
 
![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687347768752/wm)

- 但是 各国数据不互通
	- 所以只能在数据库中人为地添加一个唯一性的字段
		- id

### id 字段

- id 词源来自于 identification

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686189404517)

- id 的唯一性来自于 SERIAL 类型

### SERIAL类型

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685882881510)

- SERIAL 类型实现原理是
	- 构建了一个自增的序列
		- SEQUENCE

### SEQUENCE

- 序列就是一个挨着一个的
	- 第二秒很快就来

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230115-1673765152074)

- 序列中的东西彼此关联
	- 形成社会
- 每次都找下一个
	- 会形成唯一性约束
		- UNIQUE CONSTRAINT

### id属性

- id属性 
	- 来自于序列的下一个值
		- 如果不考虑溢出的情况
		- 应该是唯一的
		- 满足了 UNIQUE CONSTRAINT
		- 也应该满足了 非空约束
			- NOT NULL CONSTRAINT

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230620-1687259778171)

- 所以id可以作为主键
	- 也可以作为候选键

### 代理键 Surrogate Key

- id 属性并不来自于 真实系统中
	- 而是 我们在数据库中 认为创造的一个 主键

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687356730538)

- Surrogate Key
	-  [ˈsʌrəɡət]
	-  n. 	代理; 代孕者; 代表; 
	-  adj. 	替代的; 代用的;
	-  v. 	代理；代替
-  代理键
	- 系统生成的一个Key
	- 现实世界没有的
	- 与自然键不同

### 自然键 Natural Key

- 自然键
	- Natural Key
	- 也叫business key
		- 是已经存在于现实世界中的域

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687356926262)

- 在关系数据模型中
	- 一个自然键是一个候选键
	- 可以决定一切其他属性
	- 也被称作域键
		- Domain Key
- 现实中有什么自然键吗？

### 自然键

- 随着生活中 数字化程度 越来越高
	- 唯一性的标识符非常重要

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687357444942)

- 很多地方都有自然键 

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687357472811)

- 我们学了好多种Key

### 总结Key

- 按照是否显示系统中存在
	- 自然键 Natural Key
		- 也叫business key
	- 代理键 Surrogate Key
- 按照是否是表中决定因素
	- 主键 Primary Key
	- 可选键 Alternative Key

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687357663662)

- 那么究竟什么是Key呢？

### Key

- Key 是开锁的一种金属装置

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687357731354)

- 由于Key可以开锁
	- 所以Key是一种能解决问题的关键因素

### key的词组

- Key Point
	- 关键点
- Key Note
	- 基调
- Key Frame
	- 关键帧

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230621-1687358290425)

- Key Person
	- 关键人物
- Key Board
	- 键盘

## 总结
- 这次讲了键Key
	- 从是否是表中最主要字段或字段组来区分
		- 主键 Primary Key
		- 可选键 Alternative Key
	- 从是否是现实世界中已有字段来区分
		- 自然键 Natural Key
			- 也叫business key	
		- 代理键 Surrogate Key
- 最开始的时候是没有数据库系统的
	- 也就肯定没有代理键
	- 什么时候有代理键的呢？🤔
- 下次再说？👋🏻