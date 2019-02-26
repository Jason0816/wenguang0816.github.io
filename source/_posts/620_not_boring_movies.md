---
title: LeetCode刷题：620.Not Boring Movies
date: 2019-02-24 13:16:00
categories: LeetCode
tags:
  - LeetCode
---
#### [620\. Not Boring Movies](https://leetcode-cn.com/problems/not-boring-movies/)
SQL架构
```
Create table If Not Exists cinema (id int, movie varchar(255), description varchar(255), rating float(2, 1))
Truncate table cinema
insert into cinema (id, movie, description, rating) values ('1', 'War', 'great 3D', '8.9')
insert into cinema (id, movie, description, rating) values ('2', 'Science', 'fiction', '8.5')
insert into cinema (id, movie, description, rating) values ('3', 'irish', 'boring', '6.2')
insert into cinema (id, movie, description, rating) values ('4', 'Ice song', 'Fantacy', '8.6')
insert into cinema (id, movie, description, rating) values ('5', 'House card', 'Interesting', '9.1')
```
X city opened a new cinema, many people would like to go to this cinema. The cinema also gives out a poster indicating the movies’ ratings and descriptions.
Please write a SQL query to output movies with an odd numbered ID and a description that is not 'boring'. Order the result by rating.
For example, table `cinema`:
```
+---------+-----------+--------------+-----------+
|   id    | movie     |  description |  rating   |
+---------+-----------+--------------+-----------+
|   1     | War       |   great 3D   |   8.9     |
|   2     | Science   |   fiction    |   8.5     |
|   3     | irish     |   boring     |   6.2     |
|   4     | Ice song  |   Fantacy    |   8.6     |
|   5     | House card|   Interesting|   9.1     |
+---------+-----------+--------------+-----------+
```
For the example above, the output should be:
```
+---------+-----------+--------------+-----------+
|   id    | movie     |  description |  rating   |
+---------+-----------+--------------+-----------+
|   5     | House card|   Interesting|   9.1     |
|   1     | War       |   great 3D   |   8.9     |
+---------+-----------+--------------+-----------+
```
##### 解题思路：
通过`description`和`id`进行筛选，然后通过`rating`进行倒序排序（`DESC`）
##### 解答：
```sql
SELECT id, movie, description, rating
FROM cinema
WHERE id % 2 != 0 and description != 'boring'
ORDER BY rating DESC
```