---
title: LeetCode刷题：78.Subsets
date: 2019-02-24 13:02:00
categories: LeetCode
tags:
  - 位运算
  - 数组
  - 回溯算法
---
#### [78\. Subsets](https://leetcode-cn.com/problems/subsets/)
Given a set of **distinct** integers, *nums*, return all possible subsets (the power set).
**Note:** The solution set must not contain duplicate subsets.

**Example:**

**Input:** nums = [1,2,3]

**Output:**
```
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```
##### 解题思路：
```
对集合的每一个元素进行迭代，迭代时，我们保留原来的子集，并在原来的子集后面加入新的元素，之后再加入集合
迭代过程如下
[] -> 1 -> [1]
[] [1] -> 2 -> [2] [1,2]
[] [1] [2] [1,2] -> 3 -> [3] [1,3] [2,3] [1,2,3]
[] [1] [2] [1,2] [3] [1,3] [2,3] [1,2,3]
```
##### 解答：
```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> result;
        vector<int> tmp;
        result.push_back(tmp);
        int len = nums.size();
        for(int i =0; i < len; ++i){
            int resLen = result.size();
            for(int j=0; j < resLen; ++j){
                vector<int> tmp = result[j];
                tmp.push_back(nums[i]);
                result.push_back(tmp);
            }
        }
        return result;
    }
};

```