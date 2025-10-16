---
show: step
version: 1.0
enable_checker: true
---

#    主键_外键_主表_从表_foreign_key_master_table       
 
##  回忆

- 上次了解了 
	- 主表 master table
	- 从表 slave table
- 主表的主键 是从表的外键
	- 究竟什么是外键
	- foreign key？

### 回忆主键

- 为主表stall添加主键约束

```
ALTER TABLE
	stall
ADD CONSTRAINT
	stall_pk PRIMARY KEY(dk_id)
;
```

- 修改结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695891483290)

### 复合主键

- 为从表bill添加主键约束

```
ALTER TABLE
	bill
ADD CONSTRAINT
	bill_pk PRIMARY KEY(dk_id,ic_id,deal_time)
;
```

- 修改结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695891646169)

### 主键设置结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695892353963)

- 下面设置外键关系

### 设置外键 

```
ALTER TABLE
	bill
ADD CONSTRAINT
	bill_fk FOREIGN KEY(dk_id)
REFERENCES
	stall(dk_id)
;
```

- 修改结果

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695892590644)

- 设置了 外键有什么意义呢？

### 外键的意义

```
INSERT INTO
	bill(ic_id,dk_id,deal_time,price)
VALUES
	(1000,2000,'2023/1/30',40)
;
```

- 外键约束
	- 可以保证 每一个账单中的 dk_id
	- 都是在主表中存在的
	- 如果不存在 会报错

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695892951000)

### 减少冗余

- 所有档口的信息
	- 都存储在档口 表中
	- 节省空间
	- 一改全改

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695893036130)

##  总结🤔

- 这次研究了 外键约束
	- foreign key constraints

![图片描述](https://doc.shiyanlou.com/courses/uid1190679-20230928-1695893212858)

- 外键的作用
	- 减少冗余
	- 便于修改
	- 约束 数据 内容 
- 通过 
	- 主表的主键 
	- 从表的外键
- 可以有什么好处吗？
- 下次再说？👋

