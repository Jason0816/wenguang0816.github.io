---
title: LeetCode刷题：771.Jewels and Stones
date: 2019-02-24 13:20:00
categories: LeetCode
tags:
  - LeetCode
---
#### [771\. Jewels and Stones](https://leetcode-cn.com/problems/jewels-and-stones/)
You're given strings `J`representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.
The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

**Example 1:**
```
Input:J = "aA", S = "aAAbbbb"
Output: 3
```
**Example 2:**
```
Input: J = "z", S = "ZZ"
Output: 0
```
**Note:**
*   `S` and `J` will consist of letters and have length at most 50.
*   The characters in `J` are distinct.

##### 解题思路：
+ 思路1： 遍历J和S，两者相等，计数+1；
+ 思路2： 创建临时数组a[256]，先以J中元素的ASCII值作为a的索引并作标记。后以S中元素的ASCII值作为a的索引，判断该位置是否为零，如果不为零，则计数+1；
+ 思路3： 和2类似，不过将大小写字母分开，减少了数组的长度。
##### 解答：
```
//code 1：
//运行时间大于4ms；
class Solution {
public:
	int numJewelsInStones(string J, string S) {
		int num = 0;
		for (int i = 0; i < J.length(); i++)
		{
			for (int j = 0; j< S.length(); j++)
				if (J[i] == S[j])
					num += 1;
		}
		return num;
	}
};
//code 2:
//运行时间4ms；
class Solution {
public:
    int numJewelsInStones(string J, string S) {
        char a[256]={0}; 
        for(int i=0;i<J.length();++i)
            a[J[i]]++; //相应字母的ASCII值作为索引；
        int ans=0; 
        for(int i=0;i<S.length();++i)
            if(a[S[i]]) 
                ans++;
        return ans;     
    }
};
// code  3:
//运行时间0ms；
class Solution {
public:
    int numJewelsInStones(string J, string S) {
        int a_upper[26] = {0} , a_lower[26] = {0};      
        for(auto ch : J)
        {
            int x;            
            if(isupper(ch))
            {
                x = ch - 'A';
                a_upper[x] = 1;
            }
            else
            {
                x = ch - 'a';
                a_lower[x] = 1;
            }
        } 
        int num = 0;
        for(auto ch : S)
        {
            int x;
            if(isupper(ch))
            {
                x = ch - 'A';
                if(a_upper[x])  ++num;
            }
            else
            {
                x = ch - 'a';
                if(a_lower[x])  ++num;
            } 
        } 
        return num;
    }
};
```