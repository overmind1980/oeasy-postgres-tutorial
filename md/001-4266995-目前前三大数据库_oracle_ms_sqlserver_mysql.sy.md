---
show: step
version: 1.0
enable_checker: true
---

# 行业分析

## 选型

- 这次我们要学习数据库
  - 什么是数据库？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650102264659)

- 数据库就是数据的大宝库
	- 都有什么宝库呢？

### 宝库的排名

- 数据库 也有 排名
	- http://db-engines.com

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240409-1712638468646)

### 趋势图trends

- https://db-engines.com/en/ranking_trend

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240409-1712638562221)

- 前三名 一路纠缠
  - 分别 去看看 

### 第三名 sql server

- microsoft sqlserver
	- https://www.microsoft.com/en-us/sql-server/

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20240415-1713189047729) 

- 微软公司 的 数据库
	- 结合 微软的 云服务
	- 提供 现代数据平台

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250714-1752468743340) 

- ai时代 
	- 主动迎合

### 第二名 mysql

- mysql
	- https://www.mysql.com/

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650103117358)

- mysql 自称是
	- 世界上 `最流行`的 开源数据库
	- 流量担当
- mysql 为什么
	- 当时 能成为 流量明星呢？

### 渊源

- 最早
	- mysql是monty创造的开源数据库
    - 正好赶上动态网页大爆发

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250714-1752470849721) 

- LAMP 成为主流框架
    - Linux
    - Apache
    - Mysql
    - Php

- mysql 为什么能够得到
	- 开源社区的 支持呢？

### 分支
- 开始的时候
	- 使用GPL协议进行开源

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240415-1713189402184)

- 什么是GPL协议呢？

### GPL

- GPL需要开放源代码
  - 并且可以免费下载使用分发
  - 可以修改

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/4266995/uid1190679-20251013-1760360993040) 


- 修改之后也要遵守GPL协议公开并允许修改
  - 软件的子子孙孙都要遵循GPL
  - 这就是所谓的传染性

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/4266995/uid1190679-20251013-1760361041544) 

- GPL强迫大家把对软件做的改进回馈给社区
  - 让软件更好的延续下去
  - 只要遵守GPL
  - 这样大家好共同进步

### 正反馈

- 行业的大发展造成了正反馈
  - 大量的从业人员也导致
	- 大量的源代码维护需求
- 大量的维护需求岗位导致
	- 培训的倾斜
- 大量的培训倾斜导致
	- 公司选型的时候
	- 找这类开发人员更容易

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650370930040)

- 我们回到那个年代
	- 看看细节

### 错误

- MySQL官方的 bug追踪系统中 编号为11472的bug页面
	-  于2005年6月21日提交
	- 涉及的MySQL版本有5.0.8/5.5/5.6/5.7
	- 严重等级为S2（严重）。从图片中下方的评论可以看到
	-  外键更新/删除后触发器未执行
	-  https://bugs.mysql.com/bug.php?id=11472

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754356360273) 

- mysql团队面对这个问题 
	- 是如何处理的呢？

### 立即反馈

- 9天后 
	- 说一定要修复这个

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754356505596) 

- 结果如何呢？

### 结果

- 5年后
	- 错误依然还是没修复

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754356583382) 

### 7年过去

- 有人 转到了postgres数据库
	- 注意 一个mysql 有7年经验的人
	- 迁移到了 postgres

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754356745532) 

- 8年之后
	- 没有任何进展

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/48573/uid1190679-20250805-1754356889845) 

- mysql 团队在干啥呢？

### 10亿美金

- 正当mysql发展得
	- 如火如荼之时
    - 一份收购合同发在了monty眼前
- 2008年
  - sun公司将向mysql
  - 支付8亿美元现金
  - 和价值2亿美元的期权
- 当时 mysql总部位于瑞典
  - 在全球25个国家
  - 共有约400名员工

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650106255004)

- monty带领mysql
	- 接受了sun的合同
- mysql首席执行官马顿·尼科斯(Marten Mickos)
	- 将加盟sun管理层
    - monty也将成为首席技术官
- 不过更诡异的事情
	- 在一年之后发生

### 收购的嵌套

- 一年之后，2009年
  - oracle收购了sun
  - 最大的商业数据库
	- 收购了最大的开源数据库厂牌
  - 第一名吞并了第二名

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/4266995/uid1190679-20251013-1760361317910) 

- 商业数据库oracle
	- 吞并了开源数据库mysql
	- 听起来有够诡异
	- 但是真实发生了
- oracle 是什么公司呢？

### oracle

- 看看网站上oracle
	- 是如何介绍自己的
	- https://www.oracle.com/database/
		- 世界上最流行和最先进的数据管理技术
		- 每天都被开发者所信

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650102873089)

- oracle确实是
	- 世界上最大的商业软件数据库软件公司
- 收购之后
	- mysql的命运如何呢？

## 总结

- 我们了解了 数据库的排行
	- 分析了 前3名
	  1. oracle
	  2. mysql
	  3. ms-sqlserver
	- 第1名 吞并了 第2名

![图片描述](https://doc.shiyanlou.com/courses/2782/labs/4266995/uid1190679-20251013-1760361607118) 

- 数据库 格局 会 如何变化 呢？🤔
- 下次再说 👋

