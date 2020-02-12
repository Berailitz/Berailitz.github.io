---
title: 最小的K个数
date: 2020-02-07 17:00:33
tags:
---

输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

partition、堆、红黑树

```cpp
class Solution {
public:
    void swap(vector<int> &input, const int a, const int b)
    {
        int temp = input[a];
        input[a] = input[b];
        input[b] = temp;
    }
    int partition(vector<int> &input, const int start, const int end)
    {
        if (input.size() == 0)
        {
            return 0;
        }
        else
        {
            const int mid_value = input[0];
            int left = start;
            int right = end;
            while (left < right)
            {
                while (input[right] >= mid_value && left < right)
                {
                    right--;
                }
                swap(input, right, left);
                while (input[left] <= mid_value && left < right)
                {
                    left++;
                }
                swap(input, right, left);
            }
            return left;
        }
    }
    vector<int> GetLeastNumbers_Solution(vector<int> input, int k) {
        if (k == 0 || k > input.size())
        {
            return vector<int>();
        }
        else
        {
            int current_k = -1;
            while (current_k != k)
            {
                if (current_k < k)
                {
                    current_k = partition(input, current_k + 1, input.size() - 1);
                }
                else
                {
                    current_k = partition(input, 0, current_k - 1);
                }
            }
            return vector<int>(input.begin(), input.begin() + current_k);
        }
    }
};
```
