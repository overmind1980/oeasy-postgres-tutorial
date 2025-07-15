---
show: step
version: 1.0
enable_checker: true
---

#    主键_外键_主表_从表_foreign_key_master_table       
 
##  回忆

- 上次研究了 DO代码块
	- 声明变量、给变量赋值、使用变量
	- 这很像一个函数
	- SQL语句可以定义函数吗？

### 定义函数

```
\c chinese_food_city

CREATE OR REPLACE FUNCTION add(
	IN p_a integer,
	IN p_b integer,
	OUT p_sum integer
)
    AS 
	$BODY$ 
		BEGIN
			p_sum:= p_a + p_b;  -- 进行加法运算，并将计算结果赋值给输出的参数p_sum
		END;
	$BODY$ 
    LANGUAGE 'plpgsql'			-- 指定函数的程序语言
    VOLATILE					-- 优化器不进行优化
    RETURNS NULL ON NULL INPUT; -- 当传入参数含有null时返回null

SELECT add(1,2)
```

- 最后一句是函数的调用

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696167873675)

- 可以定义操作数据的函数吗？

### 定义函数

```
\c chinese_food_city

CREATE OR REPLACE FUNCTION delete_bill_by_shop(
	var_shop character varying(10)
)
RETURNS void AS $$
DECLARE
var_dk_id TEXT;
BEGIN
	SELECT 
		stall.dk_id
	INTO
		var_dk_id
	FROM
		stall
	WHERE
		stall.shop = var_shop;
	RAISE NOTICE '档口id是: %!', var_dk_id;

	DELETE 
	FROM
		bill
	WHERE
		bill.dk_id = var_dk_id;

END;
$$ LANGUAGE plpgsql;


```

- 定义结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696131443357)

### 查看函数

```
\df
```


- 查看结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696131473439)

- 如何 查询函数定义详情

### 查询函数定义详情

```
\sf delete_bill_by_shop
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696131988404)

- 函数定义了之后如何调用呢？

### 调用函数

```
SELECT delete_bill_by_shop('老家馅饼');
```

- 调用结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696166754977)

- 想办法恢复到美食城的初始状态

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

- 现在恢复到最初状态了

##  总结🤔

- 这次定义了函数FUNCTION
	- 参数是 shop的名字
	- 返回值类型是 void
	- 函数
		- 会根据shop得到dk_id
		- 再根据dk_id删除相关的bill
- 如果我想 再删除档口的时候
	- 将相关的账单记录 也都删除 
	- 应该怎么做呢？
- 下次再说？👋

