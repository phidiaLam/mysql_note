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
    ）[ENGINE=<储存引擎>] [CHARSET=<编码>]
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
    SELECT <列名>, <列名>, ...
    FROM <表名>, <表名>...
    ORDER BY <列名> [ASC|DESC], [<列名>] [ASC|DESC]
    ```
    `默认为ASC升序`
- GROUP BY分组
    按照group by的东西进行分组归纳
    ```
    SELECT <列名>, <列名>, ..., 
    FROM <表名>
    GROUP BY <列名>;
    ```
    - WITH ROLLUP
        可以实现在分组统计数据基础上再进行相同的统计（SUM,AVG,COUNT…）
        加在GROUP BY后面
    - coalesce(<列名>, <新命名（如：总数）>)
-  JOIN连接的使用
    - INNER JOIN（内连接,或等值连接）：获取两个表中字段匹配关系的记录。
    - LEFT JOIN（左连接）：获取左表所有记录，即使右表没有对应匹配的记录。
    - RIGHT JOIN（右连接）： 与 LEFT JOIN 相反，用于获取右表所有记录，即使左表没有对应匹配的记录。
    ```
    SELECT <表指代.列名>，<表指代.列名>...
    FROM <表名> <表指代> (INNER JOIN | LEFT JOIN | RIGHT JOIN)
    ON <条件>
    ```
- NULL值处理
    在WHERE后条件：
    - IS NULL: 当列的值是 NULL,此运算符返回 true
    - IS NOT NULL: 当列的值不为 NULL, 运算符返回 true
    - <=>: 比较操作符（不同于 = 运算符），当比较的的两个值相等或者都为 NULL 时返回 true
- 正则表达式
    ```
    SELECT <列名> FROM <表名> WHERE <列名> REGEXP <正则表达式>;
    ```
- 事务
    [菜鸟教程](https://www.runoob.com/mysql/mysql-transaction.html)
- ALTER 命令
    修改数据表名或者修改数据表字段
    - 删除，添加或修改表字段
    ```
    ALTER TABLE <表名> DROP|ADD <数据> <位置>;
    位置可以是 FIRST 或者 AFTER <数据>
    ```
    - 修改字段类型及名称
    MODIFY修改约束 CHANGE修改类型
    ```
    ALTER TABLE <表名> MODIFY c <类型>;
    ```
    - 修改字段默认值
    ```
    ALTER TABLE <表名> 
    -> MODIFY <数值> BIGINT NOT NULL DEFAULT <数值>;
    ```
    - 修改表类型
    ```
    ALTER TABLE <表名> ENGINE = <表类型>;
    ```
    - 修改表名
    ```
    ALTER TABLE <旧表名> RENAME TO <新表名>;
    ```
- 索引
    [cnblog](https://www.cnblogs.com/nananana/p/10387720.html)
- 临时表
    当前连接课件，关闭后自动销毁
    - 创建临时表
    ```
    CREATE TEMPORARY TABLE <临时表名> （
                                      <表内容>
                                      ）
    ```
    - 删除临时表
    ```
    DROP TABLE <临时表名>
    ```
- 复制表
    - 第一种方法
    ```
    SHOW CREATE TABLE <源表名> \G;
    
    CREATE TABLE <新表名> （
    <与源表结构一致>
    ）
    
    INSERT INTO <新表名> (<表头>...)
    SELECT <表头>...
    FROM <源表名>
    ```
    - 第二种方法
    ```
    CREATE TABLE <新表名> LIKE <源表名>;
    INSERT INTO <新表名> SELECT * FROM <源表名>;
    ```
