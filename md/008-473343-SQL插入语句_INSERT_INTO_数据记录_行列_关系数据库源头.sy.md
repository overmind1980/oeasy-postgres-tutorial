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

- 但是
	- 新建的 login 表中
	- 没有数据
- 就像
  - 数据宝库的宝箱里面
  - 没有宝贝一样
- 如何 
	- 把宝贝放到格子里？🤔
- 或者说
	- 把数据插到表里？🤔

### 查询帮助

```
\h INSERT
```

- INSERT 命令应该是
	- 向表中插入数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650457248213)

### 帮助手册

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650179572150)

### 例子

- <kbd>G</kbd>
	- 翻到最后去找例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458492948)

- 去网页搜索个例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458520999)

- 这个看起来能用！

### 插入数据

```
INSERT INTO 
	login(username,password)
VALUES
	('oeasy','123')
```

- 真的插入成功了么？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458710515)

- 我去问问数据库

### 查询

```
SELECT 
	*
FROM
	login
;
```

- 真的出来了！！！

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458755299)

- 对比一下帮助手册中的语句

### 查询帮助

- 红框的部分
  - INSERT INTO login
  - 是基本的结构
- 黄框的部分是
  - (username,password)
  - 是表的描述
  - 在中括号中
  - 是可省略的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650458978937)

- 绿框的部分
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


```
INSERT INTO 
	login
VALUES
	('o2z','456')
```

- 将表结构中的列名省略

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650459421362)

- 依然可以插入数据
	- 果然表结构是可省略的
- 但是可能会有什么问题么？

### 列序

```
INSERT INTO 
	login
VALUES
	('password','username')
```
- 如果不明确指定列名
	- 可能插错位置

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220425-1650844586843)

- 绿框中
	- 位置 插拧巴了
	- 驴唇不对马嘴
- 最好还是
	- 把列元组写清楚
- 列的顺序
	- 必须按照建表时候的顺序么？

### 插入

- 插入时
	- 列的次序 是不固定的
	- 但只要 对应好 就可以

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650459800030)

- 现在 
	- 数据库postgres的login表中 
	- 有4行了
- 4行 2列 这个结构
	- 是谁发明的呢？

### 理论来源

- 1970年的一篇文档

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650180801566)

- 题目是
   - 《大规模分享的数据银行的关系模型》
	- A Relational Model of Data for Large Shared Data Banks
- 作者是谁呢？

### 祖师

- IBM的工程师艾加德.柯德
	- E.F. Codd

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650180941243)

- 他提出了
	- 关系模型

### 关系模型之前

- 原来的数据库 都是 层次结构的
	- 就像 今天的 文件系统结构 一样
- 最初的存储介质 是 卡片和柜子
	- 一个员工 一个盒子
	- 里面存着档案 和 工资记录之类的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181030487)

- 这种 层次结构
	- 被引用到了 计算机之中

### 层次结构发展

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220418-1650292227620)

- 从 文件夹的 层次结构

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220418-1650292246063)

- 利用 软连接之类的方式 构成了
	- 复杂的网状关系
- Codd把 网状关系 简化成 关系表结构
	- 那什么是 关系(relation)表 结构呢？

### 二维关系表

- 关系(relation)表结构 就是二维表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181142426)

- 这二维 指的是 哪二维 呢？

### 关系模型

- 关系 指的是 什么关系？
  - 行和列构成的
  - 关系(relation)

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
	- 开始使用attribute
	- 作为数据库的术语(term)
- attribute 原来 
	- 指的是什么 呢？

### attribute 属性 字段

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181441489)

- login 有两个字段
	- username
	- password

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650181455100)

### 思考

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

- 这次 
	- 我们往登录(login)表里
		- 插了数据
- 所谓表(table)
  - 是一个关系(relation)
	  - 是行和列的关系
  - 行也叫
	- row
	- tuple
	- record
  - 列也叫
	- column
	- attribute
	- field
- 插入数据之后
  - 可以 通过SELECT查询 看到
- 有插入就有删除
  - 删除表中的数据吗？🤔
- 下次再说 👋
