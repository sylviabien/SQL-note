# SQL-Note
《SQL必知必会》题解+我的SQL笔记

- SQL解题技巧
- SQL题解
- 我的SQL代码

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

### 64.对顾客ID和日期排序

### 65.按照数量和价格排序

### 66.检查SQL语句



## 3.过滤数据

### 67. [返回固定价格的产品](https://www.nowcoder.com/practice/9949bfb933614abe8bd2bc26c129843e?tpId=298&tqId=2366910&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

### 68.返回更高价格的产品

### 69.返回产品并且按照价格排序

### 70.返回更多的产品





## 4.高级数据过滤

### 71.检索供应商名称

### 72.检索并列出已订购产品的清单

### 73.返回所有价格在 3美元到 6美元之间的产品的名称和价格

### 74.纠错2





## 5.用通配符进行过滤

### 75.检索产品名称和描述（一）

### 76.检索产品名称和描述（二）

### 77.检索产品名称和描述（三）

### 78.检索产品名称和描述（四）





## 6.创建计算字段

### 79.别名

### 80.打折



## 7.使用函数处理数据

### 81.顾客登录名

### 82.返回 2020 年 1 月的所有订单的订单号和订单日期





## 8.汇总数据

### 83.确定已售出产品的总数

### 84.确定已售出产品项 BR01 的总数

### 85.确定 Products 表中价格不超过 10 美元的最贵产品的价格





## 9.分组数据

### 86.[返回每个订单号各有多少行数](https://www.nowcoder.com/practice/cf1f8d4a514d455aa0468718fb411f41?tpId=298&tqId=2374634&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298)

### 87.每个供应商成本最低的产品

### 88.确定最佳顾客

### 89.确定最佳顾客的另一种方式（一）

### 90.纠错3





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

### 97.返回顾客名称和相关订单号以及每个订单的总价

### 98.返回顾客名称和相关订单号以及每个订单的总价

### 99.返回顾客名称和相关订单号以及每个订单的总价

### 100.确定最佳顾客的另一种方式（二）



## 12.创建高级联结

### 101.确定最佳顾客的另一种方式（二）

### 102.检索每个顾客的名称和所有的订单号（二）

### 103.返回产品名称和与之相关的订单号

### 104.返回产品名称和每一项产品的总订单数

### 105.列出供应商及其可供产品的数量





## 13.组合查询

### 106.将两个 SELECT 语句结合起来(一)



### 107.将两个 SELECT 语句结合起来(一)



### 108.组合 Products 表中的产品名称和 Customers 表中的顾客名称



### 109.纠错4

