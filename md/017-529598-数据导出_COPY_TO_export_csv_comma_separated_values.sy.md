---
show: step
version: 1.0
enable_checker: true
---

# 数据导出

## 回忆

- 上次我们还原了数据库
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

### 分析数据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658469009484)

- 输出应该用的是COPY这条命令
- 我们可以具体试试么？

### 插入数据

- 首先连接到oeasydb
- 把login库清空

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671246459024)

- 然后执行COPY命令
  - 列之间的分割符是<kbd>Tab</kdb>
  - 行之间的分隔符是<kbd>回车</kdb>
  - 结束输入的分隔符是`\.`

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671246369630)

- 这样真的可以插入数据么？

### 检查插入结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671246517108)

- 证明插入成功😄
- 这个COPY命令怎么理解呢？

### 查看帮助

- \h COPY

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658469151754)

- 根据红色部分
	- 写一条语句来
		- 导出login表中 的 数据

### 运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671248478051)

- 观察数据文件

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671248500286)

- COPY真的可以
	- 导出数据了！
- 不过这个数据
	- 没有标题行
- 可以
	- 加上标题 么？

### 分析

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658469159000)

- 可以在红色词语的基础上
	- 添加上绿色的词语
- 不要翻页
	- 尝试写下sql文件

### 运行

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671248618247)

- 报错了
- 怎么办？

### 搜索报错信息

- 报错信息本身就是线索

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220722-1658469167753)

- 根据上图
	- 修改一下代码

### 修改代码

- 这次将表格导出到
	- 云端硬盘上
		- 成为csv文件了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671248750792)

- CSV有个好处
	- 什么好处呢？

### 电子表格

- 就是可以用电子表格软件打开了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220723-1658536744715)

- 前提是安装电子表格软件
- 如果没有的话
	- 可以安装一个 


### 安装办公应用

```
sudo apt install libreoffice
```

- 这个安装包还是比较大的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686271637264)

- 然后就可以用Calc 打开 csv文件了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230609-1686271796398)

- 什么是csv呢？

### csv

- csv是一种文件类型 

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220723-1658538191779)

- 为了清楚
- 我们输出的文件名的扩展名
	- 应该是csv

### 备份

- 文件名明确来源
- 扩展名明确文件类型csv
	- comma separated values

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671249295441)

- 那么csv、电子表格、数据库是什么关系呢？

### 数据存储

- 三者都是数据存储的方式

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20220723-1658538521713)

- csv
  - 单一文件
  - 数据无类型
  - 只有一个基础的表格结构
- 电子表格
	- 单一工作簿文件
	- 数据有类型
	- 可以有公式计算
	- 工作簿中可以有多个工作表
- 数据库
  - 是一个系统
  - 数据类型复杂
  - 多种数据结构
	- 表
	- 视图
	- 查询
	- ...
  - 适合于大型系统
- 数据导出
	- COPY TO
		- 就这样了
- 去总结一下吧🚶

### 总结

- 数据导出并不复杂
	- 用的是COPY命令

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20221217-1671249295441)

- 确实可以将数据导出
- 但是如何反过来？
	- 再将数据导入呢？🤔
- 我们下次再说！👋🏻
