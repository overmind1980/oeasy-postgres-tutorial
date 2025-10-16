---
show: step
version: 1.0
enable_checker: true
---

# 在psql中编辑并运行sql语句

## 回忆

- 上次我们编辑了sql文件
  - sql文件是纯文本文件
  - sql批量处理sql命令

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658383948877)

- 然后我们执行了sql文件
  - 在postgres中
	  - `\i /tmp/test.sql`
	  - 执行sql文件
- 但是编辑和执行分别在两个模式·
  - shell
  - psql
- 切模式很麻烦
  - 能否在一个模式中就连编辑带执行
  - 一条龙全做了呢？🤔


### 先查帮助

- 首先还是要以postgres的身份
	- 运行psql
- 然后在psql中 help

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671187613185)

- \?查询psql命令
	- 搜索执行外部命令的的方式

### 搜索
- 执行的单词是execute
	- 可以搜索ex找到相关信息
- /ex 在帮助文档中 搜索ex
	- 找到红框中的方式

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671246753457)

- 尝试在psql中运行外部命令vim

### 运行外部命令

```
\! ls
\! pwd
\! whoami
\! vi /tmp/test.sql
```

- 运行命令

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240604-1717465511476)

- 明确当前运行psql的用户是postgres
- \\! vi /tmp/test.sql进行编辑

### 编写代码

```
DROP DATABASE 
	IF EXISTS oeasydb;

CREATE DATABASE 
	oeasydb;

\c oeasydb

CREATE TABLE login(
	username VARCHAR(20), 
	password VARCHAR(20)
);

INSERT INTO
	login(username,password)
VALUES
	('oeasy','123'),
	('o2z','456'),
	('o3z','789')
;
```

- 编辑器的配色方案比较原始
	d- 有没有
	- 可以 直接编辑文件的 命令 呢？

### 编辑命令

- 在psql中是可以直接编辑文件的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658390085992)

- 我们试试

### 编辑sql文件

- \e /tmp/test.sql
	- e的意思是编辑
	- edit

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671192293947)

- 我们选择1号编辑器
	- vim

### 保存问题

- 打开之后
	- 发现这个sql文件依然是只读的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671192362373)

- 怎么解决这个权限的问题呢？

### 所有者问题

- 进入 psql 使用的是 postgres身份
	- 而 /tmp/test.sql 的所有者为 shiyanlou
- 可以将 /tmp/test.sql 的所有者
	- 设置为 postgres 
- 注意这次所有权变化
	- postgres 从 shiyanlou 手里抢得
		- /tmp/test.sql的所有权之后
	- shiyanlou 就失去了
		- 对 /tmp/test.sql 的写权限

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658390504342)

- 然后再去
  - \e /tmp/test.sql

### 可写

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671192598271)

- 这次/tmp/test.sql就不是只读的了

### 尝试写入

- :w
  - 确实是可以写入文件的
- :q
  - 退出vim
- \i /tmp/test.sql
  - 执行test.sql语句

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671192694661)

- 执行成功

### 尝试再次运行

- 方向键<kbd>↑</kbd> 
	- 找到上一条命令
	- 尝试再次运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671192788252)

- 出现了错误

### 纠错

- 错误原因是
	- 在连接着oeasydb数据库的时候
	- 尝试着删除oeasydb
	- 就像在当前文件夹中删除当前文件夹
	- 人不能靠提着头发跳起来
- 尝试修改
	- \e /tmp/test.sql
	- 在最开始的时候添加一句

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658390916701)

- 先从oeasydb中退到postgres中
	- 再去尝试删除

### 尝试运行

- 这次可以顺利成功了
	- 都是在psql里面进行的
		- \e 进行编辑
		- \i 进行运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658391078970)

- 不过配色方案有点问题
- 想要使用
	- 默认用户shiyanlou的vim配置

### 复制vim配置文件

- 从/etc/passwd中找到两个用户的宿主文件夹

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671193032331)

- 将vim配置文件.vimrc
	- 从/home/shiyanlou
	- 复制到
	- /var/lib/postgres中
- 再运行psql

### 观察默认编辑器

- 在psql中编辑文件

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671193169738)

- 默认编辑器已经替换

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671193200275)

- 先到这里
	- 去总结吧

### 总结

- 这次想要解决
	- 在shell和psql中来回反复切换的问题
- 全都在psql中执行
  - \e 进行编辑
  - \i 进行运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658391401106)

- 这样就可以不用
	- 先\q退回到shell
	- 再进vim了编辑sql了
- 还有更好用的工作流么？
- 我们下次再说
