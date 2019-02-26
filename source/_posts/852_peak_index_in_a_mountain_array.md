---
title: LeetCode刷题：852.Peak Index in a Mountain Array
date: 2019-02-24 13:24:00
categories: LeetCode
tags:
  - LeetCode
---
#### [852\. Peak Index in a Mountain Array](https://leetcode-cn.com/problems/peak-index-in-a-mountain-array/)
Let's call an array `A` a *mountain* if the following properties hold:
*   `A.length >= 3`
*   There exists some `0 < i < A.length - 1` such that `A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]`
Given an array that is definitely a mountain, return any `i` such that `A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]`.

**Example 1:**

**Input:** `[0,1,0]`

**Output:** `1`

**Example 2:**

**Input:** `[0,2,1,0]`

**Output:** `1`

**Note:**
1.  `3 <= A.length <= 10000`
2.  `0 <= A[i] <= 10^6`
3.  A is a mountain, as defined above.
##### 解题思路：
指定临时变量`peak`和`peak_index`，`peak`与`A[i]`进行比较，若peak小于A[i]，则令`peak = A[i]; peak_index = i;`，遍历数组，直到`peak`取到最大值，`peak_index`为`peak`取最大时的i值
##### 解答：
```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& A) {
        int peak = 0, peak_index = 0;
        auto len = A.size() - 1;
        for(int i = 0; i < len; ++i)
        {
            if(peak < A[i])
            {
                peak = A[i];
                peak_index = i;
            }
        }
        return peak_index;
    }
};
```