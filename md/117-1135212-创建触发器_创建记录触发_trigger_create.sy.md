---
show: step
version: 1.0
enable_checker: true
---

#    主键_外键_主表_从表_foreign_key_master_table       
 
##  回忆

- 上次定义了函数FUNCTION
	- 参数是 shop的名字
	- 返回值类型是 void
	- 函数
		- 会根据shop得到dk_id
		- 再根据dk_id删除相关的bill
- 如果我想 再删除档口的时候
	- 将相关的账单记录 也都删除 
	- 应该怎么做呢？


### 查询触发器

- https://www.postgresql.org/docs/16/sql-createtrigger.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696167918271)

- 具体怎么触发呢？

### 构建 插入语句

```
\c chinese_food_city

INSERT INTO
	bill(ic_id,dk_id,deal_time,price)
VALUES
	('ic1034139', 
	 'dk1003324',
	 '2023-09-30 11:38:24',
	 '20')
;
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696168156556)

- 我希望每次 
	- 插入bill之后
		- 都调用一下add函数

### 创建触发器函数

- 触发器函数有固定的要求

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231002-1696249207818)

- 要求函数
	- 没有参数
	- 返回值为TRIGGER

### 定义函数和触发器

```
\c chinese_food_city

CREATE OR REPLACE FUNCTION insert_trigger() 
	RETURNS TRIGGER AS $$
		BEGIN
			RAISE NOTICE 'dk_id 是 %',NEW.dk_id;
			RETURN NEW;
		END;
	$$ LANGUAGE plpgsql;

DROP TRIGGER  IF EXISTS 
	 bill_insert_trigger ON bill;
 
CREATE TRIGGER 
	bill_insert_trigger
BEFORE INSERT ON 
	bill
FOR EACH ROW
EXECUTE FUNCTION 
	insert_trigger();

```

- 执行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231002-1696250515334)
 

### 查看触发器

```
SELECT * FROM pg_trigger ;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231002-1696250465834)

- 插入的时候真的会触发吗？

### 触发效果

```
\c chinese_food_city

INSERT INTO
	bill(ic_id,dk_id,deal_time,price)
VALUES
	('ic1034139', 
	 'dk1003324',
	 '2023-09-30 11:38:24',
	 '20')
;
```

- 插入结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231002-1696251320726)

- 确实触发了相应的函数

##  总结🤔

- 这次了解了插入触发器
	- 定义了函数
	- 对于bill表每一条新插入的数据
	- 触发调用函数
- 对于stall表
	- 可以对于删除记录定义触发器吗？
	- 一旦删除了stall的档口数据
	- 就级联删除bill中档口相关的账单数据？
- 下次再说？👋

