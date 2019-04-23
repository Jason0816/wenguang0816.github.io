---
title: 链表中环的入口节点
date: 2019-04-23 19:30:00
img: https://upload-images.jianshu.io/upload_images/14484228-7e0e3295e6d65b70.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer：55、链表中环的入口节点
categories: 剑指 offer
tags:
  - 链表
  - 鲁棒性
---
### [55\. 链表中环的入口节点](https://www.nowcoder.com/practice/253d2c59ec3e4bc68da16833f79a38e4?tpId=13&tqId=11208&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
给一个链表，若其中包含环，请找出该链表的环的入口结点，否则，输出null。

### 解题思路：
+ 确定是否有环：定义两个指针，同时从链表头节点出发，慢指针每次走一步，快指针每次走两步，如果快指针追上了慢指针，那么链表中有环，如果快指针走到了链表末尾都没有追上慢指针，那么链表中没有环
+ 找到入口节点：
    - 确定环内节点数目：快指针与慢指针相遇肯定位于环内，可以记录该相遇节点，然后从该节点出发，当再次回到这个节点经过了`k`个节点，即环内节点数目为`k`
    - 定义两个指针P1和P2指向链表的头节点，如果环内有`k`个节点，那么P1先在链表上向前移动`k`步，然后两个指针以相同的速度向前移动。当P2指向入环节点时，P1已经绕环一周，重新回到入口节点

异常处理：
1. 输入为空指针
2. 链表无环
3. 链表只有一个节点

### 解答：

```cpp
/*
struct ListNode {
    int val;
    struct ListNode *next;
    ListNode(int x) :
        val(x), next(NULL) {
    }
};
*/
class Solution {
public:
    ListNode* MeetingNode(ListNode* pHead)
    {
        if(pHead == nullptr)
            return nullptr;
        ListNode* pSlow = pHead->next;
        if(pSlow == nullptr)
            return nullptr;
        ListNode* pFast = pSlow->next;
        while(pFast != nullptr && pSlow != nullptr)
        {
            if(pFast == pSlow)
                return pFast;
            // pSlow走一步
            pSlow = pSlow->next;
            // pFast走两步
            pFast = pFast->next;
            if(pFast != nullptr)
                pFast = pFast->next;
        }
        // 不存在环
        return nullptr;
    }
public:
    ListNode* EntryNodeOfLoop(ListNode* pHead)
    {
        ListNode* meetingNode = MeetingNode(pHead);
        if(meetingNode == nullptr)
            return nullptr;
        // 获取环中节点的数目
        int nodesInLoop = 1;
        ListNode* pNode1 = meetingNode;
        while(pNode1->next != meetingNode)
        {
            pNode1 = pNode1->next;
            ++nodesInLoop;
        }
        // 先移动pNode1，次数为环中节点的数目
        pNode1 = pHead;
        for(int i = 0; i < nodesInLoop; ++i)
            pNode1 = pNode1->next;
        // 再移动pNode1和pNode2
        ListNode* pNode2 = pHead;
        while(pNode1 != pNode2)
        {
            pNode1 = pNode1->next;
            pNode2 = pNode2->next;
        }
        return pNode1;
    }
};
```