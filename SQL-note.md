# SQL笔记



## 目录

[TOC]





### **SQL61** 检索并列出已订购产品的清单*

```mysql
select distinct (prod_id) from OrderItems;
```

```mysql
select distinct(prod_id) from OrderItems;
```

```mysql
select distinct prod_id from OrderItems;
```

##### 常见的字母混合

```markdown
I和l,1
o和O和0
```





### SQL63 检索顾客名称并且排序

- https://www.nowcoder.com/practice/6cfabb1b49554c4c8d8f9977bf6a3a5d?tpId=298&tqId=2364830&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%25E7%25AF%2587%26topicId%3D298

```mysql
select cust_name  
from Customers
order by cust_name DESC;
```








### SQL64 对顾客ID和日期排序

- https://www.nowcoder.com/practice/fa4eb4880d124a4ead7a9b025fe75b70?tpId=298&tqId=2364830&ru=%2Fexam%2Foj&qru=%2Fta%2Fsql-teach-yourself%2Fquestion-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%E7%AF%87%26topicId%3D298

```MYSQL
SELECT cust_id,order_num
from Orders
order by cust_id asc, order_date DESC;
```

```markdown
order by 不能分行，只能用逗号隔开！必须写到最后一行！！！【order by cust_id asc, order_date DESC;】
注意选择项要与题目一致【SELECT cust_id,order_num】，没有说要日期就不管日期。

```





