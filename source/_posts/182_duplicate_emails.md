---
title: LeetCode刷题：182.Duplicate Emails
date: 2019-02-24 13:05:00
categories: LeetCode
tags:
  - 数据库
---
#### [182\. Duplicate Emails](https://leetcode-cn.com/problems/duplicate-emails/)

SQL架构
```sql
Create table If Not Exists Person (Id int, Email varchar(255))
Truncate table Person
insert into Person (Id, Email) values ('1', 'a@b.com')
insert into Person (Id, Email) values ('2', 'c@d.com')
insert into Person (Id, Email) values ('3', 'a@b.com')
```
Write a SQL query to find all duplicate emails in a table named `Person`.

**Example:**

| Id | Email   |
|----|---------|
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |

For example, your query should return the following for the above table:

| Email   |
|---------|
| a@b.com |

**Note**: All emails are in lowercase.
##### 解题思路：
使用 GROUP BY 和 HAVING 条件：向 GROUP BY 添加条件的一种更常用的方法是使用 HAVING 子句，该子句更为简单高效。
GROUP BY 语句用于结合合计函数，根据一个或多个列对结果集进行分组。
##### 解答：
```sql
select Email from Person
group by Email having count(Email) > 1;
```