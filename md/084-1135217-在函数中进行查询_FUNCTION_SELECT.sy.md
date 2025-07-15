---
show: step
version: 1.0
enable_checker: true
---

#  嵌套查询_根据聚合函数结果_进行查询
 

##  回忆

- 上次定义了函数
	- 并且调用了函数
	- 可以得到一个查询结果
	- 但是结果都是单行单列
	- 而且和查询无关
- 可以将查询结果 作为返回值吗？🤔

### 使用查询

```
CREATE FUNCTION one() RETURNS integer AS $$
    SELECT 1 AS result;
$$ LANGUAGE SQL;

SELECT one();
```

- 执行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696320407423)

### 查询具体表格

```
\c sanguo

CREATE FUNCTION max_fight() RETURNS integer AS $$
    SELECT max(fight) FROM heroes AS result;
$$ LANGUAGE SQL;

SELECT max_fight();
```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696320490796)

### 返回一行元素

```
\c sanguo

CREATE FUNCTION heroes() RETURNS heroes AS $$
    SELECT * FROM heroes AS result;
$$ LANGUAGE SQL;

SELECT heroes();
```

- 执行结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696320819939)

### 返回多行结果

```
\c sanguo
DROP FUNCTION test_func();

CREATE OR REPLACE FUNCTION test_func()
    RETURNS SETOF VARCHAR
    LANGUAGE plpgsql
    AS $$
    DECLARE
        var_nation TEXT;
    BEGIN
        var_nation := (SELECT nation FROM heroes WHERE name='刘备' LIMIT 1);
        RETURN QUERY SELECT name FROM heroes WHERE nation = var_nation;
    END; $$
    ;

SELECT * FROM test_func();
```

- 返回结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696334335148)

### 多列

```
\c sanguo
DROP FUNCTION test_func;
CREATE OR REPLACE FUNCTION test_func()  
RETURNS TABLE (id INTEGER,name VARCHAR) AS   
$$
BEGIN  
    RETURN QUERY   
    SELECT heroes.id,heroes.name   
    FROM heroes   
    WHERE nation = '蜀';
END; 
$$
LANGUAGE plpgsql;

SELECT * FROM test_func();
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696335157479)

### 引入递归

```
\c sanguo
DROP FUNCTION test_func;
CREATE OR REPLACE FUNCTION test_func()  
RETURNS TABLE (id INTEGER,name VARCHAR) AS   
$$
BEGIN  
    RETURN QUERY   
    SELECT heroes.id,heroes.name   
    FROM heroes   
    WHERE nation = (  
        SELECT nation   
        FROM heroes   
        WHERE heroes.name = '曹操'  
    );  
END; 
$$
LANGUAGE plpgsql;

SELECT * FROM test_func();
```

- 搜索结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696335063308)

- 可以引入变量并且根据参数进行搜索吗？

### 引入参数

```
\c sanguo
DROP FUNCTION test_func;
CREATE OR REPLACE FUNCTION test_func(nation_name VARCHAR)  
RETURNS TABLE (id INTEGER,name VARCHAR) AS   
$$
BEGIN  
    RETURN QUERY   
    SELECT heroes.id,heroes.name   
    FROM heroes   
    WHERE nation = nation_name;
END; 
$$
LANGUAGE plpgsql;

SELECT * FROM test_func('吴');
```

- 结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696335434107)

- 可以先根据武将查询到国家
- 然后得到国家内所有武将吗？

### 变量

- 在函数中通过查询结果对变量赋值

```
\c sanguo
DROP FUNCTION test_func;

CREATE OR REPLACE FUNCTION test_func(
    hero_name VARCHAR)  
    RETURNS TABLE (id INTEGER,name VARCHAR) AS   
    $$
        DECLARE
            nation_name VARCHAR(20);
        BEGIN  
            nation_name := (
                SELECT nation 
                FROM heroes 
                WHERE heroes.name = hero_name 
                LIMIT 1);
            RETURN QUERY   
                SELECT heroes.id,heroes.name   
                FROM heroes   
                WHERE nation = nation_name;
        END; 
    $$
LANGUAGE plpgsql;

SELECT * FROM test_func('孙权');
```

- 得到孙权政权所有武将

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696335836775)

- 还想要得到宝物应该怎么办？

### 得到宝物

```
DROP FUNCTION test_func;

CREATE OR REPLACE FUNCTION test_func(
    hero_name VARCHAR)  
    RETURNS TABLE (
        id INTEGER,
        name VARCHAR,
        items VARCHAR) AS   
    $$
        DECLARE
            nation_name VARCHAR(20);
        BEGIN  
            nation_name := (
                SELECT nation 
                FROM heroes 
                WHERE heroes.name = hero_name 
                LIMIT 1);
            RETURN QUERY   
                SELECT heroes.id,heroes.name,heroes.items   
                FROM heroes   
                WHERE nation = nation_name;
        END; 
    $$
LANGUAGE plpgsql;

SELECT * FROM test_func('孙权');
```

- 控制返回值类型
- 控制查询语句

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696336128405)

## 总结
- 这次熟悉了函数
	- 函数名
	- 参数列表
	- 返回值类型
	- 函数体
- heroes 表里面 有宝物
	- 这些宝物 是否都在 宝物表 里面呢？🤔
- 下次再说？👋🏻
