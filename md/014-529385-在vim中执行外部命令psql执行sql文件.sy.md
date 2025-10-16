---
show: step
version: 1.0
enable_checker: true
---

# 在vim中执行外部命令psql

## 回忆

- 上次想要解决
	- 在shell和psql中来回反复切换的问题
- 全都在psql中执行
  - \e 进行编辑
  - \i 进行运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658391401106)

- 这样就可以不用
	- 先\q退回到shell
	- 再进vim了编辑sql了
- 还有更好用的工作流么？

### 查询外部命令

- 尝试观察一下psql命令的参数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658391837636)

- 好像可以执行文件中的sql语句

### 尝试运行

- sudo -u postgres psql -f /tmp/test.sql
	- sudo -u postgres 使用postgres身份
	- psql 运行psql客户端
	- -f /tmp/test.sql 执行这个文件

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671193501137)

- 执行成功！

### 编辑

```
\c postgres

DROP DATABASE IF EXISTS
    oeasydb;

CREATE DATABASE
    oeasydb;

\c oeasydb

CREATE TABLE login(
    username VARCHAR(20),
    password VARCHAR(20)
)
;

INSERT INTO
    login(username, password)
VALUES
    ('oeasy', '123'),
    ('o2z', '456'),
    ('o3z', '789')
;

```
- 在shell中用vim打开/tmp/test.sql

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686232098549)

- 尝试:w保存

### 运行结果

- 保存失败

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686232125947)

- 原因就是

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686232159778)

- 当前shell的默认用户名shiyanlou
	- 已经失去了对于/tmp/test.sql的写权限
- 那怎么办呢？？

### 工作流调优

- /tmp/test.sql的写权限从shiyanlou手里
	- 给到了postgres手里
		- 所以用postgres就可以写/tmp/test.sql了
- 首先以postgres身份进入psql

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671193806008)

- \e /tmp/test.sql
	- 进行编辑

### 保存并执行sql文件

- 由于我们是以postgres的身份执行的psql
	- 所以可以保存 
		- 然后直接运行psql -f /tmp/test.sql

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671193919958)

- 确实是可以执行sql语句的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671193945019)

- 为什么不用加sudo -u postgres呢？

### 用户

- 我们运行psql命令的时候
	- 是以postgres这个用户来运行的
	- 所以在psql中我们进入vim的时候
	- 还是以postgres用户来运行的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230608-1686232411913)

- 在vim中运行外部命令的时候
	- 用户还是postgres
	- postgres刚好是能执行psql命令的用户
	- 所以就可以直接执行了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658392626546)

- 除此之外还有个前提

### 另一个前提

- 还有个前提是postgres用户
	- 有/tmp/test.sql的写权限

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658390504342)

- 现在我们可以不出psql中的vim
	- 就在vim中编辑并运行sql文件
	- 也可以在vim中 执行sql文件中的内容
- 我觉得这就是最好的工作流了
	- 如果您还有更好的
	- 请通过纠错告诉我
- 我们一起让教程进步

### 总结

- 这次我们优化了工作流

1. 先进入psql
2. \e /tmp/test.sql 编辑sql文件
3. :w|!psql -f % 保存并运行sql文件
4. :q 退回到psql执行其他的交互命令

- 这样就可以批处理sql语句了
	- 也就可以初始化数据库了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658393108067)

- 但是如果我们不想恢复到出厂状态
	- 而是希望把当前状态备份(backup)
	- 方便以后可以进行还原(restore)
- 应该怎么做呢？🤔
- 我们下次再说👋🏻
