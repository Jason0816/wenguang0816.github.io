---
title: LeetCode刷题：944.Delete Columns to Make Sorted
date: 2019-02-24 13:30:00
categories: LeetCode
tags:
  - LeetCode
---
#### [944\. Delete Columns to Make Sorted](https://leetcode-cn.com/problems/delete-columns-to-make-sorted/)
We are given an array `A` of `N` lowercase letter strings, all of the same length.
Now, we may choose any set of deletion indices, and for each string, we delete all the characters in those indices.
For example, if we have an array `A = ["abcdef","uvwxyz"]` and deletion indices `{0, 2, 3}`, then the final array after deletions is `["bef", "vyz"]`, and the remaining columns of `A` are `["b","v"]`, `["e","y"]`, and `["f","z"]`.  (Formally, the `c`-th column is `[A[0][c], A[1][c], ..., A[A.length-1][c]]`.)
Suppose we chose a set of deletion indices `D` such that after deletions, each remaining column in A is in **non-decreasing** sorted order.
Return the minimum possible value of `D.length`.

**Example 1:**

**Input:**` ["cba","daf","ghi"]`

**Output:** `1`

**Explanation:** 
After choosing D = {1}, each column `["c","d","g"]` and `["a","f","i"]` are in non-decreasing sorted order.
If we chose D = {}, then a column `["b","a","h"]` would not be in non-decreasing sorted order.

**Example 2:**

**Input:** `["a","b"]`

**Output:** `0`

**Explanation:** `D = {}`

**Example 3:**

**Input:** `["zyx","wvu","tsr"]`

**Output:** `3`

**Explanation:** `D = {0, 1, 2}`

**Note:**
1.  `1 <= A.length <= 100`
2.  `1 <= A[i].length <= 1000`
##### 解题思路：
题意解析，非降序意味着列中不存在降序
故进行两次for循环，外层循环为列，内层循环为行，如果前一行某列字母大于后一行（ASCII），则返回值+1；
##### 解答：
```cpp
class Solution {
public:
    int minDeletionSize(vector<string>& A) {
        int strLen = A[0].length();
        int vLen = A.size();
        int result = 0;
        //列序号
        for(int i = 0; i < strLen; ++i)
        {
            //行序号
            for(int j = 0; j < vLen - 1; ++j)
            {
                if(A[j][i] > A[j+1][i])
                {
                    result++;
                    break;//跳出循环
                }
            }
        }
        return result;
    }
};
```