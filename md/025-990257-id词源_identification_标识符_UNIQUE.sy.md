---
show: step
version: 1.0
enable_checker: true
---

# 序列sequence

###  回忆

- 上次了解了序列SEQUENCE
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

### 重新开始

- 观察环境

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686175010181)

### 插入数据

```
INSERT INTO heroes(id,name,fight,intelligence)
VALUES(1,'赵云',96,96);
```

- 插入结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686175140374)

- 数据是成功插入了
- 但是刘备、赵云两个人id相同
- 这不符合id的定义
- 怎么理解id呢？

### identification

- id来自于identification
-  identification
	-  [aɪˌdentɪfɪˈkeɪʃn]
	-  n. 	识别; 鉴定; 辨认; 确定; 
	-  n. 	确认; 身份证明; 
	-  n. 	强烈的同情感（或谅解、支持）; 
	-  n. 	密切关联


![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686181494088)

- 身份验证的🆔
	- 身份证
	- 学生卡
	- 驾驶证

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686181639884)

- identification这个单词来自于什么呢？

### identify

- identify
	- [aɪˈdentɪfaɪ]
	- vt. 	确认一致
		- regard as same
	- vt. 	识别; 鉴定; 确认; 发现; 认出; 
	- vt. 	找到; 显示; 说明身份；
	- 打成一片


![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686181721737)

- 1960-1980年代使用率飙高
- 每个人都有了自己id
	- 做事情需要identify

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686182677822)

- identify来自于什么呢？

### identity

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686182794327)

- identity 
	- [aɪˈdentəti]
	- n. 	身份; 本身; 本体; 特征; 
	- n. 	特有的感觉(或信仰); 同一性; 
		- 比如我们中国人一般都是黑头发黑眼睛
	- n. 	相同; 一致;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686183368887)

- 来自于拉丁语词根idem
	- 指的是相同的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686183512653)

### id总结

- 由同类认同认证开始
	- 今天指 个体验证标记

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686183985353)

- id必须是唯一的吗？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686184082286)

- 怎么表示唯一这个事情呢？

### unique

- CREATE TABLE的时候
	- 可以设定 列为UNIQUE 的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686184734160)

- 如何理解UNIQUE呢？


### unique

- unique 
	- [juˈniːk]
	- adj. 	唯一的; 独一无二的; 独特的; 

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686184586613)

- 不能重样的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686184934644)

- 类似的单词还有什么呢？

### unique词源

- uni- 和 one 都是一个词根

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686189404517)

- unique 词源也是 一
- 可以将列设置为UNIQUE
	- 这一列里面的东西必须不同

### 现状

- 现在已经有表了
	- 而且表里面已经有数据了
	- 怎么办呢？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686200921263)

- 查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686200942162)

### 修改表中的列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686200965470)

- 修改表ALTER TABLE 
	- 修改列 ALTER COLUMN

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686201005088)

- 给列添加一个UNIQUE约束
- 具体怎么做呢？

### 网页查找

- https://www.postgresql.org/docs/16/sql-altertable.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686201669099)

- 照猫画虎去做一下

### 更新列

- 尝试给id列添加unique约束

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686278976208)

- 但是失败了
	- 这怎么办呢？

## 总结

- 这次了解了id的来源
	- id 就是identification
		- 是一种唯一性的标识
- 需要给id列添加约束(Constraint)
	- 唯一性约束 UNIQUE
- 但是在添加约束的过程中报了错


![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686278976208)

- 这怎么办呢？🤔
- 下次再说？👋🏻