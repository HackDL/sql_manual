# SQL手册

## 一、前言

**欢迎访问SQL手册**

**作者QQ：15593838**

**github地址：https://github.com/BrechtCheung/sqlManual**

若您发现手册中有错误，或者您有更好的建议或意见，可以加我（QQ:15593838）进行反馈

手册整理不易，若能满足您的需求，可以给作者发个小红包支持一下。万分感谢!

![微信和支付宝](https://s2.loli.net/2021/12/30/2Wa1UdxhbXJkF59.jpg)



**一、【语句】select**

```sql
select * from 表名;
或者
select 字段1,字段2  from 表名;
```

**二、【语句】distinct**

```sql
select distinct 字段名 from 表名;
```

**三、【子句】where**

1、文本字段

```sql
select * from 表名where 字段名='1';
```

2、数值字段

```sql
select * from 表名 where 字段名=1;
```

3、运算符

| 运算符  | 描述                                                   |
| ------- | ------------------------------------------------------ |
| =       | 等于                                                   |
| <>      | 不等于。注释：在 SQL 的一些版本中，该操作符可被写成 != |
| >       | 大于                                                   |
| <       | 小于                                                   |
| >=      | 大于等于                                               |
| <=      | 小于等于                                               |
| BETWEEN | 在某个范围内                                           |
| LIKE    | 搜索某种模式                                           |
| IN      | 指定针对某个列的多个可能值                             |

**四、【运算符】and & or**

1、如果第一个条件和第二个条件都成立，则 and 运算符显示一条记录。

```sql
select * from 表名 where name='张三' and sex ='男';
```

2、如果第一个条件和第二个条件中只要有一个成立，则 or 运算符显示一条记录。

```sql
select * from 表名 where name='张三' or name ='李四';
```

3、您也可以把 and 和 or 结合起来（使用圆括号来组成复杂的表达式）。

```sql
select * from 表名 where (name='张三' or name ='李四') and sex ='男';
```

**五、【关键字】order by** 

1、正序排列

```sql
select * from 表名 order by 字段名;
select * from 表名 order by 字段名 asc;
```

2、倒序排列

```sql
select * from 表名 order by 字段名 desc;
```

**六、【语句】insert into**

```sql
insert into 表名(字段1,字段2) values(字段值1,字段值2)
```

**七、【语句】update**

```sql
update 表名 set 字段1=字段值1,字段2=字段值2 where 查询条件
```

**八、【语句】delete**

1、删除指定数据行

```sql
delete from 表名 where 查询条件
```

2、删除全部数据

```sql
delete from 表名;
 或
delete * from 表名;
```

**九、【子句】top与limit**

1、返回前2行记录

```sql
select top 2 * from 表名;

select * from 表名 limit 2;
```

2、返回第3到10行的记录

```sql
select top 10 * from 表名 where 字段名 not in (select top 3 字段名 from 表名)

select * from 表名 limit 3,7
```

3、返回50%的记录

```sql
select top 50 percent * from 表名;
```

**十、【操作符】like**

1、查询以a开头的数据

```sql
select * from 表名 where 字段 like 'a%';
```

2、查询以a结尾的数据

```sql
select * from 表名 where 字段 like '%a';
```

3、查询包含a的所有数据

```sql
select * from 表名 where 字段 like '%a%';
```

4、查询不包含a的所有数据

```sql
select * from 表名 where 字段 not like '%a%';
```

5、查询一个任意字符开始，然后是 "a" 的所有数据

```sql
select * from 表名 where 字段 like '_a';
```

6、查询一个任意字符开始，然后是 "a_c_e" 的所有数据

```sql
select * from 表名 where 字段 like 'a_c_e';
```

7、查询以a或者b或者c开始的所有数据

```sql
select * from 表名 where 字段 like '^[abc]';
```

8、查询以a-z开头的所有数据

```sql
select * from 表名 where 字段 like '^[a-z]';
```

9、查询不以a-z开头的所有数据

```sql
select * from 表名 where 字段 like '^[^a-z]';
```

**十一、【操作符】in**

查询结果为a或者b的数据

```sql
select * from 表名 where 字段 in (‘a’,’b’)
```

**十二、【操作符】between**

```sql
#选取介于两个值之间的数据范围内的值。这些值可以是数值、文本或者日期。
```

1、查询1-20之间的所有数据

```sql
select * from 表名 where 字段名 between 1 and 20;
```

2、查询不在1-20之间的所有数据

```sql
select * from 表名 where 字段名 not between 1 and 20;
```

3、查询1-20之间并且值不为a、b、c的所有数据

```sql
select * from 表名 where 字段名 (between 1 and 20) and 字段名 not in(‘a’,’b’,’c’);
```

4、查询'a' 和 'h' 之间字母开始的所有数据

```sql
select * from 表名 where 字段名 between ‘a’ and ‘h’;
```

5、查询不在'a' 和 'h' 之间字母开始的所有数据

```sql
select * from 表名 where 字段名 not between ‘a’ and ‘h’;
```

6、查询日期在'2021-01-01' 和 '2022-01-01' 之间的所有数据：

```sql
select * from 表名 where 字段名 not between ‘2021-01-01’ and ‘2022-01-01’;
```

**十三、【别名】as**

1、表别名

```sql
select * from 表名 as 别名
```

2、列别名

```sql
select 字段1 as 别名 from 表名
```

3、混合别名

```sql
select 

表1别名.字段名,

表2别名.字段名 

from 

表1 as 表1别名,

表2 as 表2别名
```

**十四、【连接】join**

```sql
#join 子句用于把来自两个或多个表的行结合起来，基于这些表之间的共同字段。
```

1、inner join：如果表中有至少一个匹配，则返回行

```sql
select 

表1.字段名,

表2.字段名

from 表1 inner join 表2 on 表1.id=表2.id;
```

2、left join：即使右表中没有匹配，也从左表返回所有的行

```sql
select 

表1.字段名,

表2.字段名

from 表1 left join 表2 on 表1.id=表2.id;
```

3、right join：即使左表中没有匹配，也从右表返回所有的行

```sql
select 

表1.字段名,

表2.字段名

from 表1 right join 表2 on 表1.id=表2.id;
```

4、full join：只要其中一个表中存在匹配，则返回行（mysql不支持）

```sql
select 

表1.字段名,

表2.字段名

from 表1 full outer join 表2 on 表1.id=表2.id;
```

**十五、【操作符】union**

```sql
#union 操作符用于合并两个或多个 select 语句的结果集。
#请注意，union 内部的每个 select 语句必须拥有相同数量的列。列也必须拥有相似的数据类型。同时，每个 select 语句中的列的顺序必须相同。
#注释：默认地，union 操作符选取不同的值。如果允许重复的值，请使用 union all。
```

1、union取不同的值

```sql
select 字段1,字段2 from 表名
union
select 字段1,字段2 from 表名
order by 字段1;
```

2、union all 取所有的值（包含重复的）

```sql
select 字段1,字段2 from 表名
union all
select 字段1,字段2 from 表名
order by 字段1;
```

**十六、【语句】 select into（mysql 数据库不支持 select ... into 语句，但支持 [insert into ... select](https://www.runoob.com/sql/sql-insert-into-select.html) 。）**

```sql
#select into 语句从一个表复制数据，然后把数据插入到另一个新表中。
```

1、复制新表

```sql
select * into 新表名 from 表名
```

2、复制指定列到新表

```sql
select 字段名 into 新表名 from 表名 
```

3、只复制中国的网站插入到新表中：

```sql
select * into 新表名 from 表名 where ‘web’ = ‘中国’
```

4、复制多个表中的数据插入到新表中

```sql
select 表1.字段名,表2.字段名 into 新表名
from 表1 left join 表2 on 表1.id = 表2.id
```

5、复制一个空表

```sql
select * into 新表名 from 表名 where 1=0;
```

**十七、【语句】insert into select**

```sql
#select into from 和 insert into select 都是用来复制表。
#两者的主要区别为：
#select into from 要求目标表不存在，因为在插入时会自动创建；
#insert into select from 要求目标表存在。
```

1、从一个表中复制所有的列插入到另一个已存在的表中

```sql
insert into 表名select * from 要复制的表名;
```

2、复制指定的列插入到另一个已存在的表中

```sql
insert into 表1(表1.字段1，表1.字段2)
select 表2.字段1,表2.字段2 from 表2;
```

**十八、【语句】create database（创建数据库）**

```sql
create database 数据库名;
```

**十九、【语句】create table（创建数据表）**

```sql
create table 表名 
(
 字段名 字段类型（最大长度）
)
```

**二十、【约束】**

```sql
create table 表名 
(
 字段名 字段类型（最大长度）约束
)

#在 sql 中，我们有如下约束：
#1、not null - 指示某列不能存储 null 值。
#2、unique - 保证某列的每行必须有唯一的值。
#3、primary key - not null 和 unique 的结合。确保某列（或两个列多个列的结合）有唯一标识，有助于更容易更快速地找到表中的一个特定的记录。
#4、foreign key - 保证一个表中的数据匹配另一个表中的值的参照完整性。
#5、check - 保证列中的值符合指定的条件。
#6、default - 规定没有给列赋值时的默认值。
```

**二十一、【约束】not null**

```sql
#not null 约束强制列不接受 null 值。
#not null 约束强制字段始终包含值。这意味着，如果不向字段添加值，就无法插入新记录或者更新记录。
```

1、添加 not null 约束

```sql
alter table 表名 modify 字段名 int not null;
```

2、删除 not null 约束

```sql
alter table 表名 modify 字段名 int  null;
```

**二十二、【约束】unique**

```sql
#unique 约束唯一标识数据库表中的每条记录。
#unique 和 primary key 约束均为列或列集合提供了唯一性的保证。
#primary key 约束拥有自动定义的 unique 约束。
#请注意，每个表可以有多个 unique 约束，但是每个表只能有一个 primary key 约束。
```

**（1）、创建表时，添加约束**

1、mysql

```sql
create table 表名
(
 p_id int not null,
 unique (p_id)
)
```

2、sql server / oracle / ms access

```sql
create table 表名
(
 p_id int not null unique,
)
```

```sql
#如需命名 unique 约束，并定义多个列的 unique 约束，请使用下面的 sql 语法：
```

3、mysql / sql server / oracle / ms access：

```sql
create table 表名
(
 p_id int not null,
 lastname varchar(255) not null,
 constraint uc_personid=约束名 unique (p_id,lastname)
)
```

**（2）、表已存在时，添加约束**

1、当表已被创建时，如需在 "p_id" 列创建 unique 约束，请使用下面的 sql：

mysql / sql server / oracle / ms access：

```sql
alter table 表名 add unique (p_id)
```

2、如需命名 unique 约束，并定义多个列的 unique 约束，请使用下面的 sql 语法：

mysql / sql server / oracle / ms access：

```sql
alter table 表名 add constraint uc_personid=约束名 unique (p_id,lastname)
```

**（3）、表已存在时，撤销约束**

1、mysql：

```sql
alter table 表名 drop index uc_personid=约束名
```

2、sql server / oracle / ms access：

```sql
alter table 表名 drop constraint uc_personid=约束名
```

**二十三、【约束】primary key**

```sql
#primary key 约束唯一标识数据库表中的每条记录。
#主键必须包含唯一的值。
#主键列不能包含 null 值。
#每个表都应该有一个主键，并且每个表只能有一个主键。
```

**（1）、创建表时，添加约束**

1、mysql

```sql
create table 表名
(
 p_id int not null,
 primary key (p_id)
)
```

2、sql server / oracle / ms access

```sql
create table 表名
(
 p_id int not null primary key,
)
```

3、如需命名 unique 约束，并定义多个列的 unique 约束，请使用下面的 sql 语法：

mysql / sql server / oracle / ms access：

```sql
create table 表名
(
 p_id int not null,
 lastname varchar(255) not null,
 constraint pk_personid=约束名 primary key  (p_id,lastname)
)
```

**（2）、表已存在时，添加约束**

1、当表已被创建时，如需在 "p_id" 列创建 primary key 约束，请使用下面的 sql：

mysql / sql server / oracle / ms access：

```sql
alter table 表名 add primary key  (p_id)
```

2、如需命名 unique 约束，并定义多个列的 primary key 约束，请使用下面的 sql 语法：

mysql / sql server / oracle / ms access：

```sql
alter table 表名 add constraint pk_personid=约束名 primary key  (p_id,lastname)
```

**（3）、表已存在时，撤销约束**

1、mysql：

```sql
alter table 表名 drop primary key
```

2、sql server / oracle / ms access：

```sql
alter table 表名 drop constraint pk_personid=约束名
```

**二十四【约束】foreign key**

```sql
#一个表中的 foreign key 指向另一个表中的 unique key(唯一约束的键)。
```

**（1）、创建表时添加约束**

1、mysql：

```sql
create table 表1
(
 o_id int not null,
 orderno int not null,
 p_id int,
 primary key (o_id),
 foreign key (p_id) references 表2(p_id)
)
```

2、sql server / oracle / ms access：

```sql
create table 表1
(
 o_id int not null primary key,
 orderno int not null,
 p_id int foreign key references 表2(p_id)
)
```

3、如需命名 foreign key 约束，并定义多个列的 foreign key 约束，请使用下面的 sql 语法：

mysql / sql server / oracle / ms access：

```sql
create table 表1(
 o_id int not null,
 orderno int not null,
 p_id int,
 primary key (o_id),
 constraint fk_perorders=约束名 foreign key (p_id)
 references 表2(p_id)
)
```

**（2）、表已存在时，添加约束**

1、mysql / sql server / oracle / ms access：

```sql
alter table 表1 add foreign key (p_id) references 表2(p_id)
```

如需命名 foreign key 约束，并定义多个列的 foreign key 约束，请使用下面的 sql 语法：

2、mysql / sql server / oracle / ms access：

```sql
alter table 表1
add constraint fk_perorders=约束名
foreign key (p_id)
references 表2(p_id)
```

**（3）、表已存在时，撤销约束**

1、mysql：

```sql
alter table 表1 drop foreign key fk_perorders
```

2、sql server / oracle / ms access：

```sql
alter table 表1 drop constraint fk_perorders
```

**二十五、【约束】check**

```sql
#check 约束用于限制列中的值的范围。
#如果对单个列定义 check 约束，那么该列只允许特定的值。
#如果对一个表定义 check 约束，那么此约束会基于行中其他列的值在特定的列中对值进行限制。
```

**（1）、创建表时添加约束**

1、mysql：

```sql
create table 表名
(
 p_id int not null,
 check (p_id>0)
)
```

2、sql server / oracle / ms access：

```sql
create table 表
(
 p_id int not null check (p_id>0),
)
```

3、如需命名 check 约束，并定义多个列的 check 约束，请使用下面的 sql 语法：

mysql / sql server / oracle / ms access：

```sql
create table persons
(
 p_id int not null,
 city varchar(255),
 constraint chk_person=约束名 check (p_id>0 and city='sandnes')
)
```

**（2）、表已存在时，添加约束**

1、mysql / sql server / oracle / ms access:

```sql
alter table 表名 add check (p_id>0)
```

2、如需命名 check 约束，并定义多个列的 check 约束，请使用下面的 sql 语法：

mysql / sql server / oracle / ms access：

```sql
alter table 表名add constraint chk_person=约束名 check (p_id>0 and city='sandnes')
```

**（3）、表已存在时，撤销约束**

1、sql server / oracle / ms access：

```sql
alter table 表名drop constraint chk_person=约束名
```

2、mysql：

```sql
alter table 表名 drop check chk_person=约束名
```

**二十六、【约束】default**

```sql
#default 约束用于向列中插入默认值。
#如果没有规定其他的值，那么会将默认值添加到所有的新记录。
```

 **（1）、创建表时添加约束**

1、**my sql / sql server / oracle / ms access：**

```sql
create table 表名
(
    city varchar(255) default '我是默认值'
)
```

2、通过使用类似 getdate() 这样的函数，default 约束也可以用于插入系统值：

```sql
create table orders
(
    orderdate date default getdate()
)
```

**（2）、表已存在时，添加约束**

1、mysql：

```sql
alter table 表名
alter 字段名 set default '我是默认值'
```

2、sql server / ms access：

```sql
alter table 表名
add constraint ab_c default '我是默认值' for city
```

3、oracle：

```sql
alter table 表名
modify 字段名 default '我是默认值'
```

**（3）、表已存在时，撤销约束**

**1、mysql：**

```sql
alter table 表名
alter 字段名 drop default
```

**2、sql server / oracle / ms access：**

```sql
alter table 表名
alter column 字段名 drop default
```

**二十七、【语句】create index**

```sql
#create index 语句用于在表中创建索引。
#在不读取整个表的情况下，索引使数据库应用程序可以更快地查找数据。
#可以把索引当作新华字典的音序表，例如，要查“库”字，如果不使用音序，就需要从字典的 400 页中逐页来找。但是，如果提取拼音出来，构成音序表，就只需要从 10 多页的音序表中直接查找。这样就可以大大节省时间。
#索引可以提高查询速度，但是会影响插入记录的速度。因为，向有索引的表中插入记录时，数据库系统会按照索引进行排序，这样就降低了插入记录的速度，插入大量记录时的速度影响会更加明显。这种情况下，最好的办法是先删除表中的索引，然后插入数据，插入完成后，再创建索引。
```

1、sql create index 语法

```sql
#在表上创建一个简单的索引。允许使用重复的值：
create index index_name=索引名 on 表名 (字段名)
```

2、sql create unique index 语法

```sql
#在表上创建一个唯一的索引。不允许使用重复的值：唯一的索引意味着两个行不能拥有相同的索引值。
create unique index index_name=索引名 on 表名 (字段名)
#注释：用于创建索引的语法在不同的数据库中不一样。因此，检查您的数据库中创建索引的语法。
```

3、create index 实例
（1）、下面的 sql 语句在 "persons" 表的 "lastname" 列上创建一个名为 "pindex" 的索引：

```sql
create index pindex on persons (lastname)
```

（2）、如果您希望索引不止一个列，您可以在括号中列出这些列的名称，用逗号隔开：

```sql
create index pindex on persons (lastname, firstname)
```

4、什么时候需要创建索引

```
（1）、主键自动建立唯一索引
（2）、频繁作为查询条件的字段应该创建索引
（3）、查询中排序的字段创建索引将大大提高排序的速度（索引就是排序加快速查找
（4）、查询中统计或者分组的字段；
```

5、什么时候不需要创建索引

```
（1）、频繁更新的字段不适合创建索引，因为每次更新不单单是更新记录，还会更新索引，保存索引文件
（2）、where条件里用不到的字段，不创建索引；
（3）、表记录太少，不需要创建索引；
（4）、经常增删改的表；
（5）、数据重复且分布平均的字段，因此为经常查询的和经常排序的字段建立索引。注意某些数据包含大量重复数据，因此他建立索引就没有太大的效果，例如性别字段，只有男女，不适合建立索引。
```

