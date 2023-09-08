---
show: step
version: 1.0
enable_checker: true
---

# 数据库的还原

## 回忆

- 上次尝试备份数据库
	- 用的命令是pg_dump

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658408469748)

- dump的意思是转储
	- 把数据库转储到一个sql文件中
	- 包括
		- 其中所有的表
		- 表中所有的数据
- 然后就可以进行还原了
- 具体怎么还原呢?🤔

### 查询帮助

- 还原数据库
	- 好像也就是一句话

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658405932882)

- 我们试着执行一下

### 直接执行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671194868275)

- 好像就是把这个oeasydb.sql执行了一遍
- 先去看看oeasydb.sql转储文件到底做了些什么？
- 难道这个备份文件里面没有CREATE DATABASE?

### 查看dump转储文件

- 确实没有和DATABASE相关的语句
	- 第一个CREATE的就是TABLE
- 我们需要手动建好oeasydb这个库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658407827250)

- 但是由于目前已经有了
	- oeasydb这个库
	- login这个表
- 导致整个还原过程
	- 只向login表插入了3行记录
- 尝试先把oeasydb这个库删除了

### 查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671194991086)

- psql -c XXX
	- c 的意思应该是 command
	- 可以执行一条sql命令
- 对比 psql -f XXX
	- f 的意思是 file
	- 可以执行XXX这个文件中所有的sql语句

### 删除

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671195100386)

- 删除结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671195128408)

- 确实将oeasydb删除了
- 删除了是为了看看oeasydb.sql能否将他恢复

### 恢复oeasydb中的数据表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671195202043)

- 失败！！！
- 由于oeasydb.sql中
	- 没有CREATE DATABASE的语句
- 环境中 根本没有 oeasydb产生
	- 数据库不知道还原到谁去
	- 导致还原失败
- 怎么办呢？

### 先建库再还原

- 有了oeasydb这个库之后
	- 就可以将转储的数据
		- 还原过去了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671195355142)

- 可以把oeasydb库里的内容
	- 还原到一个叫o2zdb名字的库里面吗？

### 还原到别的名字上

- 可以还原

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671195432512)

- 本质上就是执行sql语句
- 不过
	- 总用sudo -u postgres psql ...
		- 执行非常麻烦
- 能否直接使用postgres用户来登录呢？

### 切换用户

- 直接切换到postgres

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671196066794)

- shell不是默认的zsh
	- 想要修改默认shell为zsh
		- 并配置zsh
- 先exit当前登录回到shiyanlou

### 配置postgres的zsh

- sudo chsh --shell /bin/zsh postgres
	- 将postgres用户默认shell
		- 修改为/bin/zsh
- sudo cp /home/shiyanlou/.zshrc /var/lib/postgresql
	- 将shiyanlou用户的.zshrc配置文件
		- 拷贝到postgres的宿主文件夹中

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671244598818)

- 这样postgres登录环境会有变化吗？

### 登录

- 这次确实postgres登录状态确实变化了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671244616052)

- 这样就可以用psql用户的身份
	- 直接执行sql 或者 单条命令 了吗？

### 用postgres用户执行sql语句

- 确实可以执行单条sql语句了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671196362290)

- 可以批量执行sql文件吗？

### 用postgres用户执行sql文件

- 执行sql文件成功！！

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671243524720)

- 可以用postgres这个用户还原数据库吗？

### 用postgres用户还原数据库

- 还原数据库的本质其实就是
	- 连接到指定的数据库
	- 并且执行sql文件

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671243681897)

- 由于表名login已经存在
- 所以CREATE TABLE 出了问题
- 但是这个数据插入login表了吗？

### 观察

- 连接数据库并查询sql语句

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671243808304)

- 确实插入了
	- 所以现在login表里面的数据是重复的两份
	- 这有点问题
	- 问题出在哪儿呢？
- 再观察一下oeasydb.sql

### 分析

- 虽然建表的语句
	- 会发生ERROR
- 但是执行过程
	- 并没有被终止

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658405496217)

- 后面插数据的语句
	- 依然继续执行了
- 再去试试

### 再恢复

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671245112331)

- 确实如我们所料
	- 出现了ERROR
		- sql批处理不停止
		- 继续后面插入数据
		- 导致又多了3行
- 能否让他遇到ERROR
	- 就停下来呢？

### 查看帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658412132234)

- 执行命令的时候加一个参数试试

### 运行

- 执行命令psql的时候
	- 设置好ON_EEERO_STOP这个参数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671245294193)

- 这次遇到ERROR
	- 就会自动停止下来了
- 后面插数据的部分
	- 就不会执行了

### 继续观察帮助

- 可以换个参数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658412583927)

- 让本次恢复过程
	- 作为一个事务(Transaction)
	  - 要么全做
	  - 要么不做
- 事务会保持原子性
	- 做了的也会回滚(ROLLBACK)

### 尝试

- psql -1 oeasydb < oeasydb.sql

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671245682954)

- 最终数据如何？

### 最终数据

- 没有插入新的数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671245802844)

- 由于遇到了ERROR
	- 这个事务决定都不做
	- 于是进行了回滚(ROLL BACK)
- 帮助里面还有什么交代的呢？

### 远程备份加还原

- 这条命令中
	- 有一个`管道符|`
	- 键盘上的位置在回车附近

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658412925623)

- 这个管道的前面 
	- 是生成转储的sql
- 管道的后面
	- 是接收sql文件并执行
- 先备份
	- 然后将备份结果通过管道
		- 直接还原到另一个库里
- 能否备份还原
	- 多个数据库呢？

### 多个数据库

- 应该是可以备份还原多个数据库的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658413521740)

- pg_dumpall
	- 备份所有的库
		- 转储为sql文件
- 还原的时候
	- 执行这个sql就可以了
- 基本先这样
	- 总结去!🚶

## 总结

- 这次还原了数据库
	- 本质上就是通过psql执行了相应的sql文件
	- sql文件是 将当前数据库传储 得到的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658461343039)

- 通过 这种方法
	- 我们就可以备份、还原数据库了
	- 这种还原 可以无视数据库的版本
- 不过 备份的语句里面
	- 好像没有用到 INSERT语句
- 那究竟是怎么
	- 插入数据的呢？🤔
- 我们下次再说！👋
