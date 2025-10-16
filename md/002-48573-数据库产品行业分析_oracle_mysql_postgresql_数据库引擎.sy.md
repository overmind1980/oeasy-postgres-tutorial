---
show: step
version: 1.0
enable_checker: true
---

# 行业分析

## 选型

- 上次了解了 数据库的排行
	- 分析了 前3名
	  1. oracle
	  2. mysql
	  3. ms-sqlserver
	- 第1名 吞并了 第2名

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/4266995/uid1190679-20251013-1760335947701) 

- 数据库 格局 会 如何变化 呢？🤔

### 收购之后

- oracle和mysql各有定位：
  - oracle 
	- 商业数据库
    - 公司现金来源
    - 不可能免费
  - mysql 
	- 是 最流行的数据库
	- 让oracle 抵御开源的威胁

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240415-1713189972886)

- 公关话术
	- 最大的 商业/开源 数据库 
		- 都是 oracle的
	- 本身就是强化了
		- oracle数据库
	- 仿佛oracle数据库 是 最好的

### oracle进化过程

- oracle 在传统数据库领域 显得更权威
  - 毕竟 银行、军工之类的业务 选型相对保守的
  - 这就 保住了oracle的 财源

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250714-1752471433085) 

- 而mysql广泛的用户基础
    - 也成为 oracle云的 一块 拉客招牌
- 这种大背景
	- 导致了oracle对于mysql的态度

### 态度

- mysql 这个 最流行开源数据库 有两个任务
    1. 用开源`免费优势` 压制 其他商业数据库 报价
      - 比如微软、IBM
    2. 用`流量优势` 压制 其他开源数据库 用户数
      - 比如postgres

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250714-1752471981768) 

- 但前提是 
	- mysql `永远` 不能 比oracle 更出风头

### 位置

- 所以 mysql 发展空间有限
  - oracle家的
	- 棋子
    - 护城河
    - 伴读书童

- 数据库领域的 开源革命
	- 别想依赖mysql
- 否则 就永远只是个梦

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240415-1713190198979)

- 那个bug后来如何呢？

### bug

- 2005年 提出
	- 9天后 承诺修改
	- 8年后 依然没有人管

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754356968844) 

- 10年后 有人开始给这个bug过生日

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754357018391) 

- oracle的态度
  - 也就导致了 开源开发人员
  - 离职时的抱怨

### 爆料

- 自媒体时代
	- 人人 都是 信息源
	- oracle公司内部的 大牛爆料

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650104131772)

- 在 公司内部和外部 连续五年
	- 都说了 这样的话

> mysql是很差劲的

> 还是用postgres替代吧！

>  同时maria-db也是不行的

- oracle面对这样的离职员工会如何处理呢？

### 无视

- oracle官方拒绝评论

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650332951265)

- 其他人怎么说呢？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650332957610)

- MariaDB 的联合创始人 说

> 这是很正常数据库行业中人员流动

- 这MariaDB 
	- 好像 也刚被批 了	
	- MariaDB 什么来头？？

### MariaDB

- MariaDB目前排名13
	- https://mariadb.com/

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20240415-1713190465210) 

- 这两个logo 很像！
	- 有没有 什么渊源 呢？

### mariaDB 和 mysql

- 开源社区和创始人 对oracle 这样的商业公司 并不信任
  - 于是创始人 根据gpl
  - 做出了 新分支mariadb
  - 想重新开始
  - 继续 借助 开源社区的力量

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650105760336)

- 由于 mysql最早 是GPL协议 的
  - 所以 oracle 对mariadb 也没有办法
  - 因为协议的存在
  - 上了法庭 oracle理亏
- mysql创始人monty
	- 后来离开oracle
	- 再次创业

### mariaDB评价

- 当年的bug依然没有修复
	- 并且 还有人过来朝圣

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754357203066) 

- 有些东西 从根子上 就不太行
	- 还是 看看`别`的吧

### 发展趋势

- 回来再看看发展趋势

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221209-1670577094921)

- 第四名postgresql奋起直追

### postgresql

- postgres其实历史特别悠久
	- 比mysql、oracle还要悠久
	- 引领着 数据库技术 一路进化到今天的
	- https://www.postgresql.org/

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650103461991)

- 自我介绍 
	- 世界上最先进 的开源数据库
  - postgres是开放源代码的
    - 和mysql一样都是开源的
  - 敢自称是最先进的(the most advanced)
	- 对比mysql(the most popular)
- postgresql 和 mysql 都是开源的
	- postgres 用的 什么开源协议 呢？

- 我们先看看都有什么协议

### 协议选项

- 好多呀

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650346014709)

- postgres用的是 bsd协议

### BSD

- BSD 协议

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650148345328)

- 他和GPL的最大区别是他人是否以后可以闭源
  - GPL必须开源
  - BSD可以闭源
- 允许闭源之后有什么好处呢？

### 孵化

- 开源 和 商业
	- 并不是 非黑即白的
- 因为 下游闭源后
	- 可以 进行商业化
- 所以 孵化了 大量商业数据库产品
  - 催生了 各种形态的数据库创新
  - 培养了大量的 Pg 内核研发人才

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650148465998)

- 这样可以反哺
	- 上游的postgres

- 这其中就包括
  - 亚马逊redshift
  - 国产昆仑
  - 华为高斯

### 国产情况

- 国产数据库在发展中
  - 有开源也有闭源
  - 都站在postgres这个巨人的肩膀上 发展而来的
	- OceanBase
	- TiDB
	- MemFireDB

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650149122608)

- 我们选用哪个呢？

### postgres

- 选比较通用的！！！
	- 经典数据库postgres数据库
		- 包含存储、事务、SQL 这几个核心引擎
		- 以及基于这些核心引擎之上的数据库功能
		- 性能、成本、安全、可靠等企业级特性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240415-1713191345996)

- 其实所有的 数据库
  - 大同小异
  - 尤其是华为高斯
  - 很多操作类似于pg

## 总结

- 我们了解了数据库的排行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230907-1694093715005)

- 分析了前三名
  - oracle
  - mysql
  - mssql server
- 最后选用的是
	- postgres

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221209-1670579455827)

- 这个postgres到底怎么安装呢？🤔
- 下次再说 👋

