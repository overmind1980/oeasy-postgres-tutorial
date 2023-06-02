---
show: step
version: 1.0
enable_checker: true
---

# 投影运算

### 回忆

- 上次找到了适合我们的工作流程
  - 进psql
  - \e 编辑sql文件
  - :!psql -f % 执行当前sql批处理命令
- 数据库的备份还原
  - pg_dump oeasydb > oeasydb.sql 备份
  - psql oeasydb < oeasydb.sql 还原
- 数据导入导出
  - COPY TO 是导出
  - COPY FROM 是导入
- 我们还没有建立起一个有意义的数据库

### 建立基础

```
sudo -u postgres psql -c "CREATE DATABASE sanguo;"
sudo -u postgres psql sanguo -c "CREATE TABLE heroes(id serial, name VARCHAR(20),fight int,intelligence int);"
sudo -u postgres psql sanguo -c "INSERT INTO heroes(name, fight, intelligence) VALUES('刘备',60,65),('关羽',96,96),('张飞',98,60);"
```

### 观察效果

- 进入库中

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230302-1677767010441)

- 确实可以看到武将所有信息的列表
	- 如果我只想看
		- 武将名称的列表呢？

### 武将名称

- 只SELECT name
	- 就可以只要武将名称这一列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677809123962)

- 这个过程叫什么呢？

### projection 投影
- 就像光给物体描一个阴影一样

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650166097158)

- project不是项目吗？
- 为什么projection是投影呢？

### *per

- 象声词
	- 来自于投掷
	- 往前面扔

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221221-1671629678882)

### pro

- pro-词根
	- prohibit = pro + forbid 事先禁止
	- provide = pro + view 事先看过
	- promise = pro + mission 事前承诺使命
	- promote 促进
	- profit 利润
	- process 步骤、进展
		- 在计算机中
			- process也指进程
			- 占内存里面的一段空间

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230201-1675249103597)

- pro 和 fore 
	- 都是指向前

### project

- project 项目

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677810515514)

- 向前 逐个执行计划目标
	- 最终 完成整个 project

### projection

- 光向前投射到物体上
	- 把三维物体 映射到了一个二维平面
		- 降维了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677811154194)

- 投影运算的结果
	- 是原始数据数据的子集
		- 只有一列的剪影效果而已
- 可以对其他列进行投影吗？

### 更多投影

- 要哪列
	- 就 SELECT 那一列的列名

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677809986044)

- 投影
	- 具体是 怎么定义的呢？

### 投影

- 投影
	- 是一种关系运算 
- 投影的结果
	- 是关系的子集

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650166146041)

- 上图中
	- Harry 和 Peter
	- 被投到一起了吗？
- 去构造一个例子

### 构造环境

- 如下图更新张飞的智力值

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677809589492)

- 然后尝试对智力投影

### 智力
- 结果对于列
	- 做出了筛选

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677809682517)


- 但是并没有
	- 去除重复
- 去看看定义

### 反观定义

- 从关系R中选择若干属性
	- 组成新的关系
- πA1,A2,…,An(R)
	- 表示从R中选择属性集A1,A2,…,An组成新的关系
- 投影运算的结果中
	- 要去除可能的重复元组
- 直接给列名
	- 没有去除重复的功能

## 总结

- 这次研究了投影

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677811840916)

- 数据库中的投影指的是
	- 使用SELECT将表中的列
	- 投射出来

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230303-1677809682517)

- 但是没有去除重复的行
- 如何去重呢？🤔
- 下次试试？👋🏻