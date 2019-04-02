---
title: 求1+2+3+...+n
date: 2019-04-02 10:20:00
img: https://upload-images.jianshu.io/upload_images/14484228-c0f98bd75c679bc3.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer： 刷题笔记第二天： 47、求1+2+3+...+n
categories: 剑指 offer
tags:
  - 递归
  - 逻辑与
---
### [47\. 求1+2+3+...+n](https://www.nowcoder.com/practice/7a0da8fc483247ff8800059e12d7caf1?tpId=13&tqId=11200&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
求1+2+3+...+n，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）。

### 解题思路：
+ 思路1: 首先想到的是递归，但是递归要有返回条件，题目中明确说明不能使用if判断(用了if也可以AC)，所以采用逻辑与的短路特性，作为递归的返回条件
+ 思路2: 借助求和公式，`sum = n * (n + 1) / 2`，题目中规定不允许使用乘除法，可以借助求`n * (n + 1)`的二维数组的大小以及右移运算实现，有违规嫌疑

### 解答：

```cpp
// 解法1:
class Solution {
public:
    int Sum_Solution(int n) {
        int ans = n;
        // 逻辑与有短路特点，当前面为假时，则后面不计算，当ans = 0时，递归返回
        ans && (ans += Sum_Solution(n - 1));
        return ans;
    }
};

// 解法2:
class Solution {
public:
    int Sum_Solution(int n) {
        bool a[n][n + 1];
        return sizeof(a) >> 1;
    }
};
```