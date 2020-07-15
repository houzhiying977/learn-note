<!-- TOC -->

- [操作数据库](#操作数据库)
- [操作数据表](#操作数据表)
- [修改数据表](#修改数据表)
- [操作数据表中的记录](#操作数据表中的记录)
- [操作数据库](#操作数据库-1)
- [操作数据表](#操作数据表-1)
- [修改数据表](#修改数据表-1)
- [操作数据表中的记录](#操作数据表中的记录-1)

<!-- /TOC -->

## 操作数据库
- 创建数据库
```
CREATE {DATABASE | SCHEMA} [IF NOT EXISTS] db_name [DEFAULT] CHARACTER SET [=] charset name
```
- 查看数据库信息
```
SHOW CREATE DATABASE db_name;
```
- 更改数据库信息
```
ALTER {DATABASE | SCHEMA} db_name [DEFAULT] CHARACTER SET [=] charset name;
```
- 删除数据库
```
DROP {DATABASE | SCHEMA} [IF EXISTS] db_name
```
## 操作数据表
- 创建数据表
```
CREATE TABLE [IF NOT EXISTS] table-name(
    column-name data_type,
    ...
);
```
- 查看数据表结构
```
SHOW COLUMNS FROM tbl-name;
```
- 插入记录
```
INSERT [INTO] tbl_name [(col_name,...)] VALUES(val,...);
```
- 查找记录
```
SELECT * FROM tbl_name;
```
- 添加单列
```
ALTER TABLE tbl_name ADD [COLUMN] col_name column_definition [FIRST | AFTER col_name];
```
- 删除列
```
ALTER TABLE tbl_name DROP [COLUMN] col_name;
```
## 修改数据表
- 添加主键约束
```
ALTER TABLE tbl_name ADD [CONSTRAINT [symbol]] PRIMARY KEY [index_type] (index_col_name);
```
- 删除主键约束
```
ALTER TABLE tbl_name DROP PRIMARY KEY;
```
- 添加唯一约束
```
ALTER TABLE tbl_name ADD [CONSTRAINT [symbol]] UNIQUE[index_type] (index_col_name,...);
```
- 删除唯一约束
```
ALTER TABLE tbl_name DROP INDEX index_col_name;
```
- 添加外键
```
ALTER TABLE tbl_name ADD [CONSTRAINT [symbol]] FOREIGN KEY [index_type] (index_col_name,...) REFERENCES tbl_name1 (index_col_name1,...);
```
- 删除外键
```
ALTER TABLE tbl_name DROP FOREIGN KEY fk_symbol;
```
- 添加默认约束
```
ALTER TABLE tbl_name ALTER [CONSTRAINT [symbol]] index_col_name SET DEFAULT val;
```
- 删除默认约束
```
ALTER TABLE tbl_name ALTER [CONSTRAINT [symbol]] index_col_name DROP DEFAULT;
```
- 数据表重命名
```
1. ALTER TABLE tbl_name RENAME [TO|AS] new_tab_name;
2. RENAME TABLE tbl_name TO new_tab_name;
```
- 字段重命名(包括位置)       
```
ALTER TABLE tbl_name CHANGE [COLUNM] old_col_name  new_col_name column_definition [FIRST | AFTER col_name];
```
- 字段重定义(包括位置)
```
ALTER TABLE tbl_name MODIFY [COLUNM] col_name column_definition [FIRST | AFTER col_name];
```
## 操作数据表中的记录
- 插入记录
```
1. INSERT [INTO] tbl_name [(col_name,...)] {VALUES | VALUE} ({expr | DEFALUT},...),();
2. INSERT [INTO] tbl_name SET col_name={expr | DEFALUT},...;
3. INSERT [INTO] tbl_name [(col_name,...)] SELECT ...;
```
- 单表更新
```
UPDATE [LOW_PRIORITY] [IGNOGE] tbl_name SET col_name1={expr | DEFALUT} [,col_name2={expr | DEFALUT}]...[WHERE condition];
```
- 单表删除
```
DELETE FROM tbl_name [WHERE condition];
```
- 查找
```
SELECT select_expr[,select_expr...]
[
    FROM table_references
    [WHERE condition]
    [GROUP BY {col_name | position} [ASC | DESC],...]
    [HAVING condition]
    [ORDER BY {col_name | expr | position} [ASC|DESC],...]
    [LIMIT {[offset,] row_count | row_count OFFSET offset}]
];
```
title: mysql数据库
tags: mysql
notebook: mysql
---

## 操作数据库
- 创建数据库
```
CREATE {DATABASE | SCHEMA} [IF NOT EXISTS] db_name [DEFAULT] CHARACTER SET [=] charset name
```
- 查看数据库信息
```
SHOW CREATE DATABASE db_name;
```
- 更改数据库信息
```
ALTER {DATABASE | SCHEMA} db_name [DEFAULT] CHARACTER SET [=] charset name;
```
- 删除数据库
```
DROP {DATABASE | SCHEMA} [IF EXISTS] db_name
```
## 操作数据表
- 创建数据表
```
CREATE TABLE [IF NOT EXISTS] table-name(
    column-name data_type,
    ...
);
```
- 查看数据表结构
```
SHOW COLUMNS FROM tbl-name;
```
- 插入记录
```
INSERT [INTO] tbl_name [(col_name,...)] VALUES(val,...);
```
- 查找记录
```
SELECT * FROM tbl_name;
```
- 添加单列
```
ALTER TABLE tbl_name ADD [COLUMN] col_name column_definition [FIRST | AFTER col_name];
```
- 删除列
```
ALTER TABLE tbl_name DROP [COLUMN] col_name;
```
## 修改数据表
- 添加主键约束
```
ALTER TABLE tbl_name ADD [CONSTRAINT [symbol]] PRIMARY KEY [index_type] (index_col_name);
```
- 删除主键约束
```
ALTER TABLE tbl_name DROP PRIMARY KEY;
```
- 添加唯一约束
```
ALTER TABLE tbl_name ADD [CONSTRAINT [symbol]] UNIQUE[index_type] (index_col_name,...);
```
- 删除唯一约束
```
ALTER TABLE tbl_name DROP INDEX index_col_name;
```
- 添加外键
```
ALTER TABLE tbl_name ADD [CONSTRAINT [symbol]] FOREIGN KEY [index_type] (index_col_name,...) REFERENCES tbl_name1 (index_col_name1,...);
```
- 删除外键
```
ALTER TABLE tbl_name DROP FOREIGN KEY fk_symbol;
```
- 添加默认约束
```
ALTER TABLE tbl_name ALTER [CONSTRAINT [symbol]] index_col_name SET DEFAULT val;
```
- 删除默认约束
```
ALTER TABLE tbl_name ALTER [CONSTRAINT [symbol]] index_col_name DROP DEFAULT;
```
- 数据表重命名
```
1. ALTER TABLE tbl_name RENAME [TO|AS] new_tab_name;
2. RENAME TABLE tbl_name TO new_tab_name;
```
- 字段重命名(包括位置)       
```
ALTER TABLE tbl_name CHANGE [COLUNM] old_col_name  new_col_name column_definition [FIRST | AFTER col_name];
```
- 字段重定义(包括位置)
```
ALTER TABLE tbl_name MODIFY [COLUNM] col_name column_definition [FIRST | AFTER col_name];
```
## 操作数据表中的记录
- 插入记录
```
3. INSERT [INTO] tbl_name [(col_name,...)] {VALUES | VALUE} ({expr | DEFALUT},...),();
4. INSERT [INTO] tbl_name SET col_name={expr | DEFALUT},...;
5. INSERT [INTO] tbl_name [(col_name,...)] SELECT ...;
```
- 单表更新
```
UPDATE [LOW_PRIORITY] [IGNOGE] tbl_name SET col_name1={expr | DEFALUT} [,col_name2={expr | DEFALUT}]...[WHERE condition];
```
- 单表删除
```
DELETE FROM tbl_name [WHERE condition];
```
- 查找
```
SELECT select_expr[,select_expr...]
[
    FROM table_references
    [WHERE condition]
    [GROUP BY {col_name | position} [ASC | DESC],...]
    [HAVING condition]
    [ORDER BY {col_name | expr | position} [ASC|DESC],...]
    [LIMIT {[offset,] row_count | row_count OFFSET offset}]
];
```
