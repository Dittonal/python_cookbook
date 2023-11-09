# 1.6  本章练习
    特别说明：由于本书选择使用的是MySQL，正文内容也是以MySQL的语法作为主体，所以本书所有习题都是针对MySQL而言。
## 一、单选题
  1. 下面选项中，不属于DBMS的是（ ```A ）。
    ```A. SQL                                     B. MySQL
    C. SQL Server                               D. Oracle
    分析：
    SQL是语言，MySQL、SQL Server、Oracle才是DBMS。
  2. 下面选项中，属于非关系型DBMS的是（  D ）。
    ```A. MySQL                                   B. SQL Server
    C. Oracle                                    D. MongoDB
  3. 下面有关数据库的说法中，正确的是（  C ）。
    ```A. MySQL是非关系型DBMS
    B. MySQL是一门语言
    C. MySQL是使用最广泛的开源DBMS
    D. MySQL、SQL Server和Oracle的语法是完全一样的
  4. 下面数据库系统中，应用最广泛的是（  C ）。
    ```A. 分布型数据库                           B. 逻辑型数据库
    C. 关系型数据库                           D. 层次型数据库
## 二、问答题
  1. 常用的关系型DBMS和非关系型DBMS都有哪些？请分别列举最常见的几个。
    答案：
    （1）关系型DBMS：MySQL、SQL Server、Oracle、PostgreSQL。
    （2）非关系型DBMS：MongoDB、Redis。




# 2.4  本章练习
## 一、单选题
  1. SQL语言又被称为（  C ）。
    ```A. 结构化定义语言                           B. 结构化控制语言
    C. 结构化查询语言                           D. 结构化操纵语言
    分析：
    SQL，指的是“Structured Query Language（结构化查询语言）”。
  2. 每一条SQL语句的结束符是（  C ）。
    ```A. 句号                                     B. 逗号
    C. 分号                                     D. 问号
  3. 下面关于SQL的说法中，不正确的是（  ```A ）。
    ```A. SQL语句中的所有关键字必须大写
    B. 每一条SQL语句应该以英文分号结尾
    C. 库名、表名和列名的命名不能是SQL关键字
    D. 库名、表名和列名的命名只能使用英文字母、数字和下划线
    分析：
    A中，对于关键字来说，SQL是不区分大小写的。
  4. 如果给某一列进行命名，下面合法的命名是（  B ）。
    ```A. product-name                               B. product_name
    C. product+name                               D.$productname
    分析：
    在给库、表、列等命名时，我们只能使用英文字母（大小写都可）、数字、下划线（_）这3种。
  5. 下面不属于数字类型的是（  B ）。
    ```A. decimal                                  B. enum
    C. bigint                                    D. float
    分析：
    B中，enum属于字符串类型。
  6. 下面不属于字符串类型的是（  ```A ）。
    ```A. float                                     B. char
    C. blob                                     D. varchar
    分析：
    A中，float属于数字类型。
  7. 下面不属于时间日期类型的是（  C ）。
    ```A. date                                     B. year
    C. decimal                                  D. timestamp
    分析：
    C中，decimal属于数字类型。
  8. 下面选项中，可以用于注释多行内容的方式是（  B ）。
    ```A. -- 注释内容
    B. /*注释内容*/
    C. # 注释内容
    D. /注释内容/
  9. 如果表的某一列的取值是不固定长度的字符串，最适合使用的类型是（  B ）。
    ```A. char                                B. varchar
    C. nchar                               D. int
## 二、简答题
  1. 请简单说一下MySQL的数据类型都有哪些？
    答案：
    数字（整数、浮点数、定点数）、字符串、日期时间、二进制。


