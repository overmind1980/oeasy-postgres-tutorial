---
show: step
version: 1.0
enable_checker: true
---

# 删除数据记录DELETE

## 回忆

- 上次 
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

### 查询帮助

- 查询一下DELETE的帮助文档

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650184591641)

- 删除的帮助很简短
- 动手试一下！！！

### 准备

- 看看表里面有几行？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650464171462)

- 有4行
- 如果是0行
	- 就先INSERT INTO 几行进去
	- 然后再删除

### 删除

- 这...

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650464265645)

- 删除是真的能删除
	- 但是一删除就把整个表给清空了
	- 3条记录一下子全没了
- 还得重新插入记录

### 重新插入

- 正常插入没有问题

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650184953514)

- 插入时
	- 不写列名可以么？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650185065867)

- 手册里的中括号 都是可省略的
	- 不过 我们试过的
		- 容易乱
	- 还是 写清楚列名
- 那我们 想要
	- 一次插入 多个数据
		- 可以么？

### 先查手册

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650464549143)

- 观察例子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650464558745)

### 批量插入

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650464848690)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650464839152)

- 回忆一下
	- 关系表的结构

### 表的结构

- 这一切的思路	
	- 出自Codd的一篇文章

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650185174604)

- 把 整个数据库
	- 从 层次式的文件夹结构
		- 变成 二维的表结构

### 关系数据库

- 表就是relation关系
  - 是行和列的关系
  - 行也叫元组、记录
  - 列也叫属性、域

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650185248032)

- 我们 这次想要删除 指定的记录
  - 删除 用户名为oeasy的记录

### 查询手册

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650185437670)

- 好像用WHERE子句就可以实现这个功能

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650185449220)

- 我们去试试！！！

### 定点删除

- 确实可以 通过筛选
	- 进行 定点删除

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650465003341)

- 再试几个！

### 再次定点删除

- 确实可以删除

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650465087319)

- 而且 
	- 这次是根据password删除的

### 最终

- 这样就可以控制
	- 宝箱里面的宝物了！！！

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650465331387)

### 总结

- 这次我们 从登录表(login)里
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
- 下次再说 👋
