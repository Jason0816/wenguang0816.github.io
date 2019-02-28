---
title: LeetCode刷题：867.Transpose Matrix
date: 2019-02-24 13:25:00
categories: LeetCode
tags:
  - 数组
---
#### [867\. Transpose Matrix](https://leetcode-cn.com/problems/transpose-matrix/)
Given a matrix `A`, return the transpose of `A`.
The transpose of a matrix is the matrix flipped over it's main diagonal, switching the row and column indices of the matrix.

**Example 1:**
>**Input:** `[[1,2,3],[4,5,6],[7,8,9]]`
>
>**Output:** `[[1,4,7],[2,5,8],[3,6,9]]`

**Example 2:**
>**Input:** `[[1,2,3],[4,5,6]]`
>
>**Output:** `[[1,4],[2,5],[3,6]]`

**Note:**
1.  `1 <= A.length <= 1000`
2.  `1 <= A[0].length <= 1000`
##### 解题思路：
A为`m * n`的矩阵，所以A的转置为`n * m`的矩阵，故先创建`n * m`的矩阵`result`，通过遍历令`result[j][i] = A[i][j]`,最后返回`result`
##### 解答：
```cpp
class Solution {
public:
    vector<vector<int>> transpose(vector<vector<int>>& A) {
        int m = A.size();
        int n = A[0].size();
        /*
         * A为m * n的矩阵，则A的转置为n * m的矩阵
         * 所以定义result为n * m的矩阵
         */
        vector<vector<int>> result(n);
        for(int i = 0; i < n; ++i)
            result[i].resize(m);
        for(int i = 0; i < m; ++i)
        {  
            for(int j = 0; j < n; ++j)
            {
                result[j][i] = A[i][j];
            }
        }
        return result;
    }
};
```