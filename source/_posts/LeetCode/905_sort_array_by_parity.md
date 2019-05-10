---
title: LeetCode刷题：905.Sort Array By Parity
date: 2019-02-24 13:26:00
categories: LeetCode
tags:
  - 数组
---
#### [905\. Sort Array By Parity](https://leetcode-cn.com/problems/sort-array-by-parity/)
Given an array `A` of non-negative integers, return an array consisting of all the even elements of `A`, followed by all the odd elements of `A`.
You may return any answer array that satisfies this condition.

**Example 1:**
>**Input:** [3,1,2,4]

>**Output:** [2,4,3,1],
The outputs [4,2,3,1], [2,4,1,3], and [4,2,1,3] would also be accepted.

**Note:**
1.  `1 <= A.length <= 5000`
2.  `0 <= A[i] <= 5000`

##### 解题思路：
创建临时容器存放偶数和奇数，最后存入到结果容器并返回。
##### 解答：
```cpp
class Solution {
public:
    vector<int> sortArrayByParity(vector<int>& A) {
        vector<int> odd, even, result;
        for(auto vint = A.begin(); vint != A.end(); ++vint)
        {
            if((*vint) % 2 == 0)
                even.push_back(*vint);
            else
                odd.push_back(*vint);
        }
        result.insert(result.end(), even.begin(), even.end());//将even插入result；
        result.insert(result.end(), odd.begin(), odd.end());//将odd插入result；
        return result;
    }
};
```