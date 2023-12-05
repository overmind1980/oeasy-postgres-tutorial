---
show: step
version: 1.0
enable_checker: true
---

# 行业分析

## 选型

- 这次我们要学习数据库
  - 什么是数据库？
- 数据库就是数据的大宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650102264659)

- 都有什么宝库呢？

### 宝库的排名

- 有个数据库排名网站
	- http://db-engines.com

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650102596740)

### 趋势图trends

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650102855802)

- 前三名一路纠缠了好久
  - 分别去看看去看看他们的网站

### 第三名 sql server

- microsoft sqlserver

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650103310741)

- 自称是业界领先的性能和安全性
  - 微软公司的数据库产品

### 第二名 mysql

- mysql

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650103117358)

- mysql自称是
	- 世界上最流行的开源数据库
	- 论流行确实比较流行的
	- 曾经是最红的流量担当
- mysql为什么当时能够得到开源社区的支持呢？

### 分支

- mysql开始的时候使用GPL协议
- 什么是GPL协议呢？
  - GPL需要开放源代码
	  - 并且可以免费下载使用分发
	  - 可以修改
  - 修改之后也要遵守GPL协议公开并允许修改
	  - 软件的子子孙孙都要遵循GPL
  - 这就是所谓的传染性
- GPL强迫大家把对软件做的改进回馈给社区
  - 让软件更好的延续下去
  - 只要遵守GPL
  - 这样大家好共同进步

### 渊源

- mysql最早是monty创造的开源数据库
  - 正好赶上动态网页大爆发
  - LAMP 成为主流框架
    - Linux
    - Apache
    - Mysql
    - Php
- 行业的大发展造成了正反馈
  - 大量的从业人员也导致大量的源代码维护需求
  - 大量的维护需求岗位导致培训的倾斜
  - 大量的培训倾斜导致公司选型的时候找这类开发人员更容易

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650370930040)

- 正当mysql发展得如火如荼之时
  - 一份收购合同发在了monty眼前

### 10亿美金

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650106255004)

- 2008年
  - sun公司将向mysql支付8亿美元现金和价值2亿美元的期权
  - mysql总部当时位于瑞典
  - 在全球25个国家共有约400名员工
- monty带领mysql接受了sun的合同
  - mysql首席执行官马顿·尼科斯(Marten Mickos)将加盟sun管理层
  - monty也将成为首席技术官
- 不过更诡异的事情在一年之后发生

### 收购的嵌套

- 一年之后，2009年
  - oracle收购了sun
  - 最大的商业数据库收购了最大的开源数据库厂牌拥有者
  - 第一名吞并了第二名

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650106904917)

- 商业数据库oracle吞并了开源数据库mysql
  - 听起来有够诡异
  - 但是真实发生了
- oracle 是什么公司呢？


### oracle

- 看看网站上oracle是如何介绍自己的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650102873089)

- 世界上最流行和最先进的数据管理技术
  - 每天都被开发者所信任
  - oracle确实是世界上最大的商业软件数据库软件公司
- 收购之后mysql的命运如何呢？

### 收购之后

- oracle和mysql各有定位：
  - oracle有自己的一套商业的数据库应用
    - 那是他继续收购的财源
    - 是不可能免费的
  - mysql 当时是最流行的数据库
    - 可以让oracle某种程度抵御开源数据库的威胁
    - 毕竟说起来最大的开源数据库都是oracle的
    - 本身就是强化了oracle在数据库上的这个标签
      - 仿佛oracle数据库是最好的
      - 开源和商业的第一都是他家的
      - 这让他在传统的数据库领域显得更权威
      - 毕竟银行、军工之类的还是相对保守的
        - 这也就更保住了oracle的财源
    - 而且mysql广泛的用户基础
      - 也成为oracle云的一块拉客招牌
    - mysql代码还需要维护和优化
- 这种大背景导致了oracle对于mysql的态度

### 态度

