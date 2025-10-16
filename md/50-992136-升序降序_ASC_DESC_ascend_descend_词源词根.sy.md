---
show: step
version: 1.0
enable_checker: true
---

#    升序降序_ASC_DESC_ascend_descend_词源词根  

##  回忆

- 上次我们了解了排序关键字
	- ORDER BY
- 可以按照指定的关键字
	- 从低到高进行排列
- 还可以指定多个关键字
	- 先按第一关键字排序
	- 再按第二关键字排序
	- ...
- 通过计算得到的结果列
	- 也可以作为排序的依据

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230701-1688212590242)

- 一般排序都是从低到高
	- 能否从高到低呢？🤔

### 复现上次结果

```
SELECT
    name,
    (fight + intelligence) AS ability 
FROM
    heroes
ORDER BY
    ability 
;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687921166597)

- 想要按能力从高到低
	- 应该怎么办呢？

### 从高到低

```
SELECT
    name,
    (fight + intelligence) AS ability 
FROM
    heroes
ORDER BY
    ability DESC
;
```

- 关键就在红框中

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687921361134)

- 其实有个缺省的排序方式


### 从低到高

```
SELECT
    name,
    (fight + intelligence) AS ability 
FROM
    heroes
ORDER BY
    ability ASC
;
```

- 默认的方式是ASC
	- 从低到高

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687921454708)

- ASC对应什么单词吗？

### ascend

- ascend
	- 英 [əˈsend]
	- v. 	上升; 升高; 登高

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687922286788)

- 向上爬
	- 树
	- 山
	- 楼梯
	- 数据
		- 数字越来越大
		- 小往大来

### 同源单词 ascendance

- ascendant
	- [əˈsendənt]
		- adj. 	向上的；优越的；占支配地位的;
		- n. 	优势；运星；支配地位

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687922747066)

-  ascendance
	- [ə'sendəns] 
	-  n. 	上升; 优越，权势，主权

-  ascendancy
	-  [əˈsendənsi]
		- n. 	优势; 影响; 支配地位

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687922844733)

### descend

-  descend
	-  [dɪˈsend]
	-  v. 	下降; 下来; 降临; 
	-  下去; 来临; 下斜; 下倾

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687922957781)

- 向下爬
	- 树
	- 山
	- 楼梯
	- 数据
		- 数字越来越小
		- 大往小来

### 下降

-  descending 
	- [dɪˈsendɪŋ]
	- adj. 	(次序)下降的，递减的;
	- v. 	下降; 下来; 降临; 下去; 来临; 下斜; 

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687923409191)

-  descendant
	-  英 [dɪˈsendənt]
	-  n. 	后裔; 后代; 子孙; 
	-  (由过去类似物发展来的)派生物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687923646385)

### condescend

- con 一起
	- descend 向下


![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687924151776)

-  condescend
	-  英 [ˌkɒndɪˈsend]
		-  vi. 	屈尊; 俯就; 

### scan

- scend
	- 上升; 攀登; 随波浪浮沉

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687924502099)

- 在树上、在山上、在楼梯上、在数据上
	- 上来下去
		- 巡逻

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687923969289)

- scan
	- [skæn]
		- v. 	(X射线、超声波、电磁波等)扫描;
		- （为搜索病毒而）扫描（文件）;
		- （用扫描设备）扫描（图像或文件等）;
		- 浏览; 审视; 察看; 翻阅; 细看; 
		- 端详; 粗略地读; 符合韵律;
		- n. 	浏览; 扫描检查; 
		- 快速查阅; 胎儿扫描检查;

###  transcend

- trans 越过
	- scend 攀爬

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687924453297)

-  transcend
	- [trænˈsend]
	- vt. 	超越; 超出(通常的界限);

### 相关单词总结

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687925069983)

### 多个排序关键字

```
SELECT
    name,
    effects,
    city,
    value
FROM
    items
WHERE
    effects IN ('确实撤退','寿命延长')
ORDER BY
    city,
    value DESC
;
```

- 第一排序关键字city
- 第二排序关键字 value 从高到底

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687924614328)

- 能否先排value从高到低
- 再排city

### 第一第二排序关键字调换次序

```
SELECT
    name,
    effects,
    city,
    value
FROM
    items
WHERE
    effects IN ('确实撤退','寿命延长')
ORDER BY
    value DESC,
    city
;
```

- 排序结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687924784641)

- 写了DESC的是
	- 递减排序
- 没有写DESC的是
	- 默认ASC
	- 递增排序

## 总结🤔

- 这次我们研究了排序的次序	
	- ASC 递增排序 越来越大
	- DESC 递减排序 越来越小

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230628-1687922957781)

- 人生也是一样
	- 有的时候一切顺利
	- 有的时候沟沟坎坎
- 爱尔兰裔新美国人 
	- 沃森也一样
- 正当他 
	- 一统 超市收银机市场
	- 并控制维修市场
	- 垄断二手市场
	- 顺风顺水的时候
- 麻烦也在向他靠近
- 什么麻烦呢？🤔
- 下次再说？👋🏻