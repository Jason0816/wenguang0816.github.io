---
title: LeetCode刷题：942.DI String Match
date: 2019-02-24 13:29:00
categories: LeetCode
tags:
  - LeetCode
---
#### [942\. DI String Match](https://leetcode-cn.com/problems/di-string-match/)
Given a string `S` that **only** contains "I" (increase) or "D" (decrease), let `N = S.length`.
Return **any** permutation `A` of `[0, 1, ..., N]` such that for all `i = 0, ..., N-1`:
*   If `S[i] == "I"`, then `A[i] < A[i+1]`
*   If `S[i] == "D"`, then `A[i] > A[i+1]`
*   
**Example 1:**

**Input:** `"IDID"`

**Output:** `[0,4,1,3,2]`

**Example 2:**

**Input:** `"III"`

**Output:** `[0,1,2,3]`

**Example 3:**

**Input:** `"DDI"`

**Output:** `[3,2,0,1]`

**Note:**
1.  `1 <= S.length <= 10000`
2.  `S` only contains characters `"I"` or `"D"`.
##### 解题思路：
如果字符为`I`，则数字从0开始递增，如果字符为`D`，则数字从N开始递减；
##### 解答：
```
class Solution {
public:
    vector<int> diStringMatch(string S) {
        int len = S.length();
        vector<int> A;
        int incNum = 0;
        int decNum = len;
        for(int i = 0; i < len; ++i)
        {
            if(S[i] == 'I')
                A.push_back(incNum++);
            else
                A.push_back(decNum--);
        }
        A.push_back(incNum);
        return A;
    }
};
```