- mysql这个曾经最流行开源数据库有两个任务
    - 一方面用开源`免费优势`压制其他的商业数据库
      - 比如微软、IBM的生存空间
    - 另一方面用`流量优势`压制住其他开源数据库
      - 比如postgres的生存空间
  - 但永远不能比oracle自家的核心产品更出风头
- 所以mysql发展空间有限
  - 只能是个伴读书童
  - 只能是oracle家数据库方面的棋子
- 数据库领域开源的革命别想依赖mysql
  - 否则就永远只是个梦
- oracle的这种态度
  - 也就导致了开发人员离职时候的抱怨
  - 毕竟自媒体时代每个人都是信息源
- 我们听听内部人士的爆料

### 爆料

- 这位是oracle公司内部的大牛

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650104131772)

- 在公司内部和外部连续五年都说了这样的话
  - mysql是很差劲的
  - 还是用postgres替代吧！
  - 同时maria-db也是不行的
- 自媒体时代每个员工都是可以发声的
- oracle面对这样的离职员工会如何处理呢？

### 无视

- oracle官方拒绝评论

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650332951265)

- 其他人怎么说呢？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650332957610)

- MariaDB 的联合创始人说
  - 这是很正常数据库行业中人员流动
- 这MariaDB好像也被批评了
- MariaDB什么来头？

### MariaDB

- MariaDB目前排名12

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650105760336)

- 这两个logo很像呢？！
- 有没有什么渊源呢？

### mariaDB 和 mysql

- 开源社区和创始人对于oracle这样的商业公司并不信任
  - 于是创始人又重做了mariadb
  - mariadb是mysql的一个分支
  - 主要由开源社区在维护
  - 采用GPL授权许可
  - 想重新开始
  - 还想再借助开源社区的力量
- 由于mysql最早是GPL协议的
  - 最初获得了开源领域的巨大支持
  - 所以oracle对于mariadb也没有办法
  - 因为GPL协议的存在
  - 上了法庭oracle理亏
  - 这也为mysql创始人monty后来离开oracle奠定了基础
- 我们再回来看看发展趋势

### 发展趋势

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221209-1670577094921)


- 第四名postgresql奋起直追
- 我们去看看postgresql


### postgresql

- postgres其实历史特别悠久
	- 比mysql、oracle还要悠久
	- 是引领着数据库技术一路进化到今天的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650103461991)

- 世界上最先进的开源数据库
  - postgres是开放源代码的
    - 和mysql一样都是开源的
  - 敢自称是最先进的(the most advanced)
  - 对比mysql(the most popular)
- postgresql和mysql都是开源的
- postgres用的是什么协议呢？
- 我们看看都有什么协议

### 协议选项
- 好多呀

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650346014709)

- postgres的协议有点类似于bsd协议

### BSD

- BSD 协议

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650148345328)

- 他和GPL的最大区别是他人是否以后可以闭源
  - GPL必须开源
  - BSD可以闭源
- 闭源之后有什么好处呢？

### 孵化

- 开源和商业
	- 并不是非黑即白的
- 因为下游闭源后
	- 可以进行商业化
- 所以 孵化了 大量商业数据库产品
  - 催生了 各种形态的数据库创新
  - 培养了大量的 Pg 内核研发人才

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650148465998)

- 这样可以反哺
	- 上游的postgres

- 这其中就包括
  - 亚马逊redshift
  - 国产昆仑和高斯

### 国产情况

- 观察国产情况

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650149122608)

- 国产数据库在发展中
  - 有开源也有闭源
  - OceanBase、TiDB、MemFireDB
	- 都是站在postgres这个巨人的肩膀上逐渐发展而来的
- 我们选用哪个呢？

### postgres

- 选比较通用的！！！
	- 经典数据库postgres数据库
		- 包含存储、事务、SQL 这几个核心引擎
		- 以及基于这些核心引擎之上的数据库功能
		- 性能、成本、安全、可靠等企业级特性
- 其实所有的数据库
  - 本质上都相同
  - 细节上有区别
- 我们学了原理后熟悉掌握postgres
  - 基本上其他的也都基本掌握

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
