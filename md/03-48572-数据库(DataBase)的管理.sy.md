---
show: step
version: 1.0
enable_checker: true
---

# 数据库(DataBase)的管理

## 回忆

- postgres是我们的法宝
  - 用他可以建造数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419271477)

- 我们安装了postgrsql
- 然后进入了postgresql
  - 先用管理员权限进入
  - 再修改postgres用户密码进入
- 最后我们卸载了postgresql
- 到底怎么建立起属于自己的数据宝库呢？🤔
- 先要启动法宝！！！

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

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650074711160)

- 这个软件早年间叫做postgrs95
- 是由postgreSQL全球开发组拥有版权
- 可以以任何理由，使用拷贝修改和分发这些软件，不需要任何费用，也不需要任何的书面协议和许可证
- 但是要把后面这两段版权声明放在所有的拷贝中:

### 免责

- 加利福尼亚大学不应对任何一方负责。直接、间接、特殊、偶然或后果性损害，包括因使用本软件及其产品而产生的利润损失文件，即使加利福尼亚大学已被告知这种损害的可能性。
- 加利福尼亚大学特别否认任何保证，包括但不限于对适销性的默示保证，以及特定用途的健身。以下提供的软件是在“原样”的基础上，加利福尼亚大学没有义务提供维护、支持、更新、增强或修改

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650419414374)

- 这版权
  - 看起来好像不用负任何费用
  - 而且也没有任何责任
  - 法宝威力太大
  - 先要免责
- 😅
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

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650075780128)

- 有些词汇频率很高
  - CREATE
    - 新建
  - ALTER
    - 修改
  - DROP
    - 删除

### Database

- 要操作的是数据库DATABASE
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
  - 执行了CREATE DATABASE oeasydb 之后
- 但是输入之后没有任何反应，如下图

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650077199237)

- 看一下前面的提示符(prompt)
  - 从绿框中的<span style="border:3px solid green">=</span>开始输入
  - =号的意思是等你的命令
  - 绿框中的<span style="border:3px solid green">=</span> 变成了黄框中的<span style="border:3px solid yellow">-</span>
  - -号的意思是命令还没有输入完
  - 在等待继续
  - 等待什么呢？
- 等待输入一个;(semicolon)
  - : colon 冒号
  - ; semicolon 分号
    - 分号一般在语句的结尾
- 输入分号并回车之后
  - 命令交给了psql服务器的后端(backend)去执行
  - 系统报出反馈信息 CREATE DATABASE
  - 井号后面的 黄框中的<span style="border:3px solid yellow">-</span>  变成了绿框中的<span style="border:3px solid green">=</span>
  - 继续等着你输入
- 这样就建立了数据宝库？！
  - 如何看看所有的的宝库呢？

### 搜索

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650080941278)

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650080948434)

- 看起来就是\list

### 查看数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420347381)

- \list或者\l可以查看数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420360942)

- 真的可以看到自己的数据宝库！！！
  - 可以离得更近点、看得更真切么？
- 先<kbd>q</kbd>退出查询结果

### 更真切

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420440156)

- 先把扩展模式打开
- 然后再看

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420497639)

- 有四个数据宝库
- 第一个就是刚刚新建的！！！
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
- 想要进入oeasydb数据宝库
- 可以么？

### 进入

- 先查一下

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420652037)

- \c 应该就是关于连接的命令
- <kbd>q</kbd>退出查询结果
- 我们来试试

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650420953438)

- psql 作为前端(front-end)
  - 使用postgres用户连接到了oeasy
- postgres服务 作为后端(back-end)
  - 使用5432端口通过套接字
  - 接收前端发出的请求
  - 并且做出相应的反馈
- 真的建立了一个属于自己的数据宝库
- 既然这样
- 就多建几个

### 宝库

- 法宝一挥建立起了四个数据宝库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650422796729)

- 真的建立了么？

### 观察

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650423223511)

