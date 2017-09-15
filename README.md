# SQL-mysql


##convert转换属性
<pre>
SELECT @col FROM @table_name
ORDER BY CONVERT(@col,SIGNED) ASC
</pre>


##insert-select查询并插入
<pre>
INSERT INTO @table_name1
SELECT @cols FROM @table_name2
</pre>

##update-select查询并更新
<pre>
UPDATE @table_name1
SET @table_name1.@col1 = (
SELECT DISTINCT @col2
FROM @table_name2
WHERE @conditions
)
</pre>

##重新排列id
<pre>
ALTER TABLE @table_name DROP `id`;
ALTER TABLE @table_name ADD `id` INT( 8 ) NOT NULL FIRST;
ALTER TABLE @table_name MODIFY COLUMN `id` INT( 8 ) NOT NULL AUTO_INCREMENT,ADD PRIMARY KEY(id); 
</pre>

##查看某表全部列名
<pre>
SELECT COLUMN_NAME FROM information_schema.COLUMNS
WHERE TABLE_NAME = '@table_name'
AND TABLE_SCHEMA = '@db_name';
</pre>

##查看某数据库全部表名
<pre>
SELECT TABLE_NAME from information_schema.TABLES
WHERE TABLE_SCHEMA='@db_name';
</pre>

##查找重复数据
<pre>
SELECT @col,count(*) AS count
FROM @table_name
GROUP BY @col
HAVING count > 1;
</pre>

##case when统计计数
<pre>
SELECT COUNT(1) AS count
,SUM(CASE WHEN @conditions THEN @value1 ELSE @value2 END) AS sum
FROM @table_name
</pre>

