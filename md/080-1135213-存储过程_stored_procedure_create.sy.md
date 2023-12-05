---
show: step
version: 1.0
enable_checker: true
---

#  嵌套查询_根据聚合函数结果_进行查询
 

##  回忆

- 上次深入了 SELECT 查询
	- 嵌套
		- 不止 一层嵌套
		- 可以是 多层嵌套
		- 查询 总是从 内层嵌套开始
		- 一层层 向外 最后得到 想要的结果
	- IN 关键字 
		- 查询的结果 可能是 元组集合
		- 可以使用IN 替代 = 完成查询
- 这一层层嵌套实在有点复杂
- 能否分步来操作
- 一步步得到相关的结果？🤔

### 尝试存储过程

```
\c sanguo
CREATE OR REPLACE PROCEDURE test_proc()
LANGUAGE plpgsql
AS $$
DECLARE
    var_nation TEXT;
BEGIN
    SELECT nation
    INTO var_nation 
    FROM heroes
    WHERE name='刘备'
    LIMIT 1;
    RAISE NOTICE 'nation: %',var_nation ;
END; $$
;
CALL test_proc();

```

- 查询结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231002-1696258647105)

- 什么是存储过程呢？

### 存储过程

- stored procedure
	- 存储好的过程

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696298070618)

- 过程存储好之后
	- 只需要调用就行了

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20231003-1696300802858)

### 存储过程结构

```
create [or replace] procedure procedure_name(parameter_list)
language plpgsql
as $$
declare
-- variable declaration
begin
-- stored procedure body
end; $$
```

- 声明变量
- 定义具体过程体

```
create or replace procedure transfer(
   sender int,
   receiver int, 
   amount dec
)
language plpgsql    
as $$
begin
    -- subtracting the amount from the sender's account 
    update accounts 
    set balance = balance - amount 
    where id = sender;

    -- adding the amount to the receiver's account
    update accounts 
    set balance = balance + amount 
    where id = receiver;

    commit;
end;$$
```

- 得到`蜀`了之后
	- 如何得到更多的武将呢？


## 总结🤔

- 这次存储过程
	- stored procedure
	- 把需要处理的流程存储好 然后调用执行
	- 存储过程能够遍历结果集吗？？🤔
- 下次再说？👋🏻
