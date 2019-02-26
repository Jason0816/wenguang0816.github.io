---
title: LeetCode刷题：561.Array Partition I
date: 2019-02-24 13:14:00
categories: LeetCode
tags:
  - 数组
---
#### [561\. Array Partition I](https://leetcode-cn.com/problems/array-partition-i/)
Given an array of **2n** integers, your task is to group these integers into **n** pairs of integer, say (a<sub>1</sub>, b<sub>1</sub>), (a<sub>2</sub>, b<sub>2</sub>), ..., (a<sub>n</sub>, b<sub>n</sub>) which makes sum of min(a<sub>i</sub>, b<sub>i</sub>) for all i from 1 to n as large as possible.

**Example 1:**

**Input:** `[1,4,3,2]`

**Output:** `4`

**Explanation:** `n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).`

**Note:**
1.  **n** is a positive integer, which is in the range of [1, 10000].
2.  All the integers in the array will be in the range of [-10000, 10000].
##### 解题思路：
为得到最大的和，所以要保证第2大的数字和第1大的数字进行组合，第4大的数字和第3大的数字进行组合，以此类推。可以看出，我们将数组进行排序后，取`2n+1`项进行相加，即可得结果。
##### 解答：
```
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        int len = nums.size();
        sort(nums.begin(), nums.end());
        int result = 0;
        for(int i = 0; i < len; ++i)
        {
            result += nums[i];
            ++i;
        }
        return result;
    }
};
```