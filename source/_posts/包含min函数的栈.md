---
title: 包含min函数的栈
date: 2020-02-07 14:47:58
tags:
---
定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。

```cpp
class Solution {
public:
    stack<int> data, mins;
    void push(int value) {
        data.push(value);
        if (mins.size() > 0)
        {
            const int old_min = mins.top();
            if (old_min < value)
            {
                mins.push(old_min);
            }
            else
            {
                mins.push(value);
            }
        }
        else
        {
            mins.push(value);
        }
    }
    void pop() {
        data.pop();
        mins.pop();
    }
    int top() {
        return data.top();
    }
    int min() {
        return mins.top();
    }
};
```