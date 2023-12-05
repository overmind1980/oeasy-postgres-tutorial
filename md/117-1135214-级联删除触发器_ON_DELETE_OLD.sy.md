---
show: step
version: 1.0
enable_checker: true
---

#    主键_外键_主表_从表_foreign_key_master_table       
 
##  回忆

- 上次了解了插入触发器
	- 定义了函数
	- 对于bill表每一条新插入的数据
	- 触发调用函数
- 对于stall表
	- 可以对于删除记录定义触发器吗？
	- 一旦删除了stall的档口数据
	- 就级联删除bill中档口相关的账单数据？

### 恢复初始


```
DROP DATABASE 
	chinese_food_city;

CREATE DATABASE
	chinese_food_city;
	
\c chinese_food_city

CREATE TABLE public.bill (
    ic_id character varying(10),
    dk_id character varying(10),
    deal_time timestamp without time zone,
    price numeric
);


CREATE TABLE public.stall (
    dk_id character varying(10),
    shop character varying(20),
    shop_owner character varying(20)
);



COPY public.bill (ic_id, dk_id, deal_time, price) FROM stdin;
ic2034123	dk1000234	2023-09-30 11:30:01	15
ic2052342	dk1001584	2023-09-30 11:33:03	30
ic2034123	dk1001584	2023-09-30 11:34:04	3
ic2033233	dk1003324	2023-09-30 11:36:23	20
ic2035678	dk1000436	2023-09-30 11:36:44	20
ic2034434	dk1001584	2023-09-30 11:37:51	25
ic1034139	dk1003324	2023-09-30 11:38:23	20
\.



COPY public.stall (dk_id, shop, shop_owner) FROM stdin;
dk1000436	饭是钢	胡小喵
dk1000234	兰州拉面	刘老根
dk1003324	煎饼虎头军	胡小喵
dk1001584	老家肉饼	刘老根
\.

```

- 需要将空格替换为\t	
	- :%s/    /\t/g
- 现在恢复到最初状态了

### 构建 触发器和函数

```

\c chinese_food_city

CREATE FUNCTION delete_related_bills() RETURNS TRIGGER AS $$
BEGIN
    DELETE FROM bill WHERE dk_id = OLD.dk_id;
    RETURN OLD;
END;
$$ LANGUAGE plpgsql;
 
CREATE TRIGGER delete_related_bills_trigger
BEFORE DELETE ON stall
FOR EACH ROW
EXECUTE FUNCTION delete_related_bills();

```

- 创建函数和触发器

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231006-1696561299677)

### 尝试删除

```
\c chinese_food_city

DELETE FROM
    stall
WHERE
    shop = '饭是钢'
;
```

- 执行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231006-1696563031583)

### 查询bill

```
SELECT
	*
FROM
	bill
;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231006-1696563113215)

- 触发器发生了作用
	- bill表还剩下一条记录

##  总结

- 这次创建了一个删除记录的触发器
	- 删除 档口 记录
	- 函数 作用是 删除档口相关的账单记录
- 如果我想在插入之前判断
	- 如果店铺存在 
		- 只插入账单
	- 如果店铺不存在
		- 插入账单和店铺 
- 这个需求可以做吗？🤔
- 下次再说？👋

