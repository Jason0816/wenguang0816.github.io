---
title: LeetCode刷题：509.Fibonacci Number
date: 2019-02-24 13:13:00
categories: LeetCode
tags:
  - 数组
---
#### [509\. Fibonacci Number](https://leetcode-cn.com/problems/fibonacci-number/)
The **Fibonacci numbers**, commonly denoted `F(n)` form a sequence, called the **Fibonacci sequence**, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,
```
F(0) = 0,   F(1) = 1
F(N) = F(N - 1) + F(N - 2), for N > 1.
```
Given `N`, calculate `F(N)`.

**Example 1:**
>**Input:** `2`
>
>**Output:** `1`
>
>**Explanation:** `F(2) = F(1) + F(0) = 1 + 0 = 1.`

**Example 2:**
>**Input:** `3`
>
>**Output:** `2`
>
>**Explanation:** `F(3) = F(2) + F(1) = 1 + 1 = 2.`

**Example 3:**
>**Input:** `4`
>
>**Output:** `3`
>
>**Explanation:** `F(4) = F(3) + F(2) = 2 + 1 = 3.`

**Note:**
0 ≤ `N` ≤ 30.
##### 解题思路：
+ 思路1：采用递归的方法
+ 思路2：采用数组，将斐波那契数存入到数组中。
##### 解答：
```cpp
//方法1：
//效率较低，运行时间20ms
int fibonacci(int n)
{
    if(n == 0)
        return 0;
    else if(n == 1)
        return 1;
    return fibonacci(n-1) + fibonacci(n-2); 
}
class Solution {
public:
    int fib(int N) {
        return fibonacci(N);     
    }
};
//方法2：
//运行时间0ms
class Solution {
public:
    int fib(int N) {
        int *p = new int[N+1];//开辟大小为N+1的数组
        p[0] = 0;
        p[1] = 1;
        for(int i = 2; i < N+1; ++i)
        {
            p[i] = p[i-1] + p[i-2];
        }
        return p[N];
    }
};
```