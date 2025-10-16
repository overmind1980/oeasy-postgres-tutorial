---
show: step
version: 1.0
enable_checker: true
---

#  数据交集_INTERSECT_逻辑与运算_AND 

##  回忆

- 上次研究了一种嵌套查询的方法
	- 可以通过两轮筛选
		- 得到想要的结果集

- 筛选
	- 本质上是取得子集

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687494845213)

- 两轮筛选
	- 本质上是在结果子集中 取得子集

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687494857350)

- SQL语句是否可以使用集合运算呢？🤔

### 两个集合

- 武力值

```
SELECT 
    * 
FROM
    heroes
WHERE
    fight > 95
;
```

- 智力值

```
SELECT 
    * 
FROM
    heroes
WHERE
    intelligence >= 60
;
```

- 这两个集合需要取交集

### 交集运算

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687495442531)

- 这个代码能实现吗
###  具体代码

```
(SELECT 
    * 
FROM
    heroes
WHERE
    fight > 95)
    
INTERSECT

(SELECT 
    * 
FROM
    heroes
WHERE
    intelligence >= 60)
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687495545717)

- 还有什么好用的筛选方法吗？

### 筛选过程

```
SELECT 
    * 
FROM
    heroes
WHERE
    intelligence >= 60
    AND
    fight > 95
;
```

- AND的意思是而且
- 可以将前后两个布尔值进行与运算

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687496062366)

### 查看细节

```
SELECT 
    name,
    fight,
    intelligence,
    intelligence >= 60 AND fight > 95
FROM
    heroes
;
```

- 可以直接查看
	- 逻辑与(AND) 运算结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687496204757)

- 这样做有什么好处呢？


### 双层筛子

- 原来的方式
	- 过两次筛子
	- 不管谁先谁后
	- 都是比较复杂的
- 原来是过了一层筛子
	- 再过一层筛子

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687495798388)

- 这次我们直接来个双层筛子
	- 直接一把筛出来

### 逻辑与

- 现在的方式
	- 只过一次筛子
	- 遍历的次数大大减少
	- 减少cpu功耗
	- 减少运算时间
- 可以用这个方式查询出宝物吗？
- 要求
	1. 所在地为长沙
	2. 价值大于50
- 不要翻页
	- 自己尝试

### 查询宝物

```
SELECT 
    name,
    value,
    city
FROM
    items
WHERE
    city = '长沙'
    AND
    value >50
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687496480463)

- 再次尝试查询宝物表
	1. 效果为 寿命延长
	2. 价值小于50

### 逻辑与查询


```
SELECT 
    name,
    value,
    city
FROM
    items
WHERE
    effects = '寿命延长'
    AND
    value < 50
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687496687512)

### 逻辑与原理

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230624-1687570112958)

- 全真为真
- 其余为假

### 逻辑与

- 逻辑与的要求比较严苛
	- 既要满足...
	- 又要满足...

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230622-1687434011471)

- 1890年
	- Hollerith趁热申请博士学位
	- 没有正常的入学、上课、论文答辩过程
	- 哥大校方最后授予 荣誉博士
	- Hollerith对于制表机的巨大贡献是有目共睹的
	- 可是他也开始了既要...又要...的日子
- 1896年
	- Hollerith成立了自己的The Tabulating Machine Company
	- 开始了“只租不售”的销售方式
	- 卖配件、耗材……盆满钵满

### 失利
- 成名的Hollerith飘了
	- 人口普查局貌似已经离不开他的制表机
	- 新普查马上开始
	- 返回手工处理数据的时代是不可能的
	- 于是他开始提要求
		- 涨价
- 人口普查局里开了锅
	- 这小子 现在 还是局里的人啊
	- 自家人的钱 也要挣 
	- 现在还要涨价？！
	- 他都忘了这么些年局里是怎么支持他的了？！
	- 没有局里提供的大数据做实验
	- 人家当初来咱们这里之前就已经拿到专利了
	- 到咱们这儿显然不是为了升职加薪
		- 就是为了用咱的数据啊
		- 局里这么些年一直傻呵呵地投人投钱帮他一起研发

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230623-1687497650668)

- 新上任的人口普查局局长Simon North有点烦
	- 人口普查局这几年很风光
	- 很大原因就是因为每10年一次的人口普查工作做出了成绩
		- 没有乱花纳税人的钱
		- 效果还特别好
	- 公众和国会都看在眼里
- 这个时候怎么办呢?

## 总结🤔

- 我们这次了解了
	- 集合的交集运算
		- INTERSECT
	- 逻辑的与运算
		- AND
- 哪个效果好？
	- 显然是逻辑运算
		- 过一次筛子就解决所有问题
- 和 交集 对应的 集合运算 是
	- 并集
- 和 与运算 对应的 逻辑运算 是
	- 或运算
- 这两个怎么玩呢？🤔
- 下次再说？👋🏻