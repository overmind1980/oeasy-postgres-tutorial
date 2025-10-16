---
show: step
version: 1.0
enable_checker: true
---

# 安装卸载

## 回忆

- 我们了解了数据库的排行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230907-1694093715005)

- 分析了前三名
  - oracle
  - mysql
  - mssql server
- 最后选用的是
	- postgres

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221209-1670579455827)

### 法宝

- 数据库 是 
	- 数据的大宝库
- postgreSQL 是
	- 数据大宝库管理程序
    - 数据库管理程序也叫 DBMS
	- DataBase Management System
    - 可用这个法宝管理数据宝库
	- 可以造出来数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650374877504)

- 我们装上了 postgresql
  - 也就有了制造数据宝库的法宝
- 卸载 postgres
  - 也就是废掉可以制造数据宝库的法宝

## 尝试运行

- 我们尝试直接运行 psql
  - 系统报错
  - 找不到 psql 这个程序
  - 所以无法执行
  - 这个postgres要先安装

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240510-1715331075582)

- 这个postgres到底怎么安装呢？🤔

### 更新源

```
sudo apt update
```

- 安装 postgresql 之前
	- 要先更新软件源

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221209-1670581266891)

- 更新之后
	- 可以安装较新的postgres

### 安装postgres

```
yes | sudo apt install postgresql
```

- apt 是 
	- `a`dvanced `p`ackage `t`ool(高级包工具)
	- 可以在 [oeasy教您玩转linux](https://www.lanqiao.cn/courses/2712?tab=labsList) 中
	- 找到详细资料

- 有询问的地方
	- 回答 yes

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240510-1715331154018)

- 装好了之后
	- 看一下这个软件安装情况

### 查看软件

```
sudo apt show postgresql
```

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240510-1715331165006)

- 软件确实装上了
	- 运行 psql 试试

### 尝试运行

- 又报错了
	- 不过不是
	- 找不到程序！！！
	- 绿光

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240510-1715331196269)

- 这就说明
	- 原来没有 psql
    - 现在有了
- 这个报错怎么处理？

### 搜索

- 错误本身就是答案！
	- 将报错语句复制下来进行搜索
	- 搜索到的结果就是答案

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220415-1649982514055)

- 无法连接服务器的原因
  - 是没有启动postgres服务器
- 问题是如何启动呢？🤔

### 继续搜索

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220415-1649983590194)

### 启动服务

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650373260592)

- 搜到了这样的结果

### 运行

```
sudo service postgresql start
sudo service postgresql status
```

- 到服务器上试着启动postgres服务

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240510-1715331286686)

- 好了！
	- 终于服务起来了！

### 再次尝试启动psql客户端

- 使用默认的 shiyanlou/oeasy  用户登录
  - 失败了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650373905323)

- 只能用管理员权限以 postgres 用户方式运行psql
  - 终于成功！！！
- 为什么还需要专门账号
	- 才能运行pg？

### 分离

- postgres 做了角色隔离
	- 系统管理员(System Administrator)
		- root
	- 数据库管理员(DataBase Administrator)
		- postgres
- 两个 用户名 
	- 分属两个类型

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221209-1670588381128)

- pg怕系统管理员
	- 不懂数据库进行误操作
- 所以
  - 单独有一个专门的账号 postgres
  - 作为数据库管理员 dba(database administrator)
- 我如果就想作为 postgressus
	- 登录shell怎么办呢？

### 查看帮助

- 得先退出 psql客户端
  - 回到 shell
- 怎么退出呢？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650374145868)

- 现在的任务是
	- 用 postgres 用户名 
	- 登录 shell
	- 然后直接运行 psql

### 继续搜索

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220415-1649984594603)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220415-1649984604172)

### 修改密码

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240510-1715331545552)

- 更新 postgres 用户的密码
- 然后使用 postgres 和新密码登录

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20240510-1715331607357)

- 真的用 postgres 用户登录上去了😄
  - 并且可以用 postgres 用户运行psql客户端程序！！！
- 既然可以安装postgresql
  - 也可以卸载他么？

### 卸载postgresql

- 先叉掉 
	- 当前用postgres登录的终端窗口
- 然后
	- 新打开一个中端
- 键入 `sudo apt remove postgresql*`
  - 注意结尾的星号
  - 星号就是通配符(混儿)
  - 可以代表任意多个任何字符
  - postgresql-12、postgresql-common 等都会被卸载

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220415-1649985193633)

- 卸载之后
	- psql 程序就找不到了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220419-1650375090968)

- 法宝被废掉了
  - 就找不到了
  - 回到了最初的状态

## 总结

- postgres是我们的法宝
  - 用他可以构造数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419271477)

- 我们
	- 首先安装了 postgrsql
	- 然后启动了 postgresql 服务

```bash
sudo service postgresql start 
#这句是启动服务
```

- 先用管理员权限
  - 再以 postgres 用户身份
  - 运行psql数据库程序

```bash
sudo -u postgres psql 
```

- 法宝有了
	- 到底怎么建立起
	- 属于自己的数据宝库呢？🤔
- 下次再说 👋