- 真的建立了
- 但现在宝库太多了
- 能否删除数据库
- <kbd>q</kbd>退出查询结果

### 先查手册

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650078444573)

- 蓝色中括号里面的东西是可省略的
- 简单一句话DROP DATABASE database_name

### 动手

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650423440333)

- 真的都删除了
- 现在o开头的数据库就一个oeasydb了
- 把他也删掉

### 删除

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650423136928)

- 删除失败了
- 不能删除当前正在打开的数据库
- 那我们就连到别的数据库看看

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650423783213)

- 进入postgres这个数据宝库
- 然后再删
- 好像删除了
- 确认一把

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650423860691)

- 确实删空了
- 再返回去看看手册

### IF EXIST

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650078444573)

- 蓝色框里面有个IF EXIST 如何理解？
  - 中括号可省略
  - IF EXIST的意思是如果存在

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650424132000)

- 如果要删除的数据库存在
- 那就直接删了
- 如果要删除一个不存在的数据库呢？

### 不存在的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650078803180)

- 没有IF EXIST
  - 直接报错ERROR
  - ERROR错误是这个oeasydb不存在
  - 这问题可能挺严重
- 有IF EXIST
  - 发出提示不报错
  - 提示NOTICE这个oeasydb不存在
  - 写命令的知道可能oeasydb不存在
  - 就是试试
  - 所以不报ERROR
  - 可以继续往下走
- 我们按照手册中给出URL去看看

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650079043653)

### 复制网址

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650425490757)

### 网页文档

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650079275235)

- 红色的标记📌标明了帮助的版本
- 可以切换看看其他版本
- 我们用的是postgresg12
  - 因为蓝桥虚拟机引用的源是postgresg12这个版本的
  - 所以上一次apt install的时候安装的是12
  - 如果你用的自己云可以更新源
  - 然后升级到最新的版本

### 文档细节

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650079715240)

- DROP DATABASE 是SQL命令
- 这个命令有两个参数
  - IF EXISTS
    - 如果有才删
  - name
    - 数据库的名字
- 如果我想一次建两个数据库呢？

### 建立两个数据库

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650080011688)

- 想要一句话搞定是不行的
- 分成两句是可以的么？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220416-1650080042152)

- 这告诉我们
  - 饭要一口一口吃
  - 不要想要一口吃个胖子
- 胖子:“我找谁惹谁了？！”
- 除了新建(CREATE)、删除(DROP)之外
  - 还有个ALTER 怎么用呢？

### 查文档

- 没有思路了就去help

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650424386110)

- 大致明白了
  - 要用的是红色框起的那句
- 可是
  - 目前有些什么数据库可以进行修改呢？

### 查询

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650424861999)

- 这些歌都是系统的数据宝库还有模板
- 我得新建一个再改

### 具体修改

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220420-1650424976895)

- 注意第3行
  - 从=的位置开始
  - =号就是等着你输入
- 注意第四行
  - -不是开始位置
  - 意味着前面有命令还没结束
  - 直到最后的分号才结束
- 换行缩进是为了清晰
  - 一般缩进4个空格
  - 没有换行缩进的话程序也好使
- 数据库还有什么特点呢?

### 小写数据库名字

- 即使建立的时候使用大写字母
- 真正建立的数据库还是使用小写字母的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220615-1655281214757)

- 有点举重若轻的意思
- 好像和python一样不喜欢大写字母
- 总结一下吧

## 总结

- 这次研究的是数据宝库database
- 用数据库管理程序(dbms)去管理db
- 可以进行四种操作(增删改查连接)
  - 增
    - CREATE DATABASE
  - 删
    - DROP DATABASE
  - 改
    - ALTER DATABASE
  - 查
    - \l
    - \l oeasy*
  - 连接
    - \c
- 不会了就去查帮助
  - help
    - 总体帮助
  - \h CREATE DATABASE
    - 查询具体SQL命令
- 拥有了数据的宝库
  - 可是，如何存储宝贝呢？🤔
- 下次再说 👋
