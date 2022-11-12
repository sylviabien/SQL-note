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



## 10.使用子查询

### 91.返回购买价格为 10 美元或以上产品的顾客列表



### 92.确定哪些订单购买了 prod_id 为 BR01 的产品（一）



### 93.[返回购买 prod_id 为 BR01 的产品的所有顾客的电子邮件（一）](https://www.nowcoder.com/practice/962b16554fbf4b99a87f4d68020c5bfb?tpId=298&tqId=2374689&ru=/exam/oj&qru=/ta/sql-teach-yourself/question-ranking&sourceUrl=%2Fexam%2Foj%3Fpage%3D1%26tab%3DSQL%E7%AF%87%26topicId%3D298)
