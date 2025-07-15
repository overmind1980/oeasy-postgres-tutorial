---
show: step
version: 1.0
enable_checker: true
---

#    主键_外键_主表_从表_foreign_key_master_table       
 
##  回忆

- 上次创建了各种视图
	- 带计算的
	- 基于聚合函数的
	- 基于视图的
- 但是不能直接往多表连接形成的视图里插数据
	- 说是要使用trigger
	- trigger是什么意思呢？🤔

### 语句块

```
DO $$ 
DECLARE
  name text;
BEGIN 
  name := 'PL/pgSQL';
  RAISE NOTICE 'Hello %!', name;
END $$;
```

- 声明了变量name
	- name text;
- 对变量name赋值
	- name := 'PL/pgSQL'
- 使用变量name输出
	- RAISE NOTICE 'Hello %!', name;

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696126887623)

- 可以利用变量完成查询
- 并将结果赋给变量
- 然后输出吗？

### 通过查询赋值

```
\c chinese_food_city

DO $MY_BLOCK$ 
DECLARE
  var_shop text;
  var_dk_id text;
BEGIN 
  var_shop := '兰州拉面';
  SELECT 
	stall.dk_id
  INTO
    var_dk_id
  FROM
	stall
  WHERE
	stall.shop = var_shop;
  RAISE NOTICE '档口id是: %!', var_dk_id;
END $MY_BLOCK$;
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696128401291)

- 在BLOCK外面 还可以使用变量吗？

### 作用域

```
\c chinese_food_city

DO $MY_BLOCK$ 
DECLARE
  var_shop text;
  var_dk_id text;
BEGIN 
  var_shop := '兰州拉面';
  SELECT 
	stall.dk_id
  INTO
    var_dk_id
  FROM
	stall
  WHERE
	stall.shop = var_shop;
  RAISE NOTICE '档口id是: %!', var_dk_id;
END $MY_BLOCK$;
RAISE NOTICE '档口id是: %!', var_dk_id;
```

- 运行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696128482816)

- 在BLOCK中DECLARE的变量
	- 只在BLOCK中可见
- 可以根据这个查询出来的var_dk_id删除吗？

### 删除

```
\c chinese_food_city

DO $MY_BLOCK$ 
DECLARE
  var_shop text;
  var_dk_id text;
BEGIN 
  var_shop := '兰州拉面';
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
END $MY_BLOCK$;
```

- 执行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696129061118)

- 具体删除了吗？

### 查询删除结果

```
\c chinese_food_city

SELECT DISTINCT
    bill.*
FROM
	bill
NATURAL JOIN
	stall
;
```

- 确实将兰州拉面的账单信息删除了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696129143562)

- 如何理解DO这一套东西呢？ 

### 匿名代码块

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231001-1696129204116)

- https://www.postgresql.org/docs/16/plpython-do.html

```
DO $$DECLARE r record;
BEGIN
    FOR r IN SELECT table_schema, table_name FROM information_schema.tables
             WHERE table_type = 'VIEW' AND table_schema = 'public'
    LOOP
        EXECUTE 'GRANT ALL ON ' || quote_ident(r.table_schema) || '.' || quote_ident(r.table_name) || ' TO webuser';
    END LOOP;
END$$;
```

- 上述代码
	- 遍历 pubplic方案中的 所有视图
	- 授权给 webuser

##  总结🤔

- 我们这次研究了 DO代码块
	- 声明变量、给变量赋值、使用变量
	- 这很像一个函数
	- SQL语句可以定义函数吗？
- 下次再说？👋

