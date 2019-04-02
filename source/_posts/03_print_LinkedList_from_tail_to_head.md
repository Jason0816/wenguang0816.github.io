---
title: 从尾到头打印链表
date: 2019-04-02 15:00:00
img: https://upload-images.jianshu.io/upload_images/14484228-9d6dab50e206e76a.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer： 刷题笔记第二天：  3、从尾到头打印链表
categories: 剑指 offer
tags:
  - 链表
  - 栈
  - 头插法
---
### [3\. 从尾到头打印链表](https://www.nowcoder.com/practice/d0267f7f55b3412ba93bd35cfa8e8035?tpId=13&tqId=11156&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。

### 解题思路：
+ 思路1: 利用栈先进后出的性质，将链表中的数据`push`到栈中，然后`pop`到`vector`中
+ 思路2: 利用头插法，遍历链表，将链表元素插入到`vector`头部(缺点：需要多次分配空间)

### 解答：

```cpp
/*
 *  struct ListNode {
 *        int val;
 *        struct ListNode *next;
 *        ListNode(int x) :
 *              val(x), next(NULL) {
 *        }
 *  };
 */

// 解法1:
class Solution {
public:
    vector<int> printListFromTailToHead(ListNode* head) {
        vector<int> ans;
        stack<int> nodes;
        ListNode* pNode = head;
        while(pNode != NULL)
        {
            nodes.push(pNode -> val);
            pNode = pNode -> next;
        }
        while(!nodes.empty())
        {
            ans.push_back(nodes.top());
            nodes.pop();
        }
        return ans;
    }
};
//解法2:
class Solution {
public:
    vector<int> printListFromTailToHead(ListNode* head) {
        vector<int> ans;
        ListNode* pNode = head;
        while(pNode != NULL)
        {
            ans.insert(ans.begin(), pNode -> val);
            pNode = pNode -> next;
        }
        return ans;
    }
};
```