# 3.7  本章练习
## 一、单选题
  1. 如果把一张表看成是一个类，那么（  C ）就相当于表的属性。
    ```A. 行                                 B. 记录
    C. 列                                 D. 数值
    分析：
    “行”和“记录”是一个意思，而“列”和“字段”是一个意思。
  2. 在MySQL中，我们通常使用（  ```A ）来表示一个字段没有值或缺值。
    ```A. NULL                               B. EMPTY
    C. 0                                  D. ""
  3. 在MySQL中，select语句执行的结果是（  C ）。
    ```A. 数据库                             B.基本表
    C. 临时表                             D. 数据项
  4. 在MySQL中，我们可以使用（  ```A ）关键字来过滤查询结果中的重复行。
    ```A. distinct                              B. limit
    C. like                                  D. in
  5. where age between 20 and 30表示年龄在20~30之间，且（  ```A ）。
    ```A. 包含20和30                        B. 不包含20和30
    C. 包含20但不包含30                  D. 不包含20但包含30
  6. 对于limit 5, 10来说，它表示获取的是（  D ）。
    ```A. 第5~10条记录                      B. 第5~15条记录
    C. 第6~11条记录                      D. 第6~15条记录
    分析：
    对于limit start,n来说，start表示开始位置，n表示获取n条数据。limit 5,10表示从查询结果中的第5条记录开始（不包括第5条记录），共截取10条记录。
  7. 在查询商品售价price时，其结果按售价降序排列，正确的方式是（ C ）。
    ```A. order by price                       B. order by price asc
    C. order by price desc                   D. order by price limit
    分析：
    对于升序排列来说，asc是可以省略的。但是对于降序来说，desc是不可以省略的。
  8. 下面有关别名的说法中，正确的是（  B ）。
    ```A. 别名会替换真实表中的列名
    B. 如果别名中包含特殊字符，则必须使用引号括起来
    C. as关键字只能用于select子句
    D. 只能使用英文别名，不能使用中文别名
    分析：
    A中，别名并不会改变真实表中的列名。
    C中，as关键字不仅可以用于select子句，还可以用于其他子句，我们后续章节会详细介绍。
    D中，英文别名和中文别名都是可行的。
  9. 下面关于limit关键字的说法中，不正确的是（  B ）。
    ```A. limit子句通常需要放在select语句的最后面
    B. limit关键字可以限制从数据库中返回记录的行数
    C. limit 2,4表示获取查询结果的第3~6条记录
    D. limit 5表示获取查询结果的前5条记录
    分析：
    B中，limit关键字并不是限制从数据库中“返回”记录的行数，而是限制查询结果“显示”记录的行数，这两个是不一样的。
  10. 如果想要查询name字段不是NULL的所有记录，where子句应该写成（  C ）。
    ```A. where name != NULL;
    B. where name not null;
    C. where name is not null;
    D. where name ! NULL;
  11. 如果想要把product表中“product-name”这一列查询出来，正确的SQL语句是（  B ）。
    ```A. select product-name from product;
    B. select `product-name` from product;
    C. select 'product-name' from product;
    D. select "product-name" from product;
    分析：
    “product-name”中包含了特殊字符“-”，因此我们需要使用反引号（`）括起来。对于特殊列名，我们只能使用反引号，而不能使用单引号或双引号。
  12. 如果想要给product表的“name”这一列起一个别名“商品-名称”，正确的SQL语句是（  B  ）。
    ```A. select name as `商品-名称` from product;
    B. select name as "商品-名称" from product;
    C. select name as [商品-名称] from product;
    D. select name as 商品-名称 from product;
    分析：
    如果别名中包含特殊符号，我们必须使用英文引号括起来。英文单引号或英文双引号都可以，但是不允许是反引号。
  13. 下面有一段SQL代码，说法中正确的是（  C ）。
select distinct type, city
from product;
    ```A. distinct只会作用于type这一列
    B. distinct只会作用于city这一列
    C. distinct同时作用于type和city这两列
    D. 语法有误，运行报错
## 二、简答题
  1. 请简单说一下你对NULL值的理解。
    答案：
    NULL是代表该字段没有值，而不是代表该字段的值为0或''（空字符串）。
## 三、编程题
  1. 下面有一个学生表student（如表3-11所示），请写出对应的SQL语句。
表3-11  student
id	name	sex	grade	birthday	major
1	张欣欣	女	86	2000-03-02	计算机科学
2	刘伟达	男	92	2001-06-13	网络工程
3	杨璐璐	女	72	2000-05-01	软件工程
4	王明刚	男	80	2002-10-17	电子商务
5	张伟	男	65	2001-11-09	人工智能
  （1）查询成绩在80~100之间的学生基本信息。
  （2）查询所有学生基本信息，按照成绩从高到低排序。
  （3）查询成绩前3名的学生基本信息。
  （4）查询所有学生的name、grade、major这3列。
  （5）查询所有学生的name、grade这2列，并且给name起一个别名“姓名”，然后grade也要起一个别名“成绩”。
    答案：
（1）方式1：
select *
from student
where grade between 80 and 100;
    方式2：
select *
from student
where grade >= 80 and age <= 100;
  （2）
select *
from student
order by grade desc;
  （3）
select top 3 *
from student
order by grade desc;
  （4）
select name, grade, major
from student;
  （5）
select name as 姓名,
       grade as 成绩
from student;

# 本章练习
## 一、单选题
  1. 在MySQL中，having子句必须和（  C ）子句搭配一起使用。
    ```A. order by                            B. where
    C. group by                            D. limit
  2. 在分组条件（having子句）中，可以使用的聚合函数是（  D ）。
    ```A. count()                              B. sum()
    C. avg()                                D. 以上都可以
  3. 如果想要统计一个表有多少行数据，我们可以使用（  C  ）函数来实现。
    ```A. max()                               B. min()
    C. count()                              D. sum()
  4. 下面关于聚合函数的说法中，正确的是（  B ）。
    ```A. 聚合函数只能用于select子句，不能用于其他子句
    B. 聚合函数只会返回单个值
    C. 可以使用sum()函数来统计一个表有多少行
    D. count(列名)统计行数时，不会忽略值为NULL的行
    分析：
    A中，聚合函数只能用于select、order by、having这3种子句，而不能用于where、group by等其他子句。
    C中，统计一个表有多少行，应该使用count()函数。
    D中，count(列名)统计行数时，会忽略值为NULL的行。而count(*)统计行数时，才不会忽略值为NULL的行。
  5. 下面的说法中，正确的是（  B ）。
    ```A. where子句和having子句冲突，两者只能使用其中一个
    B. having子句必须要配合group by子句一起使用
    C. group by子句必须要配合having子句一起使用
    D. 可以使用where子句来设置每个分组的条件
    分析：
    A中，where子句和having子句是可以共存的。
    C中，group by子句不一定要配合having子句一起使用，但是having子句一定要配合group by子句一起使用。
    D中，应该是使用having子句来设置每个分组的条件。
  6. 对于select语句中的各种子句来说，正确的书写顺序是（  D ）。
    ```A. select→from→where→group by→having→limit→order by
    B. select→from→where→order by→group by→having→limit
    C. select→from→where→order by→limit→group by→having
    D. select→from→where→group by→having→order by→limit
  7. 如果想要查询选修了3门以上课程的学习信息（学号字段名为sno），正确的SQL语句是（  B ）。
    ```A. select * from course group by sno where count(*) > 3;
    B. select * from course group by sno having count(*) > 3;
    C. select * from course order by sno where count(*) > 3;
    D. select * from course order by sno having count(*) > 3;
