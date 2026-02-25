---
date: '2026-02-25T09:20:02+08:00'
draft: false
title: 'Leetcode 1356 - Sort Integers by the Number of 1 Bits'
---
## Approach 1
搭車時用手機打的w
```cpp
class Solution {
public:
    vector<int> sortByBits(vector<int>& arr) {
        int n = arr.size();
        vector<pair<int,int>> v(n);
        for (int i = 0; i < n; i++) {
            v[i] = std::make_pair(__builtin_popcount(arr[i]), arr[i]);
        }
        sort(v.begin(), v.end());
        for (int i = 0; i < n; i++) {
            arr[i] = v[i].second;
        }
        return arr;
    }
};
```
## Approach 2
使用 Brian Kernighan's algorithm 來更有效率的找出一個數的 set bit 有幾個 (即 hamming weight)。
```cpp
class Solution {
public:
    static int findWeight(int x) {
        int res = 0;
        while (x) {
            res++;
            x &= (x-1);
        }
        return res;
    }
    static bool cmp(int a, int b) {
        if (findWeight(a) == findWeight(b)) {
            return a < b;
        }
        return findWeight(a) < findWeight(b);
    }
    vector<int> sortByBits(vector<int>& arr) {
        sort(arr.begin(), arr.end(), cmp);
        return arr;
    }
};
```
