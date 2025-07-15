---
show: step
version: 1.0
enable_checker: true
---

#  嵌套查询_根据聚合函数结果_进行查询
 

##  回忆

- 上次了解了游标使用过程
	1. 定义游标
	2. 打开游标
	3. 遍历游标
	4. 关闭游标
- 可以将数值作为参数传入存储过程吗？🤔

### 使用参数

```
\c sanguo
CREATE OR REPLACE PROCEDURE test_proc(var_city TEXT)
    LANGUAGE plpgsql
    AS $$
    DECLARE
		var_items RECORD;
        cur_items CURSOR FOR
            SELECT name
            FROM items
            WHERE city = var_city;
    BEGIN
        OPEN cur_items;
        LOOP
            FETCH cur_items INTO var_items;
            EXIT WHEN NOT FOUND;
            RAISE NOTICE 'items: %', var_items.name;
        END LOOP;
        CLOSE cur_items;
    END;
    $$;

CALL test_proc('长沙');
```

- 最终结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696304455770)

- 可以接收参数传入
	- 存储过程 很像一个函数
- SQL语言可以创建函数吗？

### 查找帮助

- https://www.postgresql.org/docs/current/sql-createfunction.html

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696304601123)

- 具体怎么定义函数呢？

### 定义函数 
```
CREATE OR REPLACE FUNCTION add(
    integer, 
    integer
) RETURNS integer AS 
    'select $1 + $2;'
    LANGUAGE SQL
    IMMUTABLE
    RETURNS NULL ON NULL INPUT;

SELECT add(1,2);
```

- 执行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696305072578)

- 这是使用SQL语句方式定义的函数
	- 可以换一种定义方式吗?

### plpgsql

```
CREATE OR REPLACE FUNCTION add(
    a integer, 
    b integer
) RETURNS integer AS $$
    BEGIN
        RETURN a + b;
    END;
    $$ 
    LANGUAGE plpgsql;

SELECT add(1,2);
```

- 执行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696305905051)

- 再试着定义一个函数 

### 函数 

```
CREATE OR REPLACE FUNCTION increment(i integer) RETURNS integer AS $$
        BEGIN
                RETURN i + 1;
        END;
$$ LANGUAGE plpgsql;


SELECT increment(100);
```

- 自增函数

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696306008896)

- 定义函数有什么用吗？

### 调整公式

- 可能很多查询都要用到一组公式
- 但是这个公式如果修改的话
	- 很多地方都要修改
	- 想要一概全改

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231005-1696500808424)

- 通过函数定义
	- 就可以实现一改全改

## 总结

- 这次定义了函数
	- 并且调用了函数
	- 可以得到一个查询结果
	- 但是结果都是单行单列
	- 而且和查询无关
- 可以将查询结果 作为返回值吗？🤔
- 下次再说？👋🏻