## 二、问答题
  1. 请简单说一下where子句和having子句之间有什么区别？
    答案：
    （1）where子句是在分组之前对数据进行筛选，而having子句是对各个分组进行筛选。
    （2）where子句不能使用聚合函数，而having子句可以使用聚合函数。
    （3）where子句可以用于select、update、delete等语句中，但是having子句只能用于select语句。
  2. 请默写一下select语句中各个子句的顺序。
    答案：
select→from→where→group by→having→order by→limit


# 5.4  本章练习
## 一、单选题
  1. 如果一个查询的结果成为另一个查询的条件，这种查询方式被叫做（  D ）。
    ```A. 连接查询                           B. 父查询
    C. 自查询                             D. 子查询
  2. 如果想要使用like关键字来匹配单个字符，应该使用哪一个通配符？（  C ）
    ```A. %                                  B. *
    C. _                                   D. /
  3. 在MySQL中，与“not in”等价的操作符是（  D ）。
    ```A. =some                              B. <>some
    C. =all                                 D. <>all
  4. 当子查询返回多个值（多行数据）时，可以使用（  D ）关键字来处理。
    ```A. in                                  B. all
    C. some                               D. 以上都可以
  5. 当子查询的条件需要依赖父查询时，这类查询也叫做（  ```A ）。
    ```A. 关联子查询                         B. 内连接查询
    C. 全外连接查询                       D. 自然连接查询
  6. 下面关于模糊匹配的说法中，正确的是（  B ）。
    ```A. like关键字必须结合通配符一起使用
    B. rand()函数一般需要结合order by子句一起使用
    C. MySQL、SQL Server、Oracle实现随机查询的语法是一样的
    D. 子查询只能返回单个值，而不能返回多个值
    分析：
    A中，like关键字“一般”是集合通配符一起使用，但是并不代表它“必须”结合通配符一起使用。不使用通配符，也是没有问题的，比如下面的SQL语句。
select * 
from employee 
where name like '张';
    C中，MySQL、SQL Server、Oracle实现随机查询的语法是不一样的。
    D中，子查询可以返回单个值，也可以返回多个值。只是说标量子查询要求只能返回单个值而已。
## 二、问答题
  1. 如果子查询返回多个值（多行数据），我们可以使用哪些关键字来处理。
    答案：
    in、all、any、some。
  2. 请简单说一下普通子查询和关联子查询在执行上有什么区别？
    答案：
    在普通子查询中，子查询的查询条件与父查询无关。因此，子查询会在父查询处理之前执行。
    在关联子查询中，子查询的查询条件依赖于父查询中的某个值。因此，每当从父查询中检索一个新行时，都会重新对子查询进行求值，以供父查询使用。
## 三、编程题
  1. 下面有一个student表（如表5-5所示），请写出对应的SQL语句。
表5-5  student
id	name	sex	grade	birthday	major
1	张欣欣	女	86	2000-03-02	计算机科学
2	刘伟达	男	92	2001-06-13	网络工程
3	杨璐璐	女	72	2000-05-01	软件工程
4	王明刚	男	80	2002-10-17	电子商务
5	张伟	男	65	2001-11-09	人工智能
  （1）查询出所有姓“张”的学生记录。
  （2）查询出所有不是姓“刘”的学生记录。
  （3）查询出所有姓“张”并且名字长度是3个中文汉字的学生记录。
  （4）查询出姓名第2个字是“伟”的学生记录。
  （5）查询比“杨璐璐”生日晚的所有男生的姓名和生日。
  （6）查询比所有女生生日要晚的男生的姓名和生日。
  （7）查询和任意女生出生年份相同的男生的姓名和出生年份（注意是年份）。
  （8）查询不和任意女生出生年份相同的男生的姓名和出生年份（注意是年份）。
    （注：获取一个日期的年份，可以使用下一章介绍的year()函数）
    答案：
  （1）
select *
from student
where name like '张%';
  （2）
select *
from student
where name not like '刘%';
  （3）
select *
from student
where name like '张__';
    特别注意，上面“张__”中“张”后面是2个“_”。
  （4）
select *
from student
where name like '_伟%';
  （5）
select name, birthday
from student
where sex = '男' and birthday > (
    select birthday from student where name = '杨璐璐'
);
  （6）
select name, birthday
from student
where sex = '男' and birthday > all (
    select birthday from student where sex = '女'
);
  （7）
-- 方式1：使用“= any”
select name, year(birthday)
from student
where sex = '男' and year(birthday) = any(
    select year(birthday) from student where sex = '女'
);

-- 方式2：使用“in”
select name, year(birthday)
from student
where sex = '男' and year(birthday) in (
    select year(birthday) from student where sex = '女'
);
（8）
-- 方式1：使用“<>all”
select name, year(birthday)
from student
where sex = '男' and year(birthday) <> all (
    select year(birthday) from student where sex = '女'
);

-- 方式2：使用“not in”
select name, year(birthday)
from student
where sex = '男' and year(birthday) not in (
    select year(birthday) from student where sex = '女'
);

# 6.9  本章练习
## 一、单选题
  1. 如果想要获取字符串的长度，我们可以使用（  C ）函数来实现。
    ```A. count()                               B. len()
    C. length()                              D. sum()
  2. 如果想要同时去除字符串首尾的空格，我们可以使用（  ```A ）函数来实现。
    ```A. trim()                                 B. ltrim()
    C. concat()                               D. substring()
  3. 如果想要将price这一列转换为字符串类型，我们可以使用（  ```A ）来实现。
    ```A. cast(price as varchar)                    B. price + ''
    C. str(price)                              D. string(price)
  4. 如果想要返回指定日期时间是当月的第几天，我们可以使用（  C ）函数。
    ```A. month()                               B. monthname()
    C. dayofmonth()                           D. dayname()
  5. 如果有4名学生，有2个并列第1名，如果使用rank()函数添加排名，那么得到的名次是（  B ）。
    ```A. 1、2、3、4                              B. 1、1、3、4
    C. 1、1、2、3                              .D. 1、2、2、3
    分析：
    rank()函数是跳跃性的排名，比如有4名学生，有2个并列第1名，那么名次就是：1、1、3、4。
  6. 下面关于内置函数的说法中，正确的是（  C ）。
    ```A. 所有DBMS（包括MySQL、SQL Server等）的内置函数是一样的
    B. 内置函数需要用户自己定义之后才能使用
    C. 字符串函数只能用于字符串列，而不能用于数字列
    D. 可以使用floor()函数来实现向上取整
    分析：
    A中，不同DBMS的内置函数，有相同的部分，也有不同的部分。
    B中，内置函数可以直接调用，而不需要先定义。
    D中，floor()函数实现的是向下取整。


# 7.5  本章练习
## 一、单选题
  1. 如果想要删除表中所有数据（要求不能删除表），并且要求效率最高，此时应该使用（  ```A ）。
    ```A. truncate table语句                      B. drop table语句
    C. delete语句                             D. alter语句
    分析：
    B中，drop table语句效率是最高的，但是它会把表也给删除了。
  2. 在MySQL中，对表中数据的基本操作不包括（  ```A ）。
    ```A. create table语句                        B. insert语句
    C. delete语句                             D. update语句
    分析：
    A中，create table语句是对“表”的操作，而不是对“数据”的操作。
  3. 如果想要插入的记录中，主键值已经存在了，此时可以使用（  B ）来解决。
    ```A. insert语句                             B. replace语句
    C. delete语句                            D. select语句
  4. delete from product where type='文具';这一条语句表示（  B ）。
    ```A. 只能删除type='文具'的一条记录
    B. 删除type='文具'的所有记录
    C. 只能删除type='文具'的最后一条记录
    D. 以上说法都不对
  5. 往一张表插入数据时，如果不指定列名，那么下面说法正确的是（  ```A ）。
    ```A. 值的顺序必须要与表中列的顺序一致
    B. 值的顺序可以与表中列的顺序相反
    C. 值的顺序可以任意指定
    D. 以上说法都不对
  6. 下面关于数据操作语句的说法中，不正确的是（  D ）。
    ```A. 如果没有where子句，delete语句会把所有记录都删除
    B. 如果没有where子句，update语句会作用于整列中的所有记录
    C. insert语句插入数据时，可以不指定列名
    D. insert语句一次只能往表中插入一行记录
    分析：
    D中，insert语句可以插入一行记录，也可以插入多行记录。
  7. 如果想要将product表中id为“5”的商品的price增加10，那么正确的SQL语句是（  AB ）。（选2项）
    ```A.                                       B. 
      update product                           update product
      set price += 10                          set price = price + 10
      where id = 5;                            where id = 5;
    C.                                       D.
      alter table product                     alter table product
      set price += 10                          set price = price + 10
      where id = 5;                            where id = 5;
## 二、问答题
  1. 简单说明一下delete语句和truncate table语句之间的区别都有哪些？
    答案：
  （1）delete语句后面可以使用where子句，从而实现删除部分数据。而truncate table语句只能删除所有数据。
  （2）delete语句是逐行删除，truncate table语句是一次性删除，所以truncate table语句的性能更好。
  （3）使用delete语句删除数据之后，再次往表中添加记录时，自增字段的值为删除时该字段的最大值加1。使用truncate table语句删除数据之后，再次往表中添加记录时，自增字段的默认值被重置为1。




# 8.8  本章练习
## 一、单选题
  1. 在MySQL中，可以使用（  B ）语句创建一个数据库。
    ```A. create table                              B. create database
    C. create procedure                          D. create view
  2. 在MySQL中，可以使用（  ```A ）语句创建一个表。
    ```A. create table                              B. create database
    C. create procedure                          D. create view
  3. 在MySQL中，如果想要指定“lvye”作为当前数据库，正确的SQL语句是（  B ）。
    ```A. using lvye;                                B. use lvye;
    C. show lvye;                                D. in lvye;
  4. 如果想要将表名employee修改为staff，正确的SQL语句是（  C ）。
    ```A. update table employee rename to staff;
    B. update table staff rename to employee;
    C. alter table employee rename to staff;
    D. alter table staff rename to employee;
  5. 如果想要删除product这个表，正确的SQL语句是（  B ）。
    ```A. delete from product;
    B. drop table product;
    C. delete product;
    D. destroy product;
  6. 如果想要查看product这个表，正确的SQL语句是（  ```A ）。
    ```A. show create table product;
    B. display create table product;
    C. show table create product;
    D. show product;
## 二、编程题
  1. 下面是一个名为vegetable表的结构（如表8-4所示），请写出创建该表的SQL语句（不需要包括列的注释）。
表8-4  vegetable的结构
列名	类型	允许NULL	是否主键	注释
id	int	×	√	蔬菜编号
name	varchar2(5)	√	×	蔬菜名称
type	varchar2(5)	√	×	蔬菜类型
season	char(5)	√	×	上市季节
price	decimal(5, 1)	√	×	出售价格
rdate	date	√	×	入库时间（regist_date）

    答案：
create table vegetable
(
    id        int  primary key,
    name      varchar(10),
    type      varchar(10),
    season    varchar(5),
    price     decimal(10, 1),
    rdate     date
);

# 9.11  本章练习
## 一、单选题
  1. 如果想要为某一列添加主键，应该使用（  ```A ）关键字。
    ```A. primary key                         B. unique
    C. foreign key                          D. default
  2. 在MySQL中，每一列最多有（  B ）个default约束。
    ```A. 0                                  B. 1
    C. 2                                  D. 无数
  3. 下面说法中，不正确的是（  B ）。
    ```A. 一个表只能有一个主键
    B. 一个表可以有多个主键
    C. 一个表可以有多个外键
    D. 一个表可以有多个唯一键
    分析：
    一个表只能有一个主键，但是可以有多个外键，以及有多个唯一键。
  4. 下面关于检查约束（check）的说法中，正确的是（  ```A ）。
    ```A. 一个列只能设置一个检查约束
    B. 一个列可以设置多个检查约束
    C. 检查约束中只能写一个检查条件
    D. 不同列的检查约束条件必须不同
    分析：
    一个列只能设置一个检查约束，但是在该检查约束中可以有多个检查条件。此外，不同列的检查约束条件可以相同，这个是没有什么影响的。
  5. 下面关于各种约束的说法中，正确的是（  D ）。
    ```A. 默认情况下，列的默认值是0
    B. 所有表都必须有一个主键
    C. 主键允许有重复值
    D. 唯一键允许值为NULL
    分析：
    A中，默认情况下，列的默认值为NULL。
    B中，表不一定都要有一个主键。
    C中，主键具有非空性和唯一性。
  6. 下面关于主键的说法中，正确的是（  D ）。
    ```A. 只允许表中第一列创建主键
    B. 一个表允许有多个主键
    C. 主键的值允许是NULL
    D. 子表中设置了外键的列类型必须和父表中对应列的类型相同
    分析：
    A中，可以为表中任意一列创建主键。
    B中，一个表只能有一个主键。
    C中，主键的值不允许为NULL。
  7. 下面关于auto_increment属性的说法中，正确的是（  B ）。
    ```A. auto_increment属性可以用于浮点数列，也可以用于字符串列
    B. 一个表只能有一个auto_increment属性的列
    C. 设置了auto_increment属性的列，可以使用default属性来指定默认值
    D. auto_increment属性只能给主键列进行设置
    分析：
    A中，auto_increment属性只能用于整数列，而不能用于其他类型的列。
    C中，设置了auto_increment属性的列，不允许再使用default属性来指定默认值。
    D中，auto_increment属性可以给主键列进行设置，也可以给唯一键列进行设置。
  8. 如果表A和B建立外键关系，其中B依赖于A。如果想要把A和B这两个表都删除了，那么下面说法正确的是（  B ）。
    ```A. 只能删除A之后，才能删除B
    B. 只能删除B之后，才能删除A
    C. 删除A和B的顺序可以任意
    D. 以上说法都不对
## 二、问答题
  1. 请列举一下列的属性（约束）都有哪些？（至少5个）
    答案：
    主键、外键、唯一键、默认值、自动递增、条件检查、非空。
  2. 请简单说一下主键和唯一键之间的区别是什么？
    答案：
  （1）主键的值不能为NULL，而唯一键的值可以为NULL。
  （2）一个表只能有一个主键，但可以有多个唯一键。
  （3）主键可以作为外键，但是唯一键不可以。
## 三、编程题
  1. 请使用SQL语句创建一个学生表student，该表包含5列，其中列名、类型、注释如表9-2所示。
列的情况
列名	类型	注释
sno	int	学号
name	varchar(10)	姓名
sex	char(5)	性别
age	int	年龄
major	varchar(20)	专业
    其中，这些列的约束（即列属性）包括以下4个方面。
  （1）学号作为主键，并且是自动递增的，从1开始，增量为1。
  （2）名字不允许为空。
  （3）性别的值只能是：'男'和'女'。
  （4）年龄的值在0~100之间。
    答案：
create table student
(
    sno        int primary key auto_increment comment '学号',
    name       varchar(10) not null comment '姓名',
    sex        char(5) check(sex='男' or sex='女') comment'性别',
    age        int check(age>=0 and age<=100) comment '年龄',
    major      varchar(20)  comment '专业'
);



# 10.7  本章练习
## 一、单选题
  1. 对于多表连接来说，MySQL默认的连接方式是（  ```A ）。
    ```A. 内连接                             B. 自连接
    C. 左外连接                           D. 右外连接
  2. 如果想要合并两个结果集，并且保留重复记录，应该使用（  B ）。
    ```A. union                               B. union all
    C. all                                  D. join
  3. 一个员工有多个手机号，每个手机号仅属于某个特定的员工，那么员工和手机号之间的关系是（  B ）。
    ```A. 一对一                             B. 一对多
    C. 多对多                             D. 以上都不对
  4. 下面的说法中，不正确的是（  C ）。
    ```A. select语句既可以实现单表查询，也可以实现多表查询
    B. 联合查询是以“行”为单位进行操作的
    C. 内连接查询是以“行”为单位进行操作的
    D. 外连接查询是以“列”为单位进行操作的
    分析：
    联合查询（union）是以“行”为单位进行操作的，而内连接和外连接都是以“列”为单位进行操作的。
