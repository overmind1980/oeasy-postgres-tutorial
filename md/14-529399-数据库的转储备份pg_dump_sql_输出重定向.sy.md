---
show: step
version: 1.0
enable_checker: true
---

# 数据库的转储备份pg_dump

## 回忆

- 上次我们优化了工作流

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

### 还原

- 在pg官网搜索restore

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658403787417)

### 深入

- 我们看到一个单词反复出现

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658404101395)

- dump
	- 这个单词什么意思？

### dump动词

- dump的原意
	- 指的是倾倒一些没有用的东西
	- 比如倒垃圾

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658404251408)

### 名词

- 名词的含义就是垃圾场
- 据说俚语里面还有吸毒的意思😱

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658404513114)

- 计算机中也有一些临时的东西
	- 随着程序的运行总是变来变去
	- 比如内存堆(heap)中的对象

### 转储

- 在计算机中dump被翻译成转储

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658404643255)

- 就是把某个时刻的内存中的状态
- 通过文件的方式转储下来
  - coredump
  - threaddump
  - heapdump
  - tcpdump
- 这样这个状态我们就可以分析了
- 进而进行程序排错
- 这其实是一种备份数据库的方法
- 总共有三种方法

### 三种方法

- 数据库中的数据非常珍贵
- 需要备份起来

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658404877192)

- 有三种方法
  - sql dump(转储)
  - 文件系统层面的备份
  - 持续文档化
- 我们先看看这个sql dump(转储)

### pg_dump分析

-  pg_dump 是一条命令

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658405079433)

- 看到这个 >
	- 感觉这里应用了输出重定向
	- 把输出的结果重定向到oeasydb.sql文件
- 我们先不加重定向
	- 试试🏃

### pg_dump执行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658460302663)

- 确实是输出很多sql命令
  - 比如CREATE TABLE 这一行
  - 这就是pg生成的标准的sql语句
  - 我们可以注意他的换行和大小写
- 把这些输出可以重定向到oeasydb.sql

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658460529808)

### 动手

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658405323403)

- 好像得到了一个不到1k的oeasydb.sql文件
- 我们打开试试

### 打开

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658405496217)

- 备份了login表结构
- 备份了login中的数据
- 成功了！
- 开心！
- 先去总结一下

## 总结

- 我们这次尝试备份数据库
	- 用的命令是pg_dump

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220721-1658408469748)

- dump的意思是转储
	- 把数据库转储到一个sql文件中
- 然后就可以进行还原了
- 具体怎么还原呢?🤔
- 下次再说!👋🏻
