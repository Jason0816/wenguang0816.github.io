---
title: LeetCode刷题：136.Single Number
date: 2019-02-24 13:04:00
categories: LeetCode
tags:
  - LeetCode
---
#### [136\. Single Number](https://leetcode-cn.com/problems/single-number/)
Given a **non-empty** array of integers, every element appears *twice* except for one. Find that single one.

**Note:**
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

**Input:** `[2,2,1]`

**Output:** `1`

**Example 2:**

**Input:** `[4,1,2,1,2]`

**Output:** `4`
##### 解题思路：
题目要求算法的时间复杂度为O(n),空间复杂度为O(1)；
将容器的所有的数字进行异或运算，由于相同两个数字异或结果为0，所以所有元素异或的结果便为所寻单独的数字。
##### 解答：
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int result = 0;
        for(auto ibeg = nums.begin(); ibeg != nums.end(); ++ibeg)
        {
            result ^= *ibeg;  //所有数字进行异或运算 
        }
        return result;
    }
};
```