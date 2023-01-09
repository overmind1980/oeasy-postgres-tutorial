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
- 然后就可以进行还原了
- 我们先看看转储文件
- 具体怎么还原呢?🤔

### 查询帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658405932882)

- 好像就是一句话
- 我们试着执行一下

### 直接执行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671194868275)

- 好像就是把这个oeasydb.sql执行了一遍
- 先去看看oeasydb.sql转储文件到底做了些什么？
- 难道这个备份文件里面没有CREATE DATABASE?

### 查看dump转储文件

- 确实没有和DATABASE相关的语句

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658407827250)

- 第一个CREATE的就是TABLE
- 我们需要手动建好oeasydb这个库
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
	- 导致还原失败
- 怎么办呢？


### 先建库再还原

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671195355142)

- 可以把oeasydb的库还原到一个叫o2zdb的名字上吗？

### 还原到别的名字上

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671195432512)

- 可以还原
- 本质上就是执行sql语句
- 不过总用sudo -u postgres psql ...执行非常麻烦
- 有点麻烦能否直接使用postgres登录呢？

### 切换用户

- 直接切换到postgres

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221216-1671196066794)

- shell不是默认的zsh
- 想要修改默认shell
- 并配置zsh
- 先exit当前登录回到shiyanlou

### 配置postgres的zsh

- sudo chsh --shell /bin/zsh postgres
	- 将postgres用户默认shell修改为/bin/zsh
- sudo cp /home/shiyanlou/.zshrc /var/lib/postgresql
	- 将shiyanlou用户的zshrc配置文件拷贝到postgres的宿主文件夹中

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671244598818)

- 这样postgres登录是就可以自动使用配置正常的zsh了吗？

### 登录

- 这次确实postgres登录确实正常了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671244616052)

- 这样就可以用psql用户直接执行sql或者单条命令了吗？

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
- 所以现在库里面的数据是两份
- 这有点问题
- 问题出在哪儿呢？
- 再观察一下oeasydb.sql

### 分析

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658405496217)

- 建表的语句会发生ERROR
- 后面插数据的语句执行了
- 再去试试

### 再恢复

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671245112331)

- 确实如我们所料
- 出现了ERROR
- sql批处理不停止
- 继续后面插入数据
- 导致又多了3行
- 能否让他遇到ERROR就停下来呢？

### 查看帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658412132234)

- 执行的时候加一个参数试试

### 运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671245294193)

- 这次遇到ERROR就会自动停止下来了
- 后面插数据的部分就不会执行了

### 继续观察帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658412583927)

- 可以加上参数
- 让本次恢复过程作为一个事务(Transaction)
  - 要么全做
  - 要么不做

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

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658412925623)

- 这个管道的前面 
	- 是生成转储的sql
- 管道的后面
	- 是接收sql文件并执行

- 能否备份还原多个数据库呢？

### 多个数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658413521740)

- 应该是可以备份还原多个数据库的
	- 基本先这样
- 我们总结去!🚶

## 总结

- 这一次我们还原了数据库
	- 本质上就是通过psql执行了相应的sql文件
	- sql文件是将当前数据库传储得到的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658461343039)

- 通过这种方法
	- 我们就可以备份还原数据库了
	- 这种还原可以无视数据库的版本
- 不过备份的语句里面
	- 好像没有用到INSERT语句
- 那究竟是怎么插入数据的呢？🤔
- 我们下次再说！👋
