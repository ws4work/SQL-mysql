# SQL-mysql


##convert转换属性
SELECT @col FROM @table_name
ORDER BY CONVERT(@col,SIGNED) ASC


##insert-select查询并插入
INSERT INTO @table_name1
SELECT @cols FROM @table_name2


##update-select查询并更新
UPDATE @table_name1
SET @table_name1.@col1 = (
SELECT DISTINCT @col2
FROM @table_name2
WHERE @conditions
)


##重新排列id
ALTER TABLE @table_name DROP `id`;
ALTER TABLE @table_name ADD `id` INT( 8 ) NOT NULL FIRST;
ALTER TABLE @table_name MODIFY COLUMN `id` INT( 8 ) NOT NULL AUTO_INCREMENT,ADD PRIMARY KEY(id); 


##查看某表全部列名
SELECT COLUMN_NAME FROM information_schema.COLUMNS
WHERE TABLE_NAME = '@table_name'
AND TABLE_SCHEMA = '@db_name';


##查看某数据库全部表名
SELECT TABLE_NAME from information_schema.TABLES
WHERE TABLE_SCHEMA='@db_name';


##查找重复数据
SELECT @col,count(*) AS count
FROM @table_name
GROUP BY @col
HAVING count > 1;

##case when统计计数
SELECT COUNT(1) AS count
,SUM(CASE WHEN @conditions THEN @value1 ELSE @value2 END) AS sum
FROM @table_name


