---
title: 和为S的两个数字
date: 2020-02-08 10:55:46
tags:
---

输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

两端向内，小了挪大，大了挪小

```cpp
class Solution {
public:
    vector<int> FindNumbersWithSum(vector<int> array,int sum) {
        vector<int> result;
        if (array.size() > 1)
        {
            auto start = array.begin(), end = array.end() - 1;
            while (start < end)
            {
                if (*start + *end == sum)
                {
                    result.push_back(*start);
                    result.push_back(*end);
                    break;
                }
                else if (*start + *end < sum)
                {
                    start++;
                }
                else
                {
                    end--;
                }
            }
        }
        return result;
    }
};
```
