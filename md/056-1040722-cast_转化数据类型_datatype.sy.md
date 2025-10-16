---
show: step
version: 1.0
enable_checker: true
---

#    升序降序_ASC_DESC_ascend_descend_词源词根  

##  回忆

- 上次 查询了 综合素质
	- 数值 来自于 武力和智力 的 平均值
	- 平均值 来自 整数地板除 的结果
	- 将 除数 设置为 2.0 之后
	- 除法模式 变为 浮点数除法
		- 商为浮点数
- 商可以 用各种方式取整
	- round 四舍五入
	- ceil 天花板
	- 地板
- 能否对 浮点数类型 和 整数类型 
	- 进行 类型转化呢？

### 搜索 cast

- https://www.postgresql.org/docs/15/sql-expressions.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692257858226)

### 具体使用

- 将浮点数 转化为 整型数字

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692258195826)

- 如何理解这个int4呢？

### 搜索

- 搜索 databtype

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692258738486)

- int其实 就是
	- integer
	- 对应4-byte的整型数字

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692258701565) 

- 可以将整型数字
	- 转化为浮点型数字吗？

### 转化为浮点型

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692258947766)

- real 
	- 4-byte 浮点型
- double precision 
	- 8-byte 浮点型

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692258998839)

- 还有什么数字类型吗？

### 精确十进制 decimal

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692259110468)

- numeric
	- 精确十进制
	- 拥有极高的底数和指数的精度

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692259149013)

- 可以将数字 转化为 字符串吗？

### 字符串类型

- character
	- https://www.postgresql.org/docs/15/datatype-character.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692259289999)

- 类型列表

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692259313862)

- 更多字符类

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692259716107)

- "char" 对应单字节类型
- 可以将字符串转化为数字吗？

### 转为数字

- 将字符串转化为数字

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692260276642)

### ascii序列

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692259847220)

- 对应生成结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692259862444)

- 可以有字节序列类变量吗

### 字节序列类

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692260064304)

- 尝试查询

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692260076842)

- 字符串和字符序列可以相互转化吗？

### 搜索encode

- https://www.postgresql.org/docs/15/functions-binarystring.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692260484092)

- 尝试使用convert_to
	- 将字符串 转化为字节序列

### 转化

- convert_to

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692261573926)

- 可以将字符序列 转化为字符串吗？

### 解码

- 先将纯字符串转化为字节序列
	- 再将 字节序列进行解码

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230817-1692262497742)

- 总结一下本次内容

## 总结
- 这次研究的是类型转化
	- 数值型
		- 整数
		- 浮点数
		- 高精度十进制
	- 字节序列
	- 字符串
- 字符串中的长度设置有什么意义吗？🤔
- 下次再说？👋🏻