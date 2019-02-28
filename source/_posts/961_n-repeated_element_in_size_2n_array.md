---
title: LeetCode刷题：961.N-Repeated Element in Size 2N Array
date: 2019-02-24 13:31:00
categories: LeetCode
tags:
  - LeetCode
---
#### [961\. N-Repeated Element in Size 2N Array](https://leetcode-cn.com/problems/n-repeated-element-in-size-2n-array/)
In a array `A` of size `2N`, there are `N+1` unique elements, and exactly one of these elements is repeated N times.
Return the element repeated `N` times.

**Example 1:**
>**Input:** `[1,2,3,3]`
>
>**Output:** `3`

**Example 2:**
>**Input:** `[2,1,2,5,3,2]`
>
>**Output:** `2`

**Example 3:**
>**Input:** `[5,1,5,2,5,3,5,4]`
>
>**Output:** `5`

**Note:**
1.  `4 <= A.length <= 10000`
2.  `0 <= A[i] < 10000`
3.  `A.length` is even
##### 解题思路：
根据题意，其余数字都是不同的，仅有目标值重复，故寻找出现次数大于1的数
##### 解答：
```cpp
class Solution {
public:
    int repeatedNTimes(vector<int>& A) {
        int len = A.size();
        for(int i  = 0; i < len; ++i)
            for(int j = i + 1; j < len; ++j)
                if(A[i] == A[j])
                    return A[i];
    }
};
```
