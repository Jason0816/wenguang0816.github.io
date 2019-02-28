---
title: LeetCode刷题：657.Robot Return to Origin
date: 2019-02-24 13:18:00
categories: LeetCode
tags:
  - LeetCode
---
#### [657\. Robot Return to Origin](https://leetcode-cn.com/problems/robot-return-to-origin/)
There is a robot starting at position (0, 0), the origin, on a 2D plane. Given a sequence of its moves, judge if this robot **ends up at (0, 0)** after it completes its moves.
The move sequence is represented by a string, and the character moves[i] represents its ith move. Valid moves are R (right), L (left), U (up), and D (down). If the robot returns to the origin after it finishes all of its moves, return true. Otherwise, return false.

**Note**: The way that the robot is "facing" is irrelevant. "R" will always make the robot move to the right once, "L" will always make it move left, etc. Also, assume that the magnitude of the robot's movement is the same for each move.

**Example 1:**
>**Input:** "UD"
>
>**Output:** true 
>
>**Explanation**: The robot moves up once, and then down once. All moves have the same magnitude, so it ended up at the origin where it started. Therefore, we return true.

**Example 2:**
>**Input:** "LL"
>
>**Output:** false
>
>**Explanation**: The robot moves left twice. It ends up two "moves" to the left of the origin. We return false because it is not at the origin at the end of its moves.
##### 解题思路：
设置四个标志位，利用switch-case判断moves的值，相应标志位+1。
当‘上’=‘下’并且‘左’=‘右’的时候，机器人回到原点。
##### 解答：
```cpp
// code 1：
// 8ms
class Solution {
public:
    bool judgeCircle(string moves) {
        vector<int> sign(4,0);
        for(auto c : moves)
        {
            switch(c)
            {
                case 'U':
                    sign[0]++;
                    break;
                case 'D':
                    sign[1]++;
                    break;
                case 'L':
                    sign[2]++;
                    break;
                case 'R':
                    sign[3]++;
                    break;
            }
        }
        return sign[0] == sign[1] && sign[2] == sign[3];
    }
};
// code 2：
// 4ms
class Solution {
public:
    bool judgeCircle(string moves) {
        int a = 0, b = 0, c = 0, d = 0;
        for(int i=0;i<moves.size();i++){
            a+=moves[i]=='R';
            b+=moves[i]=='L';
            c+=moves[i]=='U';
            d+=moves[i]=='D';
        }
        return a == b && c == d;
    }
};

```