---
title: LeetCode刷题：627.Swap Salary
date: 2019-02-24 13:17:00
categories: LeetCode
tags:
  - LeetCode
---
#### [627\. Swap Salary](https://leetcode-cn.com/problems/swap-salary/)
SQL架构
```
create table if not exists salary(id int, name varchar(100), sex char(1), salary int)
Truncate table salary
insert into salary (id, name, sex, salary) values ('1', 'A', 'm', '2500')
insert into salary (id, name, sex, salary) values ('2', 'B', 'f', '1500')
insert into salary (id, name, sex, salary) values ('3', 'C', 'm', '5500')
insert into salary (id, name, sex, salary) values ('4', 'D', 'f', '500')
```
Given a table `salary`, such as the one below, that has m=male and f=female values. Swap all f and m values (i.e., change all f values to m and vice versa) with a single update query and no intermediate temp table.For example:
```
| id | name | sex | salary |
|----|------|-----|--------|
| 1  | A    | m   | 2500   |
| 2  | B    | f   | 1500   |
| 3  | C    | m   | 5500   |
| 4  | D    | f   | 500    |
```
After running your query, the above salary table should have the following rows:
```
| id | name | sex | salary |
|----|------|-----|--------|
| 1  | A    | f   | 2500   |
| 2  | B    | m   | 1500   |
| 3  | C    | f   | 5500   |
| 4  | D    | m   | 500    |
```
##### 解题思路：
利用SQL中的case-when多条件判断语句，类似C++中的switch-case语句
##### 解答：
```
UPDATE salary
SET sex = (CASE sex WHEN 'm' THEN 'f'
                    WHEN 'f' THEN 'm'
           END)
```