- 创建数据库
    ```
    CREATE DATABASE <数据库名>
    ```
- 创建用户权限数据库
    ```
    mysqladmin -u root 0p create <数据库名>
    ```
- 删除数据库
    ```
    drop database <数据库名>
    ```
- 选择数据库
    ```
    use <数据库名>
    ```
- 数据类型
    [菜鸟教程](https://www.runoob.com/mysql/mysql-data-types.html)
- 创建数据表
    ```
    CREATE TABLE <数据表>（
        <列名> <列类型> <属性[AUTO_INCREMENT：自增][NOT NULL:不为空]>
        ...
    ）ENGINE=<储存引擎> CHARSET=<编码>
    ```
    `PRIMARY KEY(列名字)` 主键
- 删除数据表
    `DROP TABLE <数据表>`
- 插入数据
    ```
    INSERT INTO <数据表> ( <列名1>, <列名2>,...<列名n> )
                        VALUES
                        ( <数值1>, <数值2>,...<数值n> )，
                        ...;
    ```
    如果全填可省略表头，自增填写0或者null
    一次性添加多行可括号多行数值
- 查询数据
    ```
    SELECT <列名>,<列名>...（*代替全部）
    FROM <表名>...
    [WHERE <条件>]
    [LIMIT <返回的记录数>][ OFFSET <数据偏移量（默认为0）>]
    ```
- WHERE子句
    ```
    SELECT <列名>,<列名>...
    FROM <表名>...
    [WHERE [BINARY：区分大小写] <条件> [AND|OR] <条件>]
    ```
- UPDATE更新
    ```
    UPDATE <表名> SET <列名>=<数据>, <列名>=<数据>...
    [WHERE <条件>]
    ```
- DELETE语句
    ```
    DELETE FROM <表名> [WHERE <条件>]
    ```
- LIKE子句
    匹配字符
    ```
    SELECT <列名>, <列名>,...
    FROM <表名>
    WHERE <列名> LIKE <列名>=<数值> [AND|OR] <列名>=<数值>
    ```
    `数值：比如%COM` 匹配所有以COM结尾
- UNION操作符
    删除表中重复数据
    ```
    SELECT <列名>, <列名>, ... 
    FROM <表名>
    [WHERE <条件>]
    UNION [ALL | DISTINCT]
    SELECT <列名>, <列名>, ... 
    FROM <表名>
    [WHERE <条件>];
    ```
    ```
    ALL:包括重复数据
    DISTINCT:不包括重复数据，默认可省略
    ```
- ORDER BY排序
    ```
    SELECT field1, field2,...fieldN FROM table_name1, table_name2...
    ORDER BY field1 [ASC [DESC][默认 ASC]], [field2...] [ASC [DESC][默认 ASC]]
    ```
