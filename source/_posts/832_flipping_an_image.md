---
title: LeetCode刷题：832.Flipping an Image
date: 2019-02-24 13:23:00
categories: LeetCode
tags:
  - 数组
---
#### [832\. Flipping an Image](https://leetcode-cn.com/problems/flipping-an-image/)
Given a binary matrix `A`, we want to flip the image horizontally, then invert it, and return the resulting image.
To flip an image horizontally means that each row of the image is reversed.  For example, flipping `[1, 1, 0]` horizontally results in `[0, 1, 1]`.
To invert an image means that each `0` is replaced by `1`, and each `1` is replaced by `0`. For example, inverting `[0, 1, 1]` results in `[1, 0, 0]`.

**Example 1:**
>**Input:** [[1,1,0],[1,0,1],[0,0,0]]
>
>**Output:** [[1,0,0],[0,1,0],[1,1,1]]
>
>**Explanation:** First reverse each row: [[0,1,1],[1,0,1],[0,0,0]].
Then, invert the image: [[1,0,0],[0,1,0],[1,1,1]]

**Example 2:**
>**Input:** [[1,1,0,0],[1,0,0,1],[0,1,1,1],[1,0,1,0]]
>
>**Output:** [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]
>
>**Explanation:** First reverse each row: [[0,0,1,1],[1,0,0,1],[1,1,1,0],[0,1,0,1]].
Then invert the image: [[1,1,0,0],[0,1,1,0],[0,0,0,1],[1,0,1,0]]

**Notes:**
*   `1 <= A.length = A[0].length <= 20`
*   `0 <= A[i][j] <= 1`

##### 解题思路：
+ 翻转：利用临时数组反转
+ 反转：与1异或获得反转效果或者利用if-else判断，**不可按位取反**
##### 解答：
```cpp
class Solution {
public:
    vector<vector<int>> flipAndInvertImage(vector<vector<int>>& A) {
        for(auto vint = A.begin(); vint != A.end(); ++vint)
        {
            int len = (*vint).size();
            vector<int> tmp(len, 0);
            for(int i = 0; i < len; i++)
                tmp[i] = (*vint)[len - 1 - i];
            for(auto &i : tmp)
            {
                i ^= 1;
            }
            *vint = tmp;
        }
        return A;
    }
};
```