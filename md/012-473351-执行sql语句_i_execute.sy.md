---
show: step
version: 1.0
enable_checker: true
---

# 执行sql语句 i

## 回忆

- 上次总结了学到的东西
  - 建库的法宝
	- postgres
  - 数据库
	- DATABASE
  - 表
	- TABLE 
  - 数据
	- DATA
- 他们都可以进行
	- 增
	- 删
	- 改
	- 查
- 这样就可以建立起属于自己的数据库
  - 不过每次建立要打好多字很麻烦
  - 能否一下子就建立起一个数据库呢？🤔

### 思路

- 没思路 就看帮助
	- 看帮助 就是思路

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650201563773)

- 可以通过
	- \i '/tmp/test.sql' 
	- 执行批处理的sql命令吗？
- 我们去试试
- 首先
	- 先新建一个sql文件

### 新建

- 使用vi
	- 去编辑一个/tmp/test.sql文件

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650201672683)

- vi 是编辑器
- /tmp/test.sql 是被编辑的文件
  - /tmp 代表temporary 临时的
  - test 代表测试
  - sql
    - structured query language
    - 我们那些增删改查的语句都是sql语句

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650201682354)

- 进入之后
	- 注意左下角显示[新文件]

### 书写程序

- 按<kbd>i</kbd>键
	- 左下角出现插入
	- 将vim的模式切换进入到插入模式

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650201682354)

- 然后
	- 写新建新建库的sql命令
	- CREATE TABLE test;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650202373558)

- 输入完成后
	- <kbd>esc</kbd>退回到正常模式
	- 左下角 `-- 插入 --` 消失

```
CREATE DATABASE test;
```

### 保存程序

- 输入:w进行保存

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650202441067)

- 保存之后有提示

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220417-1650202469247)

- 如果想要深入vim学习
  - 可以去这里
  - [oeasy教您玩转vim](https://www.lanqiao.cn/courses/2840)

### 尝试执行

- 用postgres用户运行psql客户端

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658382927122)

- 执行之后有成功提示
  - CREATE DATABASE
  - 并且确实可以查找到新建的库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658382964917)

- 如果再执行一次test.sql会如何呢？

### 再次执行

- 按方向键<kbd>↑</kbd>找到上一条命令
	- \i /tmp/test.sql
	- 回车
	- 再次运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658383018863)

- 这也很合理
	- 执行一次之后
	- 就已经有了test这个数据库
	- 想要再建一个同名的test
	- 就会报错
- 我们尝试把数据库初始化程序写得完整一点
  - 建库
  - 建表
  - 插数据
  - 全都一把完成

### 重写程序

- 按<kbd>i</kbd>
	- 左下角出现`插入`
	- 然后插入如下的新建库的命令

```
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

- 输入完成后
- <kbd>esc</kbd>
	- 退回到正常模式
- 输入:w
	- 保存

### 观察

- 现在的代码
	- 删库
	- 建库
	- 建表
	- 插入数据
	- 一气呵成

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658383359963)

- :q
	- 退出vim
- 尝试执行这条sql批处理处理命令

### 尝试执行

- 再次以postgres身份运行psql

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658383589468)

- 执行成功
- 这样就是
	- 连建库
	- 到建表
	- 到插数据
	- 一条龙了🐲

### 总结

- 这次我们编辑了sql文件
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
- 不要停止
	- 走入下一个实验
- 下次再说 👋
