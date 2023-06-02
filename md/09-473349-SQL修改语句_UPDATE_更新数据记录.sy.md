---
show: step
version: 1.0
enable_checker: true
---

# 修改数据记录UPDATE

## 回忆

- 上次我们 从登录表(login)里
	- `删除`了 数据
- 删除命令 
	- 是DELETE
- 插入命令 
	- 是INSERT
	- INSERT 也可以一次批量插数据
- 删除的时候
	- 一般都要 用WHERE子句筛选
		- 需要删除的记录
- 筛选出来的是行、记录、元组
	- 表(table)是一个relation(关系)
	  - 是 行和列的关系
	  - 行也叫row、tuple、record
	  - 列也叫column、attribute、field
- 增和删都有了
	- 可以改数据么？🤔

### 打基础

- 新建一个数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220421-1650504473053)

- 然后建立宝箱(table)的结构

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220421-1650504485232)

- 然后插入3条记录
- 修改本质上是
	- 先删除再插入
- 但我想 一条命令 完成更新
  - 有可能么？🤔

### 搜索文档

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650198647130)

- 还是得找个例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650198653546)

### 尝试

- 将用户oeasy的密码
	- 修改为321

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220421-1650504801666)

- 这样就更新密码了么？

### 结果

- 确实
	- 而且`oeasy`这条记录变成了最后一条

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220421-1650504770507)

- 回看UPDATE命令中
  - 有一个WHERE子句
    - WHERE username='oeasy'
    - 这是对于用户名进行的筛选
		- 就像DELETE中的一样
- 只不过
    - DELETE用于删除
    - UPDATE用于更新
- 如果我 不用WHERE子句
	- 进行限制呢？

### 清零

- 不作任何筛选的情况下
	- 所有的记录都被更新了
	- 相当于所有用户的密码统一了😲

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220421-1650504922273)

- 那我还想只更新oeasy的密码该如何呢？

### WHERE筛选

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650199290474)

- WHERE子句负责筛选
- 符合条件的才进行更新或者删除

### WHERE

- WHERE子句根据条件
	- 筛出相应的行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650199344822)

- 如果
	- 我想修改用户名呢？

### 继续

- 筛子还是那个筛子
	- 筛出的还是用户名为oeasy的行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220421-1650505136618)

- 只不过通过SET修改的
  - 不是password属性
  - 而是username属性

### 分工
- WHERE负责的是筛选
- SET 负责设置属性值
  - 或者说操作数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230317-1679017265556)

- 可以根据密码改用户名么？

### 试试

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657807002079)

- 好像真的可以

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657807020123)

- 可以一次更新两个属性么？

### 查看帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657807526491)

- 好像可以试试

### 更新多个属性

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220714-1657807396378)

- 确实可以啊~
- 学了好多SQL语句了
- 可以分出类型吗？

### SQL 分类

- 我们现在所学的语句可以分成两类
  - 操作数据库的结构
    - 对于库的增删改查
    - 对于表的增删改查
  - 操作表里面具体的数据
    - 对于记录的增删改查

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220421-1650505507033)

- DDL(Data Definition Language) 数据定义语言
  - CREATE,DROP,ALTER等等
  - DDL命令会影响整个数据库或表结构
  - 控制宝库和宝箱结构
- DML(Data Manipulate Language) 数据操作语言
  - INSERT、DELETE、UPDATE和SELECT等等
  - 但DML命令会影响表中的一个或多个记录
  - 在具体结构里面填充数据
  - 控制宝箱里面的宝贝

### 总结

- 这次我们在登录表(login)里面更新了数据
	- 数据存储在表里
- 表(table)是一个relation(关系)
  - 是行和列的关系
  - 行也叫row、tuple、record
  - 列也叫column、attribute
- 各种DML命令
  - 插入是INSERT
  - 查询SELECT
  - 删除DELETE
  - 更新是UPDATE
- 更新的时候
	- 一般都要用WHERE子句
		- 筛选记录
- 数据的增删改查
	- 都有了
- 我们总结一下？🤔
- 下次再说 👋