## 二、问答题
  1. 请简单说一下表与表之间的关系有哪些？
    答案：
    一对一 、一对多（多对一）、多对多。
  2. 请简单说一下union和union all之间的区别。
    答案：
    union和union all都可以合并两个结果集，但是对于重复数据，union只会保留其中一条，而union all则会全部保留下来。
  3. 请简单说一下左外连接、右外连接和完全外连接之间的区别。
    答案：
    左外连接，是根据左表来获取连接结果。右外连接，是根据右表来获取连接结果。完全外连接，同时保留左表和右表的所有连接记录。



# 11.6  本章练习
## 一、单选题
  1. 在MySQL中，用于创建视图的语句是（  C ）。
    ```A. create table                               B. create index
    C. create view                               D. create database
  2. 在视图上不能完成的操作是（  C ）。
    ```A. 查询数据                                B. 更新数据
    C. 在视图上创建新的表                      D. 在视图上创建新的视图
    分析：
    在视图上可以定义另一个新视图，但是不可以定义新表。
  3. 在删除视图时，用于判断视图是否存在的关键字是（  ```A ）。
    ```A. if exists                                  B. exists
    C. as exists                                 D. is exists
  4. 为了简化复杂的查询操作，而又不增加数据的存储空间，常用的方法是创建一个（  ```A ）。
    ```A. 视图                                   B. 索引
    C. 游标                                   D. 另一个表
  5. 下面关于创建视图的说法中，正确的是（  C ）。
    ```A. 视图只能创建在单表上
    B. 创建视图时，with check option是必需的
    C. 可以基于2个或2个以上的表来创建视图
    D. 删除一个视图，会删除对应原表的数据
    分析：
    A中，视图既可以基于单表创建，也可以基于多表创建。
    B中，创建视图时，with check option是可选的。
    D中，删除一个视图，只会删除视图的定义，并不会删除对应原表的数据。
  6. 下面关于视图的说法中，正确的是（  B ）。
    ```A. 通过视图可以插入数据、修改数据，但不能删除数据
    B. 视图也可以由视图派生出来
    C. 查询视图和查询表的语句是不一样的
    D. 视图是数据库用来存储数据的另一种形式的表
    分析：
    A中，通过视图，可以插入数据、修改数据和删除数据。
    C中，查询视图和查询表的语句是一样的，都是使用select语句。
    D中，视图并不保存数据，它保存的是一条select语句。
