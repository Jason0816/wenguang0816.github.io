---
title: 变态跳台阶
date: 2019-04-03 15:25:00
img: https://upload-images.jianshu.io/upload_images/14484228-dd70f6a8a2cfe109.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer：刷题笔记第三天：9、变态跳台阶
categories: 剑指 offer
tags:
  - 递归
  - 循环
---
### [9\. 变态跳台阶](https://www.nowcoder.com/practice/22243d016f6b47f2a6928b4313c85387?tpId=13&tqId=11162&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

### 解题思路：
+ 思路1: 利用递归思路，可参考[8、跳台阶](http://blog.wenguang0816.top/2019/04/03/08-jumpfloor/)
递归公式为：
```
f(1) = 1
f(2) = 1 + f(1) = 2
f(3) = 1 + f(1) + f(2) = 4
...
f(n) = 1 + f(1) + f(2) + ... + f(n-1)
```
另外可以观察到：
```
f(n) = 1 + f(1) + f(2) + ... + f(n-2) + f(n-1)
f(n-1) = 1 + f(1) + f(2) + ... + f(n-2) + f(n-1)
-->
f(n) = 2*f(n-1)
```
+ 思路2: 除最后一个台阶外，每一个台阶都可以选择跳或者不跳，故`f(n) = 2 ^ (n - 1)`

### 解答：

```cpp
// 解法1:
class Solution {
public:
    int jumpFloorII(int number) {
        if(number <= 0)
            return 0;
        if(number == 1)
            return 1;
        int ans = 1;
        while(number > 0)
        {
            ans += jumpFloorII(number -1);
            --number;
        }
        return ans;
    }
};

// 解法2:
class Solution {
public:
    int jumpFloorII(int number) {
        if(number <= 0)
            return 0;
        if(number == 1)
            return 1;
        int ans = 1;
        return 2 * jumpFloorII(number - 1);
    }
};

// 解法3:
class Solution {
public:
    int jumpFloorII(int number) {
        int ans =  pow(2, number - 1);
        return ans;
    }
};
```