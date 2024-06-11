#### 常用数据类型 

- Char (10)：十个字符串
- Varchar (10)：弹性容纳十个字符串，小于 10 则省略多余 null 字符，上限为 10
- Nchar (10)：可容纳中文的十个 Unicode 数据
- Nvarchar (10)：弹性容纳十个 Unicode 数据，小于 10 则省略多余 null 字符，上限为 10
- Decimal (10.2)：小数类型，长度为 10 小数点后保留两位
- Time：时间+精确到后七位：HH:MM: SS. 1234567
- Date：日期：YYYY-MM-DD
- Datetime：日期+时间+精确到后 3 位：YYYY-MM-DD HH:MM: SS. 123
- Smalldatetime：日期+时间：YYYY-MM-DD HH:MM:SS
- Datetime 2：日期+时间+精确到后 7 位：YYYY-MM-DD HH:MM: SS. 1234567

#### SQL 约束  

![[ASLant_Images/5366e84c35e1b5c446436f53cb476504_MD5.jpg]]

#### 本地连接

如果实例是默认名字即可用英文符号 `.` 或者 `(local)` 又或者 `localhost` 进行连接如果是自定义名称，那么就需要用 `IP\实例名` 或 `本机名\实例名` # 约束

> **主键约束**：检查当前列是否有重复值，如果有则不保存当前数据进入数据库

创建方法：表 - 设计 - 右键列名前面 - 设为主键/删除主键 SQL 语句添加 - primary key
```sql
-- 新建表时添加 primary key
create table Student(
  Sno int identity primary key not null,
)
```

> **唯一约束 unique**：同理主键约束，主键约束也是唯一约束

创建方法：设计界面右键空白处 - 索引/键 - 添加 - 自定义标识名称 (可忽略) - 更改常规的类型为唯一键 SQL 语句添加
```sql
-- 新建列时添加
create table Student(
  Sno char(8) primary key,
  Sname char(8) unique,
)
-- 已经创建了列的时候添加
alter table Student add unique(Sname)
-- 添加多个对象也是可以的
alter table Student add unique(Sname, Sage)
```

> **检查约束**：检查当前列中设定的条件是否为真，为假则提示错误

创建方法：设计界面右键空白处 - Check 约束 - 添加 - 自定义标识名称 (可忽略) - 常规表达式 - 配置表达式如：`xxx = '男' or xxx = '女'` ，xxx 为列表名 SQL 语句添加
```sql
-- 创建列时添加
create table T_Employee(
  Age int not null check(age >= 18 and age <= 50),
);
-- 已有列后添加
alter table T_Employee add check(age >= 18 and age <= 50)
-- 当然也可以同时添加多个check约束
alter table T_Employee add check(age >= 18 and age <= 50), check(EmpName != 'test')
```

> **默认约束**：默认当前列的数据都是指定数据

设置方法：列属性 - 默认值绑定 - 设置默认值 SQL 语句添加
```sql
-- 创建列时添加
create table T_Employee(
  Sex nchar(8) default '保密'
);
-- 已有列后添加
alter table T_Employee add constraint sex default '保密' for sex
```

> **主键约束与唯一约束的区别**：

[table id=12 /] 主键约束也是与唯一性相同的，但是他只能有一个且不能为空，而且整个表只存在一个主键，而唯一性约束就是主键“管不到”的列上它来负责数据的唯一性，所以可以拥有多个唯一性约束 # 主键和外键关系

主键就类似于一个核心，外键的数据需要去主键确定是否存在才能存储进入外键数据表举个例子，假如给学号列表定位主键，因为每个人的学号是独一无二的，我们把整个班级的学号都存储到了主键上，当另一张表想要存储进入一条学号数据时，外键就会先来看看主键是否存在这个学号，如果存在则存储进入自己的表中，否则就提示错误。建立外键关系也相当与特定情况下为了数据安全增加了一道保障 > 如何建立外键呢？首先得满足以下条件

- 当两个表的某列数据需要关联的时候
- 一个列创建为外键的时候，另一个列必须为主键
- 两个列的属性与列名需要完全一致

