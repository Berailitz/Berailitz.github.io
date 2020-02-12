---
title: 和为S的连续正数序列
date: 2020-02-08 10:48:27
tags:
---

所有和为S的连续正数序列（至少有2个数）

1~2开始，小了挪右端点，大了挪左端点

```cpp
class Solution {
public:
    vector<vector<int> > FindContinuousSequence(int sum) {
        vector<vector<int>> results;
        if (sum >= 3)
        {
            int a = 1, b = 2, current_sum = 3, mid = sum / 2;
            while (a <= mid)
            {
                if (current_sum < sum)
                {
                    b++;
                    current_sum += b;
                }
                else
                {
                    if (current_sum == sum)
                    {
                        vector<int> r;
                        for (int i = a; i <= b; i++)
                        {
                            r.push_back(i);
                        }
                        results.push_back(r);
                    }
                    current_sum -= a;
                    a++;
                }
            }
        }
        return results;
    }
};
```
