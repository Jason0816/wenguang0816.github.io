---
title: LeetCode刷题：1.Two Sum
date: 2019-02-24 13:01:00
categories: LeetCode
tags:
  - 数组
  - 哈希表
---
#### [1\. Two Sum](https://leetcode-cn.com/problems/two-sum/)
Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.
You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

**Example:**

>Given nums = [2, 7, 11, 15], target = 9,
>
>Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].

##### 解题思路：
对数组进行遍历，将符合条件的数组元素返回；
另有高效率**遍历哈希表法**，待研究。
##### 解答：
```cpp
//暴力法：遍历整个数组，耗时较长（72ms）
class Solution {
public:
	vector<int> twoSum(vector<int>& nums, int target) 
	{
		vector<int> result;
        int size = nums.size();
		for (int i = 0; i < size; i++)
		{
            int complement = target - nums[i];
			for (int j = i + 1; j < size; j++)
			{
				if (nums[j] == complement)
				{
					result.push_back(i);
					result.push_back(j);
					return result;
				}	
			}
		}
		return result;
	}
};
```