## 二、简答题
  1. 请简单说一下视图和表之间有什么区别和联系，请分别说一下？
  答案：
  （1）区别：表保存的是真实数据，而视图保存的是一条select语句。
  （2）联系：视图中所有的数据都来源于表。对视图数据的增删改，会影响表中的数据；对原表的增删改，也会影响视图中的数据。
  2. 请简单说一下视图的作用都有什么？
    答案：
  （1）聚焦特定数据：比如某一个表的列非常多，而我们一般只会用到某几个列的数据，此时就可以使用视图来聚焦特定的数据，为用户定制数据。
  （2）提高重用性：如果一个查询操作经常使用，并且select语句本身又长又复杂（比如使用很多聚合函数、关联其他表等），此时我们可以将其保存成一个视图。
  （3）提高安全性：对于一些不能被修改的重要的字段，如果我们不希望被用户误操作，此时可以使用视图只暴露一些不重要的字段，而把那些重要字段给隐藏起来。

## 三、编程题
  1. 请基于本书中的product表，写出每一个问题对应的SQL语句。
  （1）创建一个包含name、price、date这3列的视图，并命名为product_v。
  （2）查看product_v的创建代码。
  （3）将product_v修改为包含name、price这两列的视图。
  （4）删除product_v这个视图。
    答案：
  （1）
