---
title: 矩形覆盖
date: 2019-04-04 10:30:00
img: https://upload-images.jianshu.io/upload_images/14484228-bed5c3df25430959.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer：10、矩形覆盖
categories: 剑指 offer
tags:
  - 递归
---
### [10\. 矩形覆盖](https://www.nowcoder.com/practice/72a5a919508a4251859fb2cfb987a0e6?tpId=13&tqId=11163&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
我们可以用`2*1`的小矩形横着或者竖着去覆盖更大的矩形。请问用n个`2*1`的小矩形无重叠地覆盖一个`2*n`的大矩形，总共有多少种方法？

### 解题思路：
这仍然是一个斐波那契数列问题。
```
f(1) = 1
f(2) = 2
f(n) = f(n-1) + f(n-2)
```
### 解答：

```cpp
class Solution {
public:
    int rectCover(int number) {
        if(number <= 0)
            return 0;
        if(number == 1)
            return 1;
        int first = 1, second = 2, third = 2;
        for(int i = 2; i < number; ++i)
        {
            third = first + second;
            first = second;
            second = third;
        }
        return third;
    }
};

```