---
date: '2026-02-18T14:28:07+08:00'
draft: false
title: 'LeetCode 693 - Binary Number With Alternating Bits'
tags:
- LeetCode
categories:
- LeetCode
---
## Approach 1 (brute force)
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

---

## Approach 2 (XOR trick)
```cpp
class Solution {
public:
    bool hasAlternatingBits(int n) {
        long long x = n ^ (n>>1);
        return ((x & (x+1)) == 0);
    }
};
```

---

## Approach 3 (XOR trick too:))
```cpp
class Solution {
public:
    bool hasAlternatingBits(int n) {
        unsigned int x = n ^ (n >> 2);
        return ((x & (x-1)) == 0);
    }
};
```