create view product_v
as select name, price, date from product;
  （2）
show create view product_v;
  （3）
alter view product_v
as select name, price from product;
  （4）
drop view product_v;

# 12.5  本章练习
## 一、单选题
  1. 在MySQL中，不能对视图执行的操作是（  D ）。
    ```A. select                                B. insert
    C. update                               D. create index
    分析：
    我们只能对表的字段进行创建索引，而不能对视图的字段创建索引。
  2. 我们给表建立索引的主要目的是（  C ）。
    ```A. 节省存储空间                        B. 提高安全性
    C. 提高查询速度                        D. 提高更新速度
  3. 索引可以加快数据的（  B ）速度。
    ```A. 插入                                B. 查询
    C. 更新                                D. 以上都是
    分析：
    索引只会加快数据的查询速度，并不会加快数据的插入或更新速度




# 13.6  本章练习
## 一、单选题
  1. 如果想要调用一个名为pr的存储过程，我们应该使用（  B ）。
    ```A. pr();                                B. call pr();
    C. do pr();                             D. show pr();
  2. 如果想要删除一个名为pr的存储过程，我们应该使用（  C ）。
    ```A. drop proc pr;                         B. drop function pr;
    C. drop procedure pr;                    D. delete procedure pr;
  3. 如果想要查看数据库中都有哪些触发器，我们可以使用（  B ）。
    ```A. show trigger                          B. show triggers
    C. select triggers                         D. display triggers
  4. 对表的哪一个操作时，不会触发触发器？（  ```A ）
    ```A. select                               B. insert
    C. update                              D. delete
  5. 如果某数据库在非工作时间（每天8:00之前、18:00之后、周六周日）不允许用户插入数据，下面哪一种方式实现最为合理？（  B ）。
    ```A. 存储过程                           B. before触发器
    C. 存储函数                           D. after触发器
  6. 下面关于触发器的说法中，正确的是（  B ）。
    ```A. 在一个表上只能创建一个触发器
    B. 在一个表上针对同一个数据操作只能创建一个before触发器
    C. 用户可以调用触发器
    D. 可以使用alter trigger语句来修改一个触发器
    分析：
    A中，一个表上可以创建多个触发器。
    C中，用户是不可以调用触发器的，触发器是由insert、delete、update这几种操作触发的。
    D中，MySQL不存在alter trigger语句。如果想要修改一个触发器，我们应该先删除该触发器，然后再创建一个同名的触发器。
