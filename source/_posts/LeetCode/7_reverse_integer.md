---
title: LeetCode刷题：7.Reverse Integer
date: 2019-02-27 21:49:00
categories: LeetCode
tags:
  - 数学
---
#### [7\. Reverse Integer](https://leetcode-cn.com/problems/reverse-integer/)
Given a 32-bit signed integer, reverse digits of an integer.
**Example 1:**

>**Input:** `123`
>
>**Output:** `321`

**Example 2:**
>**Input:** `-123`
>
>**Output:** `-321`

**Example 3:**
>**Input:** `120`
>
>**Output:** `21`

**Note:**
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−2<sup>31</sup>,  2<sup>31 </sup>− 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.
##### 解题思路：
初始化一个`long long`类型的变量`ans`用于保存反转后的整数，每次执行以下操作：
1. `ans = ans * 10 + x % 10;`
2. `x /= 10;`

最后判断`ans`是否溢出，溢出则返回0，否则返回`ans`
*在第一次尝试时，忽略了反转后的数字可能出现溢出的情况，定义int类型的ans会导致溢出，所以将ans定义为 long long类型*
##### 解答：
```cpp
class Solution {
public:
    int reverse(int x) {
        //INT_MAX : 2147483647 
        //INT_MIN : -2147483648
        long long ans = 0;
	    while (x != 0) {
            ans = ans * 10 + x % 10;
            x /= 10;
        }
	    return (ans > INT_MAX || ans < INT_MIN) ? 0 : ans;
    }
};
```
