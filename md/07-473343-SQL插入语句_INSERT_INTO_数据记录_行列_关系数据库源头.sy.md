---
show: step
version: 1.0
enable_checker: true
---

# 插入数据记录INSERT

## 回忆

- SELECT 是查询命令
  - 可以计算 2+2
  - 可以查询版本号
  - 还可以查询有哪些表
    - SELECT \* FROM pg_tables;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650456766122)

- 但是新建的 login 表中
  - 没有数据
- 就像
  - 数据宝库的宝箱里面没有宝贝一样
- 如何把宝贝放到格子里？🤔
- 或者说把数据插到表里面？🤔

### 查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650457248213)

- INSERT 命令应该是
	- 向表中插入数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650179572150)

### 例子

- <kbd>G</kbd>
	- 翻到最后去找例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458492948)

- 去网页搜索个例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458520999)

- 这个看起来能用！

### 插入数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458710515)

- 真的插入成功了么？
- 我去问问数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458755299)

- 真的出来了！！！
- 对比一下帮助手册中的语句

### 查询帮助

- 红色的部分
  - INSERT INTO login
  - 是基本的结构
- 黄色的部分是
  - (username,password)
  - 是表的描述
  - 在中括号中
  - 是可省略的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458978937)

- 绿色的部分
    - VALUES('oeasy','123')
- 大括号里面用|分隔开
    - |之间是或者的选择关系
  - 我们选的是后面的VALUES
    - expression 是 'oeasy'
    - 然后有个中括号里面的逗号
    - 逗号后面跟另一个expression
      - '123'
  - 合在一起就是
    - 是插入的具体内容
    - VALUES('oeasy','123')

- 我们试试省略表结构

### 省略

- 将表结构中的列名省略

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650459421362)

- 依然可以插入数据
	- 果然表结构是可省略的
- 但是可能会有什么问题么？

### 列序

- 如果不明确指定列名
	- 可能插错位置

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220425-1650844586843)

- 绿框中的就是插错位置了
	- 驴唇不对马嘴
	- 最好还是把列元组写清楚
- 列的顺序必须按照建表时候的顺序么？

### 插入

- 插入时列的次序是不固定的
	- 但只要对应好就可以

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650459800030)

- 现在数据库postgres的login表中有4行了
- 这4行其实来自于数据库基本理论

### 理论来源

- 1970年的一篇文档

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650180801566)

- 题目是
  - 《大规模分享的数据银行的关系模型》
- 作者是谁呢？

### 祖师

- IBM的工程师艾加德.柯德
	- E.F. Codd

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650180941243)

- 他提出了关系模型

### 关系模型之前

- 原来的数据库都是层次结构的
	- 就像今天的文件系统结构一样
	- 最初的存储介质是卡片和柜子
	- 一个员工一个盒子
		- 里面存着档案和工资记录之类的东西

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181030487)

- 这种层次结构被引用到了计算机之中

### 层次结构发展

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220418-1650292227620)

- 从文件夹型的层次结构

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220418-1650292246063)

- 利用软连接之类的方式构成了
	- 比较复杂的网状关系
- Codd把他简化成关系表结构
	- 那什么是关系(relation)表结构呢？

### 二维关系表

- 关系(relation)表结构就是二维表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181142426)

- 这二维指的是哪二维呢？

### 关系模型

- 关系指的是什么的关系？
  - 行和列构成的
  - 一个关系(relation)

- 横着的
  - 叫行(row)
  - 元组(tuple)
  - 记录(record)

- 竖着
  - 叫列(column)
  - 领域(field)
  - 属性(attribute)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181704214)

- 这篇1970年的文章
	- 开始使用attribute作为数据的术语(term)
- attribute指的是什么呢？

### attribute 属性 字段

- login有两个字段

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181441489)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181455100)

- 我们建表时候的列名
- 就是属性(attribute)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181526769)

- attribute 这个词是怎么来的呢？

### 词源

- tribe
	- 部落

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181862293)

- tribe最早指的是罗马的三个部落

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181871310)

- tribute指的是部落的保护费

### tribute

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181879086)

- contribute指的是做出贡献

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181888063)

- distribute指的是对贡品进行分发
- 分配贡品

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181894650)

- retribute指的是返还的礼物
- 那attribute怎么来的？

### attribute

- 动词[əˈtrɪbjuːt]是归因

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181901593)

- 名词[ˈætrɪbjuːt]是属性
- 登录表(login)有两个属性(attributes)
  - username
  - password
- 那最初的文章如何称呼行呢？

### tuple

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650182694931)

- tuple就是行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650182732560)

- 元组是由属性构成的
	- 一个n元组对应着一行
	- 也叫做一条记录(record)

### record

- 下表中共有
  - 3行数据(rows)
  - 3条记录(records)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650182779884)

- 每行数据
  - 都是一个2元组(2-tuple)
  - 包括
	  - 2个域(fields)
	  - 或者说2个列(columns)
	  - 或者说2个属性(attributes)

### 总结

- 这次我们往登录(login)表里面插了数据
- 所谓表(table)
  - 是一个关系(relation)
	  - 是行和列的关系
  - 行也叫row、tuple、record
  - 列也叫column、attribute、field
- 插入数据之后
  - 可以通过SELECT查询看到
- 有插入就有删除
  - 删除表中的数据吗？🤔
- 下次再说 👋
