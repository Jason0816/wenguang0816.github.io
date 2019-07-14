---
title: 跳台阶
date: 2019-04-03 15:00:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190403-1.jpg
summary: 剑指 offer：8、跳台阶
categories: 剑指 offer
tags:
  - 查找
  - 数组
---
### [8\. 跳台阶](https://www.nowcoder.com/practice/8c82a5b80378478f9484d87d1c5f12a4?tpId=13&tqId=11161&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级。求该青蛙跳上一个n级的台阶总共有多少种跳法（先后次序不同算不同的结果）。

### 解题思路：
利用递归思想：可以根据第一步的走法，将所有走法分为两类，第一类是第一步走`1`个台阶，另一类是第一步走`2`个台阶，所以`n`个台阶的走法就等于先走`1`个台阶后`n-1`个台阶的走法，加上先走`2`个台阶后`n-2`个台阶的走法，用公式表示为：
```
f(n) = f(n-1) + f(n-2)
```
有了递归公式，接下来就需要确定终止条件了，当有`1`个台阶时，只有一种走法，`f(1) = 1`，当有`2`个台阶时，有两种走法，`f(2) = 2`，因此递归公式为：
```
f(1) = 1
f(2) = 2
f(n) = f(n-1) + f(n-2)
```
通过观察递归公式可以发现，递归公式和斐波那契数列相似，则可以改进代码，提高算法运行效率

### 解答：

```cpp
// 解法1:
class Solution {
public:
    int jumpFloor(int number) {
        if(number == 1)
            return 1;
        if(number == 2)
            return 2;
        return jumpFloor(number -1) + jumpFloor(number -2);
    }
};

// 解法2:
class Solution {
public:
    int jumpFloor(int number) {
        int first = 1, second = 1, third = 0;
        if(number == 0)
            return 0;
        if(number == 1)
            return 1;
        for(int i = 1; i < number; ++i)
        {
            third = first + second;
            first = second;
            second = third;
        }
        return third;
    }
};
```