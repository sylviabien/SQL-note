# SQL-Note
> 《SQL必知必会》题解+我的SQL笔记

- 1.[SQL踩坑经验.md](./1.SQL踩坑经验.md)
- 2.[解题技巧1-子查询的做题方法.md](./2.解题技巧1-子查询的做题方法.md)

> 题单来源，[牛客网](https://www.nowcoder.com/exam/oj?page=1&tab=SQL%E7%AF%87&topicId=298)



## 1.检索数据

### 60.[从 Customers 表中检索所有的 ID](https://www.nowcoder.com/practice/009199576d094b56807a8368058841ee?tpId=298&tqId=2363165&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

```mysql
select cust_id from Customers;
```



### 61.[检索并列出已订购产品的清单](https://www.nowcoder.com/practice/9e4741b77f4244149a069883bc0d23be?tpId=298&tqId=2364828&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

```mysql
select distinct prod_id from OrderItems;
```



### 62.[检索所有列](https://www.nowcoder.com/practice/cf0e3919ba8e4fa2ba19ea09df7fb756?tpId=298&tqId=2364829&ru=%2Fpractice%2F9e4741b77f4244149a069883bc0d23be&qru=%2Fta%2Fsql-teach-yourself%2Fquestion-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

```mysql
select cust_id,cust_name from Customers;
```



## 2.排序检索数据

### 63.检索顾客名称并且排序

```mysql
select cust_name from Customers
order by cust_name desc;
```



### 64.对顾客ID和日期排序

```mysql
select cust_id,order_num
from Orders
order by cust_id ,order_date desc;
```



### 65.按照数量和价格排序

```mysql
select *
from OrderItems
order by quantity desc,item_price desc;
```



### 66.检查SQL语句

```mysql
select vend_name
from Vendors
order by vend_name desc;
```





## 3.过滤数据

### 67. [返回固定价格的产品](https://www.nowcoder.com/practice/9949bfb933614abe8bd2bc26c129843e?tpId=298&tqId=2366910&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

```mysql
select prod_id,prod_name
from Products
where prod_price=9.49
```



### 68.返回更高价格的产品

```mysql
select prod_id,prod_name
from Products
where prod_price >=9;
```



### 69.返回产品并且按照价格排序

```mysql
select prod_name,prod_price
from Products
where prod_price between 3 and 6
order by prod_price ;
```



### 70.返回更多的产品

```mysql
select distinct order_num 
from OrderItems
where quantity >=100;
```





## 4.高级数据过滤

### 71.检索供应商名称

```mysql
select vend_name
from Vendors
where vend_country ='USA' and vend_state ='CA';
```



### 72.检索并列出已订购产品的清单

```mysql
select order_num,prod_id,quantity
from OrderItems
where prod_id in ('BR01','BR02','BR03')
and  quantity >=100;
```



### 73.返回所有价格在 3美元到 6美元之间的产品的名称和价格

```mysql
select prod_name,prod_price
from Products
where prod_price between 3 and 6
order by prod_price asc;1
```



### 74.纠错2

```mysql
select vend_name
from Vendors
where vend_country='USA' AND vend_state='CA'
```





## 5.用通配符进行过滤

### 75.检索产品名称和描述（一）

```mysql
select prod_name,prod_desc
from Products
where prod_desc like '%toy';
```



### 76.检索产品名称和描述（二）

```mysql
select prod_name,prod_desc
from Products
where not prod_desc like '%toy%'
order by prod_name;
```



### 77.检索产品名称和描述（三）

```mysql
select prod_name,prod_desc
from Products
where prod_desc like '%toy%'
and prod_desc like '%carrots%';
```



### 78.检索产品名称和描述（四）

```mysql
select prod_name,prod_desc
from Products
where prod_desc like '%toy%carrots%';
```





## 6.创建计算字段

### 79.别名

```mysql
select vend_id,
vend_name as vname,
vend_address as vaddress,
vend_city as vcity
from Vendors
order by vname asc;
```



### 80.打折

```mysql
select 
prod_id,
prod_price,
prod_price*0.9 as sale_price
from Products;
```





## 7.使用函数处理数据

### 81.顾客登录名

```mysql
select
cust_id,
cust_name,
upper(concat(left(cust_contact,2),left(cust_city,3)))
as user_login
from Customers;
```



### 82.返回 2020 年 1 月的所有订单的订单号和订单日期

```mysql
select order_num,order_date
from Orders
where year (order_date)=2020
and month (order_date)=1
order by order_date asc;
```







## 8.汇总数据

### 83.确定已售出产品的总数

```mysql
select sum(quantity) as items_ordered
from OrderItems;
```



### 84.确定已售出产品项 BR01 的总数

```mysql
select sum(quantity) as items_ordered
from OrderItems
where prod_id like 'BR01'
```



### 85.确定 Products 表中价格不超过 10 美元的最贵产品的价格

```mysql
select max(prod_price) as max_price
from Products
where prod_price <=10 ;
```

## 9.分组数据

### 86.[返回每个订单号各有多少行数](https://www.nowcoder.com/practice/cf1f8d4a514d455aa0468718fb411f41?tpId=298&tqId=2374634&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)



```mysql
select order_num, count(*) as order_lines
from OrderItems
group by order_num
order by order_lines asc;
```



### 87.每个供应商成本最低的产品

```mysql
select vend_id,
min(prod_price) as cheapest_item
from Products
group by vend_id
order by cheapest_item asc;
```



### 88.确定最佳顾客

```mysql
select order_num
from OrderItems
group by order_num
having sum(quantity)>=100
order by order_num asc;
```



### 89.确定最佳顾客的另一种方式（一）

```mysql
select order_num,
sum(item_price*quantity ) as  total_price
from OrderItems
group by order_num
having total_price>=1000
order by order_num asc;
```



### 90.纠错3

```mysql
select order_num,count(*) as items
from OrderItems
group by order_num
having count(*)>=3
```





## 10.使用子查询

### 91.[返回购买价格为 10 美元或以上产品的顾客列表](https://www.nowcoder.com/practice/827eb2a210c64ccdb8ec28fe4c50c246?tpId=298&tqId=2374686&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

```mysql
select cust_id
from Orders
where order_num in
(
    select order_num from OrderItems
    where item_price >=10
    )
```



### 92.[确定哪些订单购买了 prod_id 为 BR01 的产品（一）](https://www.nowcoder.com/profile/548473347/codeBookDetail?submissionId=404543255)

```mysql
select cust_id,order_date
from Orders
where order_num in
(
select order_num
from OrderItems
where prod_id ='BR01')
```



### 93.[返回购买 prod_id 为 BR01 的产品的所有顾客的电子邮件（一）](https://www.nowcoder.com/practice/962b16554fbf4b99a87f4d68020c5bfb?tpId=298&tqId=2374689&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%E7%AF%87%26topicId%3D298)

```mysql
select cust_email from Customers
where cust_id in

(select cust_id from  Orders
where order_num in

(select order_num from OrderItems
where prod_id='BR01'))
```



### 94.[返回每个顾客不同订单的总金额](https://www.nowcoder.com/practice/ce313253a81c4947b20e801cd4da7894?tpId=298&tqId=2374691&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

- 坑点：`OrderItems.order_num = Orders.order_num`需要考虑，2个订单是否完整

```mysql
select
  cust_id, 
  (
      select sum( item_price*quantity ) as total_ordered
      from OrderItems
      where OrderItems.order_num = Orders.order_num
      group by order_num
   ) as total_ordered
from
  Orders
order by  total_ordered desc
```



### 95.[从 Products 表中检索所有的产品名称以及对应的销售](https://www.nowcoder.com/practice/2b289b78de1546f38fd24e17e56f1bec?tpId=298&tqId=2374695&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

```mysql
select prod_name,
(
select sum(quantity) as quant_sold
from OrderItems
where Products.prod_id=OrderItems.prod_id
group by prod_name
)as quant_sold
from Products
```





## 11.联结表

### 96.返回顾客名称和相关订单号

```mysql
select cust_name,order_num
from Orders,Customers
where Customers.cust_id=Orders.cust_id
order by cust_name asc;
```



### 97.返回顾客名称和相关订单号以及每个订单的总价

```mysql
select 
Customers.cust_name,
Orders.order_num,
sum(item_price*quantity)as OrderToal
from Customers,Orders,OrderItems
where Customers.cust_id=Orders.cust_id 
 and Orders.order_num=OrderItems.order_num
group by cust_name,order_num
order by cust_name asc,order_num asc;
```



### 98.返回顾客名称和相关订单号以及每个订单的总价

```mysql
select cust_id,order_date
from Orders 
where Orders.order_num in
(
    select order_num from OrderItems
    where prod_id='BR01'
)

order by order_date asc;
```



### 99.返回顾客名称和相关订单号以及每个订单的总价

> 方法1：inner join

```mysql
select cust_email 
from Customers 
inner join Orders on Customers.cust_id=Orders.cust_id
inner join OrderItems on Orders.order_num=OrderItems.order_num
where OrderItems.prod_id='BR01';
```

> 方法2

```mysql
select cust_email
from Customers
where cust_id in 
(select cust_id from Orders
    where order_num in 
    ( select order_num from OrderItems
        where prod_id = 'BR01'
      )
  );
```



### 100.确定最佳顾客的另一种方式（二）

> inner join

```mysql
select Customers.cust_name,sum(item_price*quantity) as total_price
from Customers 
inner join Orders on Customers.cust_id=Orders.cust_id
inner join OrderItems on Orders.order_num=OrderItems.order_num
group by Customers.cust_name
having total_price >=1000;
```





## 12.创建高级联结

### 101.确定最佳顾客的另一种方式（二）

```mysql
select cust_name,order_num
from Customers
inner join Orders on Customers.cust_id=Orders.cust_id
order by cust_name asc;
```



### 102.检索每个顾客的名称和所有的订单号（二）

```mysql
select cust_name,order_num
from Customers
left outer join Orders on Customers.cust_id=Orders.cust_id
order by cust_name asc;
```



### 103.返回产品名称和与之相关的订单号

```mysql
select prod_name,order_num
from Products
left outer join OrderItems on Products.prod_id=OrderItems.prod_id
order by prod_name asc;
```



### 104.返回产品名称和每一项产品的总订单数

```mysql
select prod_name,count(order_num)as orders
from Products
left outer join OrderItems on Products.prod_id=OrderItems.prod_id
group by prod_name
order by prod_name asc;
```



### 105.列出供应商及其可供产品的数量

```mysql
select Vendors.vend_id,count(Products.prod_id) as prod_id
from Vendors
left outer join Products on Vendors.vend_id=Products.vend_id
group by Vendors.vend_id
order by Vendors.vend_id ;
```





## 13.组合查询

### 106.将两个 SELECT 语句结合起来(一)

```mysql
(select prod_id,quantity
from OrderItems
where quantity =100)
union
select prod_id,quantity
from OrderItems
where prod_id like 'BNBG%'
order by prod_id
```



### 107.将两个 SELECT 语句结合起来(一)

```mysql
select *
from OrderItems
where quantity=100
or prod_id like 'BNBG%';
```



### 108.组合 Products 表中的产品名称和 Customers 表中的顾客名称

```mysql
select prod_name
from Products
union all 
select cust_name
from Customers
order by prod_name;
```



### 109.纠错4

```mysql
select cust_name,cust_contact,cust_email
from Customers
where cust_state in ('MI','IL')
order by cust_name;
```