## 二、简答题
  1. 简单说一下存储过程和存储函数之间有什么区别？
    答案：
  （1）用途不同：存储过程是一系列SQL语句的集合，它一般涉及表的各种操作。而存储函数一般不涉及表的操作，而是完成特定的功能（比如将字符串转换为小写）。
  （2）参数不同：存储过程的参数类型有int、out、inout这3种，而存储函数的参数类型类似于in参数。
  （3）返回值不同：存储过程可以不返回值，也可以输出一个或多个结果集（注意这是集合）。而存储函数有且只能返回一个值（这是标量值，而不能是集合）。
  （4）调用方式不同：存储过程需要使用call关键字来调用，而存储函数一般在SQL语句中调用（类似于内置函数）。
## 三、编程题
  1. 定义一个不带参数存储过程pr，查询product表中不同type商品的平均售价，并且调用执行该存储过程。
    答案：
-- 定义
create procedure pr()
begin
    select type as 类型, avg(price) as 平均售价
    from product
    group by type;
end;

-- 调用
call pr();
  2. 定义一个带参数的存储过程pr，其参数名为ptype。也就是输入商品类型，然后查询该类型最高售价的商品基本信息。并且要调用该存储过程，输入参数的值为'衣服'。
    答案：
-- 定义
create procedure pr(ptype varchar(10))
begin
    select *
    from product
    where type = ptype and price = (
        select max(price) from product where type = ptype
    );
