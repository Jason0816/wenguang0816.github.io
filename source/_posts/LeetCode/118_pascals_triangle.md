---
title: LeetCode刷题：118.Pascal's Triangle
date: 2019-02-24 13:03:00
categories: LeetCode
tags:
  - 数组
---
#### [118\. Pascal's Triangle](https://leetcode-cn.com/problems/pascals-triangle/)
Given a non-negative integer *numRows*, generate the first *numRows* of Pascal's triangle.
![In Pascal's triangle, each number is the sum of the two numbers directly above it.](http://upload-images.jianshu.io/upload_images/14484228-f1bcb06c89999105.gif?imageMogr2/auto-orient/strip)

**Example:**

**Input:** `5`

**Output:**
```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```
##### 解题思路：
根据杨辉三角的特点创建容器，并将每行开头和结尾赋值为1，当行数大于2时，根据杨辉三角的运算规则进行运算
##### 解答：
```cpp
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>> res(numRows, vector<int>());
        for (int i = 0; i < numRows; ++i)
        {
            res[i].resize(i + 1);  //确定每行数字的个数
            //每行开头和结尾都为1
            res[i][0] = 1;
            res[i][i] = 1;
        }
        if (numRows > 2)
        {
            for (int i = 2; i < numRows; ++i) 
            {
                for (int j = 1; j < i; ++j) 
                    res[i][j] = res[i-1][j] + res[i-1][j-1];
            }
        }
	    return res;
    }
};
```