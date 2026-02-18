---
date: '2026-02-18T14:28:07+08:00'
draft: false
title: 'LeetCode 693 - Binary Number With Alternating Bits'
tags:
- LeetCode
categories:
- LeetCode
---
```cpp
class Solution {
public:
    bool hasAlternatingBits(int n) {

        int cur = n & 1;

        for (int i = 1; i < 31; i++) {
            if ( (n >> i) == 0 ) break;
            int nxt = (n >> i) & 1;
            if (nxt == cur) return false;
            else cur = nxt;
        }

        return true;
    }
};
```
