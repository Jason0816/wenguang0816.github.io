---
title: 斐波那契数列
date: 2019-04-01 16:50:00
img: https://upload-images.jianshu.io/upload_images/14484228-85685db844f2ddfd.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer： 刷题笔记第一天：7、斐波那契数列
categories: 剑指 offer
tags:
  - 循环
  - 斐波那契
---
### [7\. 斐波那契数列](https://www.nowcoder.com/practice/c6c7742f5ba7442aada113136ddea0c3?tpId=13&tqId=11160&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
大家都知道斐波那契数列，现在要求输入一个整数n，请你输出斐波那契数列的第n项（从0开始，第0项为0）。

**注：n<=39**

### 解题思路：
>斐波那契数列：0, 1, 1, 2, 3, 5, 8 ......;
>
>这个数列从第3项开始，每一项都等于前两项之和。
>
>利用递推公式：f(n) = f(n - 1) + f(n - 2);(当n >= 2时)
>
>时间复杂度O(n), 空间复杂度O(1)


### 解答：

```cpp
class Solution {
public:
    int Fibonacci(int n) {
        int i = 0;
        int a = 0, b = 1;
        while(i < n)
        {
            b = a + b;
            a = b - a;
            ++i;
        }
        return a;
    }
};
```