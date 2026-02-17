---
date: '2026-02-17T11:42:06+08:00'
draft: false
title: 'Leetcode 401 - Binary Watch'
---
## Approach 1 - Classic Enumeration
把所有小時、分鐘的組合列出來，然後看他們的 set bit 的數量加起來是不是 `turnedOn`。這是我一開始想到的作法，此外似乎 C++ 20 就開始有 `std::format()` 可以用了，還蠻酷的:) 我第一次使用
### AC Code
```cpp
class Solution {
public:
    vector<string> readBinaryWatch(int turnedOn) {
        vector<string> ans;
        for (int h = 0; h < 12; h++) {
            for (int m = 0; m < 60; m++) {
                int t1 = __builtin_popcount(h);
                int t2 = __builtin_popcount(m);
                if (t1+t2 == turnedOn) {
                    string time = std::format("{}:{:02}", h, m);
                    ans.push_back(time);
                }
            }
        }
        return ans;
    }
};
```
## Approach 2 - Binary Enumeration
這是官解提供的作法之一，因為小時跟分鐘加起來有 10 個 bits，所以有 `2^10=1024` 種可能性，我們可以透過枚舉 `0~1024` 的 i，i 從 MSB 開始數四位是小時，剩下六位是分鐘，透過基本的位元運算以及 Approach 1 的一些觀念就可以做出來了。anyway 這題非常簡單，依然是不用動腦的 Easy 類別。

然後這個作法比 Approach 快了一點，but idk why.
### AC Code
```cpp
class Solution {
public:
    vector<string> readBinaryWatch(int turnedOn) {
        vector<string> ans;
        for (int i = 0; i < 1024; i++) {
            int h = i>>6, m = i&63;
            if (h < 12 && m < 60 && __builtin_popcount(h)+__builtin_popcount(m)==turnedOn) {
                ans.emplace_back(std::format("{}:{:02}", h, m));
            }
        }
        return ans;
    }
};
```
## Untitled
今天是大年初一，祝各位新年順利！
