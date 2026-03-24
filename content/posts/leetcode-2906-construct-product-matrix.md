---
date: '2026-03-24T09:38:39+08:00'
draft: false 
title: 'Leetcode 2906 - Construct Product Matrix'
tags:
- LeetCode
---
## Solution
對每個位置存 prefix product 跟 suffix product (這個位置**以前**所有元素的乘積，和這個位置**以後**所有元素的 product)，最後把這兩個數字乘起來(記得模12345)就好了:)))
```cpp
class Solution {
public:
    vector<vector<int>> constructProductMatrix(vector<vector<int>>& grid) {
        const int mod = 12345;
        int n = grid.size(), m = grid[0].size();

        vector<vector<int>> prefixP(n, vector<int>(m, 1));
        vector<vector<int>> suffixP(n, vector<int>(m, 1));
        long long cur = 1;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (i == j && i == 0) {
                    cur = (cur * grid[i][j]) % mod;
                    continue;
                }
                
                prefixP[i][j] = cur % mod;
                cur  = (cur * grid[i][j]) % mod;

            }
        }

        cur = 1;
        for (int i = n-1; i >= 0; i--) {
            for (int j = m-1; j >= 0; j--) {
                if (i == n-1 && j == m-1) {
                    cur = (cur * grid[i][j]) % mod;
                    continue;
                }
                
                suffixP[i][j] = cur % mod;
                cur  = (cur * grid[i][j]) % mod;
            }
        }

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                grid[i][j] = (prefixP[i][j] * suffixP[i][j]) % mod;
            }
        }

        return grid;
    }
};
```
