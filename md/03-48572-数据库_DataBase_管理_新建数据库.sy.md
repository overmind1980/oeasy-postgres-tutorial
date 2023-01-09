---
show: step
version: 1.0
enable_checker: true
---

# 数据库(DataBase)的管理

## 回忆

- postgres是我们的法宝
  - 用他可以构造数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419271477)

- 我们
	- 首先安装了 postgrsql
	- 然后启动了 postgresql 服务
	  - 先用管理员权限进入
	  - 再以 postgres 用户身份进入
	- 最后我们卸载了 postgresql
- 法宝有了
	- 到底怎么建立起属于自己的数据宝库呢？🤔

### 再次进入

- sudo -u postgres psql
  - sudo
    - 使用管理员权限
  - -u postgres
    - 作为postgres用户执行
  - psql
    - postgres的命令行程序

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650074512962)

- 提示说让我们help for help
- 第一个是
  - \copyright
  - 版权说明

### 版权

- 73年开始有Ingres
	- 是很多数据库的源头
	- 95年叫做postgres95

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650074711160)

- 是由postgreSQL全球开发组拥有版权
- 可以以任何理由
	- 使用拷贝修改和分发这些软件
	- 不需要任何费用
	- 也不需要任何的书面协议和许可证
	- 但是要把后面这两段版权声明放在所有的拷贝中:

### 版权

- 加利福尼亚大学不应对任何一方负责
	- 直接、间接、特殊、偶然或后果性损害
	- 包括因使用本软件及其产品而产生的利润损失文件
	- 即使加利福尼亚大学已被告知这种损害的可能性
- 加利福尼亚大学特别否认任何保证
	- 包括但不限于对适销性的默示保证
	- 以及特定用途的健身
	- 以下提供的软件是在“原样”的基础上
	- 加利福尼亚大学没有义务提供维护、支持、更新、增强或修改

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419414374)


- 看起来好像不用负任何费用
  - 而且也没有任何责任
  - 法宝威力太大
  - 版权就是要免责😅
- 我们继续help看看帮助

## 查看帮助

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650075589419)

- \h 查看命令

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650075598316)

- <kbd>↑</kbd>、<kbd>↓</kbd>
  - 上下移动一行
- <kbd>ctrl</kbd>+<kbd>f</kbd>、<kbd>ctrl</kbd>+<kbd>b</kbd>
  - 上下翻页
- <kbd>q</kbd>
  - 退出当前帮助内容

### 找到规律

- 有些词汇频率很高
  - CREATE
    - 新建
  - ALTER
    - 修改
  - DROP
    - 删除

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650075780128)

- 我们首先要新建数据库！

### Database

- 数据库就是DataBase
- 也就是要
  - 新建数据库
    - CREATE DATABASE
  - 修改数据库
    - ALTER DATABASE
  - 删除数据库
    - DROP DATABASE

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650076575213)

- 具体怎么新建呢？

### Manual

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419634588)

- \h XXX可以查看具体的命令

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419738579)

- 红中括号里面都是可省略的选项
- 最关键的只有一句

### 新建数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419809389)

- 这句红色最重要
- 试着执行

### 执行之后
- 执行了CREATE DATABASE oeasydb 之后
	- 但是输入之后没有任何反应
		- 如下图

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650077199237)

- 看一下前面的提示符(prompt)
  - 从绿框中的<span style="border:3px solid green">=</span>开始输入
	 - <span style="border:3px solid green">=</span>号的意思是等你的命令
  - 回车后
	- 绿框中的<span style="border:3px solid green">=</span> 变成了黄框<span style="border:3px solid yellow">-</span>
  - <span style="border:3px solid yellow">-</span>号的意思是命令还没有输入完
	- 在等待继续
    - 等待什么呢？
- 等待输入一个;(semicolon)
  - ; semicolon 分号
    - 分号作为语句结束的标志
- 输入分号并回车之后
  - 命令通过psql
  - 交给了服务器的后端(backend)去执行
  - 执行之后
	  - 系统报出反馈信息 CREATE DATABASE
	- 井号前面的 黄框中的<span style="border:3px solid yellow">-</span>  
	- 变成了绿框中的<span style="border:3px solid green">=</span>
	- 继续等着你输入
- 这样就建立了数据宝库？！
  - 如何查看新建的宝库呢？

### 搜索

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650080941278)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650080948434)

- 看起来就是
	- \list 或者 \l

### 查看数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420347381)

- \list或者\l可以查看数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420360942)

- 真的可以看到自己建的数据库！！！
  - 可以看得更真切么？
- 先<kbd>q</kbd>退出查询结果

### 更真切

- \x 切换模式
 
![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420440156)

- 从表格模式切换到
	- 记录扩展模式

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420497639)

- 总共有4个数据宝库
- 第1个就是刚刚新建的！！！
- 如果只想看新建的oeasydb应该如何呢？

### 查询数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650423526644)

- 查询叫oeasy的数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650423536239)

- 查询的时候会使用到通配符
  - \*
    - 代表零到任意多个任意字符
  - ？
    - 代表一个任意字符
- \l oeasy*  就是 查询oeasy开头的数据库
- 想要连接oeasydb数据库
- 可以么？

## 总结

- 这次研究的是数据库database
- 用数据库管理程序(dbms)去管理数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221209-1670592407879)

- 可以新建数据库
    - CREATE DATABASE
- 可以查询数据库
    - \l
    - \l oeasy*
- 不会了就去查帮助
  - help
	- 是总体帮助
  - \h
	- 是查询所有SQL语句
  - \h CREATE DATABASE
    - 是查询具体SQL命令
- 如何连接数据库呢？🤔
- 下次再说 👋