如何区分谁是外键谁是主键？A 现在需要去找 B 确定是否存在这个数据，A 就是外键，B 就是主键 > 可视化创建方法：

演示一下，这里创建一张名为 test 1 的表，作为外键表，一列为 ID 列，一列为 Name 列，他们对应 int 类型与 nvarchar 类型 [![[ASLant_Images/5366e84c35e1b5c446436f53cb476504_MD5.jpg]] 然后再新建一个名为 test 2 的表，作为主键表请注意！因为我要 Name 这个列创建外键关系，所以在这个主键表需要把 Name 设为主键 [![](undefined) 两张表的 Name 列的属性、数据类型、Null 是否为空全部一致的情况下，我们回到 test 1 表右键空白处，点击关系 [![](undefined) 在新的窗口中点击添加，然后在右侧表和列规范点击最右边的按钮 [![](undefined) 然后把主键表改为 test 2，下面的选项分边选择两张表的 Name 列 [![](undefined) 然后点击确定，关闭，Ctrl + S 保存，此时会提示一个提示更改了表什么什么的，确定即可这时候我们去编辑 test 2 表，在 Name 输入两个参数，小明和小红 [![](undefined) 然后我们去编辑 test 1 外键表，尝试在 Name 里面输入其他的数据 [![](undefined) 此时就会提示约束冲突，然后我们输入主键表中的数据 [![](undefined) 此时就会发现没问题啦 > 语句创建方法

创建表时添加：constraint 自定义外键名 foreign key (外键列名) references 主键表名 (主键列名) 创建表后添加：alter table 外键表名 constraint 自定义外键名 foreign key (外键列名) references 主键表名 (主键列名) 当前表的列名为外键，表名 (列名) 为主键
`foreign key (外键名) references 主键表名(主键名)`

```sql
-- 建立表1-Customer里面的CustomerID列与表2-Orders里面的CustomerID列为主外键关系
-- 表2的CustomerID将设置为外键
create table Orders(
  OrderID int primary key,
  CustomerID int,
  foreign key (CustomerID) references Customer(CustomerID)
)

-- 建表后添加
alter table Orders add constraint FK_Orders_Customer foreign key (CustomerID) references Customer(CustomerID)
```

#### 增删改查

> **create 新增数据库**

```sql
-- 创建一个名为T_Employee的表
create table T_Employee(
        -- 设置为自增、主键
  EmpId int identity primary key,
  EmpName nvarchar(32) not null,
  Age int not null,
  Sex nchar(8) not null,
  Salary money not null,
  Birthday date not null
);
```

> **insert 新增数据**

Insert into 表名 values (对应列内容 1 , 对应列内容 2 , 对应列内容 3... ...)

```sql
-- 在test1表中插入一行数据，数据由逗号隔开且顺序对应
insert into test1 values(1, '小明', 18, '男')
```

如果需要增加多行就使用 union 即可 insert into 表名 values (对应列名 1 , 对应列名 2 , 对应列名 3... ...) select 对应列内容 1 , 对应列内容 2 , 对应列内容 3 unionselect 对应列内容 1 , 对应列内容 2 , 对应列内容 3 unionselect 对应列内容 1 , 对应列内容 2 , 对应列内容 3

```sql
-- 在test1表中插入多行数据，数据由逗号隔开且顺序对应
insert into test1
select 2, '茄子', 18, '男' union
select 3, '毛子', 20, '男' union
select 4, '小波', 21, '女' union
select 5, '馒老六', 22, '男'
```

以上方法适用于正行数据新增，如果只想增加某一项则需要在表名后面列出想要新增的列 insert into 表名 (对应列名 1 , 对应列名 2 , 对应列名 3... ...) values (对应列内容 1 , 对应列内容 2 , 对应列内容 3... ...)

```sql
-- 在test1表中插入一行数据到指定列，数据由逗号隔开且顺序对应指定列
insert into test1(ID, Age, Gender) values(6, 18, '男')
```

如果忽略某内容时，值为 NULL > **delete 删除数据**

Delete from 表单名 where 条件

```sql
-- 删除test1表中ID=4的一行数据
delete from test1 where ID = 4
```

或者删除整个表格的数据，但保留列 delete from 表名

```sql
-- 删除了test1表中全部数据，保留了列的属性
delete from test1
```

如果不想要这张表单，那么也可以全部移除 drop from 表名运行完刷新表，就会发现 test 1 表已经不见了，彻底删除

```sql
-- 彻底删除整张表test1
drop table test1
```

> **update 修改数据**

Update 表名 set 列名= ...

```sql
-- 修改test1表的Gender列全部为“女”
update test1 set Gender = '女'
```

当然也可以修改数值，增加条件等 update 表名 set 列名 = \'xxx\' , 列名 = \'xxx\' , 列名 = \'xxx\' 

```sql
-- 修改test1表中Gender列全部改为“骚”；Age列的数值全部+3；ID列数值全部+1
update test1 set Gender = '骚', Age += 3, ID += 1
```

当然还可以指定某一行然后修改，比如我们指定 ID 列列等于 5 的行，修改他的名字为茄子 update 表名 set 列名 = \'xxx\' where 列名 = \'xxx\' where 后面就是搜索条件 

```sql
-- 修改test1表中ID=2的一行其中的Name数据为“馒老六”
update test1 set Name = '馒老六' where ID = 2
```

Where 后面条件满足时才会进行索引，否则跳过 > **select：查询数据**

- 查询列数据

在 test 1 表中查找 name 列与 Age 列的全部数据，如果查找单列就输入一个即可 select 列名 1, 列名 2 from 表名

```sql
select Name, Age from test1
```

- **运算符比较查询**

在 test 1 表中获取大于 18 岁的数据（Age > 18） 运算符有>、<、>=、<=、= - **or 或关系、and 与关系**

在这里也可以用到或关系和与关系，或也就是两个条件只需要满足一个即可，而与需要同时满足才行 select * from 表名 where 列名 = xx or 列名 = xx

```sql
select * from test1 where Age = 18 or Name = '小黄'
```

在这里只要等于 18 岁的满足条件 1，所以搜索出来了；小黄的名字满足条件 2，也被搜索出来了

```sql
select * from test1 where Age = 18 and Name = '小明'
```

这里使用了 and，也就是两个必须满足才能搜索到，所以只输出了小明这一行的数据，因为条件 1 与 2 全部满足 - **like 模糊搜索% , \_**

Like 的意思就是模糊查找； %代表的是**任意的字符串**，它的值**可以是空**的也**可以不是空**的 \_代表的的是一个**占位符**，可以理解为它是**存在**数据的只是**不知道数据是什么**，它只代表一个数值！并且不能为空！ Like 演示：找出 test 1 表中 Age 列全部是 18 的数据

```sql
select * from test1 where Age like '18'
```

Like 就是精确搜索，它同等于 where Age = \'18\' **%演示：**找出 test 1 表中 Phone 列中前面符合 123456 数据因为%他的值可空也可以不空，可以看见小明的 Phone 数值只有 123456 但是也被搜索了，因为它后面没有值，满足条件；123456 后面还存在数据的也被搜索了，因为后面有数值，也算满足条件，这就是%的使用方法 

```sql
select * from test1 where Phone like '123456%'
```

既然能忽略后面的数值，那么同理也可以忽略前面

```sql
select * from test1 where Phone like '%5678'
```

前面和后面也可以同时忽略，只提取中间

```sql
select * from test1 where Phone like '%56%'
```

**\_演示**：找出 test 1 表中 Age 列中以 8 结尾的数据
```sql
select * from test1 where Age like '_8'
```

### 修改表名列名与列类型


```sql
-- 修改表名 
exec sp_rename '表名', '新表名'
-- 修改列名
exec sp_rename '表名.[列名]', '新列名' , 'column'
--修改表类型
alter table 表名 alter column 列名 数据类型 not null;
```

### 函数

> **修改显示内容：`replace`**

把 test 1 表中的 Name 列的所有“小明”替换成“小红”并不修改数据内容，只显示在结果 `replace(列名, 转换前, 转换后)`

```sql
select replace (Name, '小明', '小红') from test1
```

> **反向显示：`reverse`**

把 test 1 表中的 Name 列所有数据全部反向显示，如 ABC 反向显示为 CBA `reverse(列名)`

```sql
select reverse(Name) from test1
```

> **字符串转换为数字：`str`**

将字符串转换成数字并返回 `str(数字字符串,  最大长度, 小数后几位)` 如果数字字符串没有小数，可以忽略第三项的小数后几位设置；最大长度为整个数字的长度，包括小数

```sql
select str('123456', 6)
-- 结果为123456
select str('123.456', 6, 3)
-- 结果为123.456
```

> **提取指定字符：`substring`**

提取“我起了一枪秒了有什么好说的”其中的“一枪秒了”字段这个并不是从 0 开始计算，而是从 1 开始，“我起了”分别是 123，“一”处于第四个，所以从 4 开始截取，然后向后取四个字符 `substring('字符串数据', 起始位置, 取值范围)`

```sql
select substring('我起了一枪秒了有什么好说的', 4, 4)
```

> **返回字符串位置：`charindex`**

返回“我起了一枪秒了有什么好说的”其中的“一枪秒了”在这句话的多少位置原理同上 `charindex('想要查询的字符串', '整个字符串')`

```sql
select charindex('一枪秒了', '我起了一枪秒了有什么好说的')
-- 返回了4
```

> **获取指定字符串长度：`len`**

`len('指定字符串')`

```sql
select len('我起了一枪秒了有什么好说的')
```

> **获取左/右指定数据：`left/right`**

从左/右获取指定的数据 `left/right('指定的字符串', 获取多少位)`

```sql
select left('我起了一枪秒了有什么好说的', 5)
select right('我起了一枪秒了有什么好说的', 5)
```

> **获取当前年月日：`getdate`**

获取当前时间 `getdate()`

```sql
select getdate() 当前时间
select day(getdate()) 当前天数
select month(getdate()) 当前月数
select year(getdate()) 当年年数
```

> **时间戳差距计算：`datediff`**

计算给出的两个时间段相差多少年/月/日 `datediff(年/月/日, '时间1', '时间2')`

```sql
-- 依次对应查询年月日
select datediff(year, '2000-1-1', '2002-5-5')
select datediff(month, '2000-1-1', '2002-5-5')
select datediff(day, '2000-1-1', '2002-5-5')
```

如果第一个数值比第二个数值要小，将返回负数结果 > **增加时间：`dateadd`**

给指定时间增加年/月/日 `dateadd(年/月/日, 增加大小, 指定时间)`

```sql
-- 获取当前时间并增加8天
select dateadd(day, 8, getdate())
```

> **随机取数：`rand`**

在 0 - 1 中间随机取值 `rand()`

```sql
select rand()
```

随机取整数可以用*来解决 floor 是取 0 至 N-1 之间的；ceiling 是取 0 至 N 之间

```sql
select floor(rand()*100)
select ceiling(rand()*100)
```

> **指定舍去数：`round`**

round 的意思就是指定一个位置进行四舍五入，比如我在下方案例里面的数值填上 12345.567，把舍去的数值改为 2，那么他就会向右边推进两位，然后开始运算四舍五入，也就是保留两位小数变成 12345.570 如果我填写-1，那么他就会向左边推进一位，然后开始计算四舍五入，结果为 12350.000 同理，如果我填写-2，他就会向左边推进 2 位进行四舍五入运算，结果为 12300.000 `round('数值', 舍去的数值)`

```sql
select round(12345.567, -2) --12300.000
select round(12345.567, -1) -- 12350.000
select round(12345.567, 0) -- 12346.000
select round(12345.567, 1) -- 12345.600
select round(12345.567, 2) -- 12345.570
```

> **转换函数：`cast , convert`**

将数据转换成其他格式 `cast(数据 as 类型)``convert(类型, 数据)`

```sql
-- cast转换
select '当前时间为：' + cast(getdate() as nvarchar(max))
-- convert转换
select '当前时间为：' + convert(nvarchar(max), getdate())
```

Cast 与 convert 的区别就是 convert 可以格式化时间和数值 # 不允许重复

test 1 表中存在重复的 name 值，就可以用 distinct 去过滤掉重复数据 `distinct 列名`

```sql
-- 去掉重复的name
select distinct name from test1
```

## 分组查询 group by

group by 的主要用处就是对一堆数据进行分组查询，先分组，再查询 `group by 分组列名`

```sql
-- 从test表中先把sex分组，然后从分组中查询每个分组最大的salary
select max(salary) from test group by sex
```

## 增加&&删除字段

```sql
-- 新增字段
alter table 表名 add 字段名 数据类型

-- 删除字段
alter table 表名 drop column 字段名
```

## 替换字段名

```sql
execute sp_rename '表名.字段名','新字段名'
```

## 去重

```sql
select distinct(列名) from 表名
```

## 删除数据库全部表

```sql
use master;
go
sp_msforeachtable @command1="drop table ?"
go
```

## 主外键设置

### 建表时设置

`foreign key references [主键表名]([主键列名])`

```sql
create table T_ATM(
    BianHao int primary key identity(1,1),
    MingCheng varchar(20) not null,
    XingBie char(1) not null,
    BiShaJi varchar(300),
    ShenGao decimal(18,2),
    TiZhong decimal(18,2),
    ShengRi date,
    # 设置主键
    ChuShengDiBH int foreign key references T_CSD(ChuShengDiBH),
    TuPian varchar(100)
)
```



### 建表后设置

`alter table [外键表名] add constraint 约束名 foreign key ([外键列名]) references [主键表名]([主键列名])`

```sql
alter table [UserInfo] add constraint FK_User_Role_User foreign key ([Id]) references [UserAuth]([Id])
```



## 视图


视图是一个虚拟的表，是一个表中的数据经过某种筛选后的显示方式，视图由一个预定义的查询 select 语句组成。



### 视图的作用

1. 视图隐藏了底层的表结构，简化了数据访问操作，客户端不再需要知道底层表的结构及其之间的关系。
2. 视图提供了一个统一访问数据的接口。（即可以允许用户通过视图访问数据的安全机制，而不授予用户直接访问底层表的权限）
3. 从而加强了安全性，使用户只能看到视图所显示的数据。
4. 视图还可以被嵌套，一个视图中可以嵌套另一个视图。



```sql
if exists(select * from sys.views where name = 'testView') -- 视图是否存在
drop view testView -- 存在就删除
go
create view testView -- 创建视图
as
select [user_name], [user_passwd], [dept_id] -- 视图内容
from [T_user]
go
select * -- 查询视图
from testView
```

## 存储过程

> 创建不带参数存储过程

```sql
if (exists (select * from sys.objects where name = 'proc_get_student'))
    drop proc proc_get_student
go
create proc proc_get_student
as
    select * from student;

--调用、执行存储过程
exec proc_get_student;
```


> 带参存储过程

```sql
if (object_id('proc_find_stu', 'P') is not null)
    drop proc proc_find_stu
go
create proc proc_find_stu(@startId int, @endId int)
as
    select * from student where id between @startId and @endId
go

exec proc_find_stu 2, 4;
```

## Datediff

DATEDIFF () 函数返回两个日期之间的时间。

```sql
SELECT DATEDIFF(day,'2008-12-30','2008-12-29') AS DiffDate
-- -1
```

## Isnull

Isnull (参数 1，参数 2)，判断参数 1 是否为 NULL，如果是，返回参数 2，否则返回参数 1。

```sql
select ISNULL(null,'helloword') -- 返回helloword字符串
select ISNULL('','helloword') -- 返回 空串
```

# 判断是否为 null

使用 `is` 或 `is not` 即可直接判断是否为 null

```sql
select * from userinfo where info is not null
```

