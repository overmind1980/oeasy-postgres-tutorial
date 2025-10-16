---
show: step
version: 1.0
enable_checker: true
---

# 自增序列

### 回忆

- 上次了解了
	- 去重字段
	- 投影字段
- 去重字段
	- 不能重复
	- 投影字段选取其中的第一列
- 发现items表中
	- 只有一列没有重复
	- 为什么没有重复呢？

### 回忆创建

- 建items表的时候
	- id 的数据类型是 serial

```
CREATE TABLE items(
    id serial, 
    name VARCHAR(20),
    city VARCHAR(10),
    effects VARCHAR(30),
    value int
)
;
```

- 什么是serial呢？

### serial

- 搜索serial
	- 找到数据类型
	- https://www.postgresql.org/docs/16/datatype-numeric.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685868612502)

- 分成大中小 
	- 三种serial
- 这个词的词根来自于什么呢？

### serial 连续的

- serial
	- [ˈsɪəriəl]
	- 顺序排列的; 排成系列的; 连续的; 多次的; 
	- 以连续剧形式播出的; 连载的;
	- 串行的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685868941144)

- serial dilution
	- 连续稀释

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685869379162)

- serial killer
	- 连环杀手

- 词根来自于 
	- series

### series 系列

-  series
	- [ˈsɪəriːz]
	- 系列; 连续; 接连; 
	- (广播或电视上题材或角色相同的)系列节目;
	- (两队之间的)系列比赛; 串联;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685869533803)

-  series 
	- 连续剧
	- 系列电影
	- 系列小说

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685869731828)

- 词根来自*ser-

### *ser-

- 原始印欧词根的意思是“排队”

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685869855866)

###  serried 密集的

- serried
	- [ˈserid]
	- 密集的; (行列)密排的; 靠拢的

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685870569175)

### sort

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685870823818)

- sort
	-  [sɔːt]
	- 分好类
	- 排好序

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685870958097)

###  consort 

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685880953958)

- con-
	- 一起
- sort
	- 整合

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685880917393)

- consort 
	- [ˈkɒnsɔːt ]
	-(统治者的)配偶; 
	- 一组(演奏几世纪前音乐的乐师);
	- vi. 	厮混; 鬼混;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685881010094)

- consortium
	- [kənˈsɔːtiəm]
	- n. 	联盟; (合作进行某项工程的)财团，银团，联营企业

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685881099644)

### assort

- assort 
	- [ә'sɒ:t]
	- a- "to"
	- 分类; 协调；
	- 相配; 把…分级;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685881273273)

- assortative
	- [ə'sɔ:trtətɪv]
	- 分类的; 协调的; 
	- 协调; 相配的;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685881556516)

- assorted
	- [əˈsɔːtɪd]
	- adj. 	各色; 各种各样的; 整理好的
	- v. 	把…分级；把…归为一类; 
	- 协调；相配；交际;

- 分类分好了
	- 比例调配好了
		- 就是某种法术



###  sorcery 法术

- sorcery
	- [ˈsɔːsəri]
	- 法术

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685871862803)

- 这是什么巫术？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685871884628)

- 使用 法术的人
	- 就是 法师

### 男女巫

-  sorcerer 
	- [ˈsɔːsərə(r)]
	- (故事中的)术士，男巫，巫师

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685872328684)

- sorceress 
	- [ˈsɔːsərəs]
		- n. 	(故事中的)女术士，女巫，巫婆;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685872536904)

### 法术

- ensorcell 
	- [in'sɔ:səl]
	- vt. 	迷惑，盅惑，使着迷;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685873135497)

- sermon 
	- [ˈsɜːmən]
	- n. 	布道; 讲道; 冗长的说教

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685872811166)

- 让你入队
	- 今天有今天布道的方式

### dissertation 论文

- 以前指的是讨论或者辩论
	- 现在把这些长篇大论放到一起
		- 写出来

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685881799857)

- dissertation
	- [ˌdɪsəˈteɪʃn]
	- n. 	论文; 学位论文; 专题论文

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685881855448)


### assert

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685874705846)

-  assert
	- [əˈsɜːt]
	- 明确肯定; 断言; 坚持自己的主张; 
	- 表现坚定; 维护自己的权利(或权威); 生效;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685874878959)

- assertion 
	- [əˈsɜːʃn]
	- n. 	明确肯定; 断言; 
	- 声称; 使用; 主张;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685875065540)

- assert 肯定
	- 否定 怎么说呢？

### desert

-  desert
	- [ˈdezət]
	- n. 	沙漠; 荒漠; 荒原;
	- v. 	抛弃，离弃，遗弃(某人); 
	- 舍弃，离弃(某地方); 擅离(部队); 逃走;
	- 开小差; 废弃; 背离;
	- adj. 	不毛的; 沙漠的; 无人的;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685875284238)

-  desertion
	- [dɪˈzɜːʃən]
	- n. 	（违背法律或道义责任的）遗弃（尤指配偶）; 
	- 遗弃; 荒废; 放弃; 被离弃（或抛弃）状态;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685875428782)

- deserter
	- [dɪˈzɜːtə(r)]
	- n. 	逃兵; 开小差的人

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685875437204)

### insert 向内插入

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685874017047)

-  insert 
	-  [ɪnˈsɜːt , ˈɪnsɜːt]
	-  插入; 嵌入; (在文章中)添加，加插;
	-  n. 	(书报的)插页，广告附加页; 插入物; 添加物

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685874042113)

### 向外插出

- exsert
	- [ek'sә:t] 
	- 向外插入
	- 外露的; 使伸出; 突出的; 
	- 使突出; 抽出;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685874604040)

- exserted
	- [ekˈsɜːtɪd]
	- adj. [生物]伸出的，[生物]突出的
	- v. 使……伸出；使……突出

###  exert 发挥

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685882045236)

-  exert
	- [ɪɡˈzɜːt]
		- vt. 	发挥; 施加; 
		- 行使; 运用; 努力; 竭力;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685882157923)

## 总结

- 这次了解了serial的词源

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230604-1685882881510)

- serial 是一种数据类型
- 应该如何理解这种数据类型呢？🤔
- 下次再说？👋🏻