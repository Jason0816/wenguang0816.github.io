---
title: LeetCode刷题：268.Missing Number
date: 2019-02-24 13:09:00
categories: LeetCode
tags:
  - 位运算
  - 数组
  - 数学
---
#### [268\. Missing Number](https://leetcode-cn.com/problems/missing-number/)
Given an array containing *n* distinct numbers taken from `0, 1, 2, ..., n`, find the one that is missing from the array.

**Example 1:**

**Input:** `[3,0,1]`

**Output:** `2`

**Example 2:**

**Input:** `[9,6,4,2,3,5,7,0,1]`

**Output:** `8`

**Note**:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?
##### 解题思路：
要求时间复杂度为O(n)；
+ 思路1： 采用和[136\. Single Number](https://leetcode-cn.com/problems/single-number/)类似的思路，将容器中所有的数字和有序数列`1,2,3……,n`异或，如果容器中存在数字`x`，那么和有序数列中对应的`x`异或结果为零，最终得到的结果便为缺失的数字。
+ 思路2：采用求和相减，若容器长度为`n`，利用求和公式计算`s1 = n * (n+1) / 2`，减去容器中数字的求和`s2`，则可得缺失的数字。
##### 解答：
```
//方法1：
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int result = 0;
        int len = nums.size();
        for(int i = 0; i < len; ++i)
        {
            result ^= (i+1) ^ nums[i];
        }
        return result;
    }
};
//方法2：
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int s1 = n * (n + 1) / 2;
        int s2 = 0;
        for(int i : nums)
        {
            s2 += i;
        }
        return s1 - s2;
    }
};
```