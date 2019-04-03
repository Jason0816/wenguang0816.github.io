---
title: 反转链表
date: 2019-04-02 20:00:00
img: https://upload-images.jianshu.io/upload_images/14484228-8b99b537751faec0.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer：刷题笔记第二天：15、反转链表
categories: 剑指 offer
tags:
  - 链表
---
### [15\. 反转链表](https://www.nowcoder.com/practice/75e878df47f24fdc9dc3e400ec6058ca?tpId=13&tqId=11168&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
输入一个链表，反转链表后，输出新链表的表头。

### 解题思路：
通过3个指针遍历一遍链表，实现链表反转，详细过程参见[（转载）漫画：如何将一个链表“逆序”？](http://blog.wenguang0816.top/2019/03/20/reverse-linked-list/)

### 解答：

```cpp
/*
struct ListNode {
	int val;
	struct ListNode *next;
	ListNode(int x) :
			val(x), next(NULL) {
	}
};*/
class Solution {
public:
    ListNode* ReverseList(ListNode* pHead) {
        if(pHead == NULL || pHead->next == NULL)
            return pHead;
        ListNode *p1 = pHead;
        ListNode *p2 = pHead->next;
        ListNode *p3 = NULL;
        while(p2 != NULL)
        {
            p3 = p2->next;
            p2->next = p1;
            p1 = p2;
            p2 = p3;
        }
        pHead->next = NULL;
        pHead = p1;
        return pHead;
    }
};
```