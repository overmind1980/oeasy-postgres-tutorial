---
show: step
version: 1.0
enable_checker: true
---

#   IN关键字_从元组中选择   

##  回忆

- 上次了解了Flint
	- 是托拉斯之父
	- 能让这些各自为政的企业真正联合起来 
	- 但是联合起来之后往往是空架子 
	- 想要他们 成为有机整体 
	- 还需要深度整合 


- Flint不但坚信"越大越好"
	- 还相信"花样越多越好"
- 联合了三家当时的数字化公司
	- 第一家 做打卡闹钟 
	- 第二家 做计算尺 
	- 第三家 做打孔卡机械
	- 叫CTR
- 三样东西都有一个共同点
	- 处理信息
	- 企图用数字 统一度量衡

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230624-1687616096462)

- 1924年
	- CTR更名为IBM
	- 一个放眼全球为商业用途生产机器的公司
- 本次内容参考了《竞争者的垄断梦》
- 这就是商业领域里面的
	- 交集和并集
	- 与或运算
- 不过经常提到的是
	- 子交并补
	- 与或非
- 这如何理解呢？🤔

### 补集

- 排除运算

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687668162796)

- 关键字是EXCEPT

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687698212064)

- A排除B
	- A EXCEPT B

### EXCEPT

```
(SELECT 
    *
 FROM
    heroes)
EXCEPT
(SELECT 
    *
 FROM
    heroes
 WHERE
    name = '刘备')
;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687696107938)

- 补集和交集
	- 谁优先级更高呢？

### 优先级

- https://www.postgresql.org/docs/16/queries-union.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687696878999)

- 在没有括号的情况下
	- UNION 和 EXCEPT 都是从左到右
	- INTERSECT 优先级最高

- 有没有逻辑上的
	- EXCEPT 运算呢？

### 逻辑运算

```
SELECT 
    *
FROM
    heroes
WHERE
    NOT name = '刘备'
;
```

- 逻辑运算 NOT

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687697118915)

- 如何理解这个NOT呢？

### 逻辑运算NOT

```
SELECT 
    name,
    name = '刘备' AS is_liubei,
    NOT name = '刘备' not_liubei
FROM
    heroes
;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687697312096)

- 有了这个NOT 究竟该如何运算呢？

### NOT优先级

```
SELECT 
    *
FROM
    heroes
WHERE
    NOT name = '刘备'
    AND name = '关羽'
;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687697430012)

- 可以看到NOT
	- 是先和 name = '刘备'
	- 运算了
- 如果我想
	- 先进行AND运算
	- 再进行NOT运算
	- 应该如何呢?

### 括号优先级

```
SELECT 
    *
FROM
    heroes
WHERE
    NOT 
    (name = '刘备'
    AND 
    name = '关羽')
;
```

- 这应该如何理解呢？

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687697580123)

### 查看原理

```
SELECT 
    name,
    (name = '刘备'
    AND 
    name = '关羽') AS is_liu_guan,
    NOT 
    (name = '刘备'
    AND 
    name = '关羽') AS not_liu_guan
FROM
    heroes
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687697772271)

- 没有人同时
	- 既是刘备
	- 又是关羽

### 逻辑运算优先级总结

- 先非 NOT
- 后与 AND
- 再并 OR
- 有括号的要优先

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687698085280)


## 总结🤔

- 这次研究了集合的非集
	- EXCEPT 排除
- 对应的逻辑运算为
	- 非运算 NOT

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230625-1687698879796)

- 整体来说
	- NOT 是对于布尔值的否定
	- EXCEPT 是对于集合的排除
	- 这些都是 数字化时代的运算
- 除了Flint 手下的 这些数字化
	- 打孔卡记录
	- 时钟打卡
	- 计算尺
	- 之外
- 还有一个领域 诞生了
	- 收银机 领域
	- 诞生了 专业的收银机公司
	- 这是怎么做到的呢？ 
- 下次再说？👋🏻