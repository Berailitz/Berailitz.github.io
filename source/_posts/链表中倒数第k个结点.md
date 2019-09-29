---
title: 链表中倒数第k个结点
date: 2019-09-30 00:54:54
tags:
---

输入一个链表，输出该链表中倒数第k个结点。

快慢指针，快指针先走`k`步。


``` cpp
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
    ListNode* FindKthToTail(ListNode* pListHead, unsigned int k) {
        if (pListHead == nullptr || k == 0)
        {
            return nullptr;
        }
        else
        {
            ListNode *left = pListHead, *right = pListHead;
            while (k > 1)
            {
                if (right->next == nullptr)
                {
                    left = nullptr;
                    break;
                }
                else
                {
                    right = right->next;
                }
                k--;
            }
            while (right->next != nullptr)
            {
                right = right->next;
                left = left->next;
            }
            return left;
        }
    }
};
```
