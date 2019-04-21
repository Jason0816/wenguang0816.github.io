---
title: 数值的整数次方
date: 2019-04-21 13:52:00
img: https://upload-images.jianshu.io/upload_images/14484228-05fef34f486bd5b0.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer：12、数值的整数次方
categories: 剑指 offer
tags:
  - 数学
---
### [12\. 数值的整数次方](https://www.nowcoder.com/practice/1a834e5e3e1a4b7ba251417554e07c00?tpId=13&tqId=11165&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
给定一个double类型的浮点数base和int类型的整数exponent。求base的exponent次方。

### 解题思路：
+ 思路1：直接求解
+ 思路2：简单快速幂：
  - 写出指数的二进制表达，例如`13`的二进制为`1101`
  - 以底数为`10`为例：`10^13 = 10^1101 = 10^0001 * 10^0100 * 10^1000`

### 解答：

```cpp
// 方法1
class Solution {
public:
    double Power(double base, int exponent) {
        double res = 1.0;
        if(exponent == 0)
            return 1;
        if(exponent < 0)
        {
            if(base == 0)
                throw "The denominator cannot be 0";
            else
                base = 1.0 / base;
        }
        while(exponent)
        {
            res *= base;
            exponent = (exponent > 0) ? --exponent : ++exponent;
        }
        return res;
    }
};
// 方法2:
class Solution {
public:
    double Power(double base, int exponent) {
        double res = 1.0;
        int flag = 1; // 指数正负标志位，1为正
        if(exponent == 0)
            return 1;
        if(exponent < 0)
        {
            if(base == 0)
                throw "The denominator cannot be 0";
            else
                exponent = -exponent;
            flag = 0;
        }
        while(exponent != 0)
        {
            if((exponent & 1) == 1)
                res *= base;
            base *= base;
            exponent >>= 1;
        }

        return flag ? res : (1 / res);
    }
};
```