end;

-- 调用
call pr('衣服');


# 14.2  本章练习
## 一、单选题
  1. 在MySQL中，可以使用（  B ）关键字来读取一个游标。
    ```A. select                                B. fetch
    C. get                                  D. read
  2. 下面关于游标的说法中，不正确的是（  D ）。
    ```A. 在使用游标之前，我们必须先打开游标
    B. 游标只能在存储过程或存储函数中使用
    C. 一个存储过程中可以定义多个游标
    D. 游标本质上是一条select语句
    分析：
    D中，游标并不是一条select语句，而是被select语句查询出来的结果集。
  3. 如果想要声明一个名为cur的游标，正确的语句是（  ```A ）。
    ```A. declare cur cursor for select name, price from product
    B. declare cur cursor as select name, price from product
    C. cursor cur for select name, price from product
    D. cursor cur as select name, price from product
    分析：
    声明游标（创建游标）的语法如下：
declare 游标名cursor for 查询语句;
## 二、问答题
  1. 请简单说一下游标的作用是什么？
    答案：
    游标可以使得我们对查询结果集进行遍历，也就是一行一行地处理数据，以便对每一条数据进行相应的操作。

# 15.3  本章练习
## 一、单选题
  1. 在MySQL中，我们可以使用（  B ）关键字来回滚一个事务。
    ```A. commit                           B. rollback
    C. submit                            D. back
  2. 下面不属于事务的属性的是（  D ）。
    ```A. 原子性                           B. 一致性
    C. 隔离性                           D. 暂时性
## 二、简答题
  1. 请简单说一下事务的属性都有哪些？
    答案：
    原子性、一致性、隔离性、持久性。


# 16.4  本章练习
## 一、单选题
1. 在MySQL中，预设的拥有最高权限的用户名是（  D ）。
 ```A. administrator                              B. manager
 C. user                                      D. root
2. 下面可以将root用户的密码修改为“666”的语句是（  AD  ）。（选2项）
 ```A. alter user 'root'@'localhost' identified by '666';
 B. alter user 'root'@'localhost'='666';
 C. set password for 'root'@'localhost' identified by '666';
 D. set password for 'root'@'localhost'='666';
3. 如果想要删除本地的test1用户，我们可以使用（  ```A ）来实现。
 ```A. drop user 'test1'@'localhost';
 B. drop user 'test1'.'localhost';
 C. drop user 'localhost'@'test1';
 D. drop user 'localhost'.'test1';
4. 下面关于安全管理的说法中，正确的是（  C ）。
 ```A. 使用create user语句创建一个新用户后，该用户可以访问所有数据库。
 B. 使用grant语句授予用户权限之后，该用户可以把自身的权限再授予其他用户。
 C. 使用show grants语句查询权限时，需要指定查询的用户名和主机名
 D. 我们只能授予普通用户对数据表查询、插入、更新、删除这4种权限
 分析：
 A中，创建新用户之后，默认只能登录MySQL服务器，而不具备任何操作数据库的权限。
 B中，使用grant语句授权用户权限时，只有加上with grant option，该用户才能把自身的权限再授予其他用户。
 D中，可以授予各种权限，而不只限于查询、插入、更新、删除这4种。


# 17.5  本章练习
## 一、单选题
1. 下面关于数据库备份的说法中，不正确的是（  C ）。
    ```A. 库的备份，会将该库所有的表都一起备份了
    B. 为了保证数据的安全性，我们需要经常对数据库进行备份
    C. 数据库的备份和还原，只能通过软件的方式来还原
    D. 对于库备份的还原，会覆盖该库中同名的表
    分析：
    C中，数据库的备份和还原，有2种方式：①软件的方式（Navicat for MySQL）；②SQL代码方式。

# 18.4  本章练习
## 一、单选题
  1. 下面不属于MySQL系统数据库的是（  C ）。
    ```A. mysql                                B. information_schema
    C. master                               D. performance_schema
  2. 对于用户的权限表，一般包含在哪一个数据库中？（  B ）
    ```A. sys                                   B. mysql
    C. user                                  D. test
