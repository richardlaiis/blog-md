---
date: '2026-03-25T20:13:03+08:00'
draft: false
title: 'Leetcode 3546 - Equal Sum Grid Partition I'
---
## 解法
基本上就是對於 row 跟 column 存 prefix sum，然後看當前累積的和有沒有機會等於全部元素的和除以 2。這是一題應該被放在簡單類別的中等題。
```cpp
class Solution {
public:
    bool canPartitionGrid(vector<vector<int>>& grid) {
        int m = grid.size(), n = grid[0].size();
        long long sum = 0;
        for (auto i:grid) {
            for (auto j:i) sum += j;
        }

        if (sum & 1) return false;
        sum >>= 1;

        long long cur_hor = 0;
        for (int i = 0; i < m-1; i++) {
            for (int j = 0; j < n; j++) cur_hor += grid[i][j];
            if (cur_hor == sum) return true;
        }

        long long cur_ver = 0;
        for (int j = 0; j < n-1; j++) {
            for (int i = 0; i < m; i++) cur_ver += grid[i][j];
            if (cur_ver == sum) return true;
        }

        return false;
    }
};
```
## 不知道標題要取什麼
之後想養成跑步的習慣，天氣跟時間允許的話就跑，code跟我至少要有一個是跑得動的～XD 感覺自己還在因為某些事造成的創傷所苦，希望趕快好起來！不然有的時候我真的好怕自己失去面對一切的動力，或許有時候我還是該跟人類說話，我不知道(?)
