---
date: '2026-02-15T09:29:08+08:00'
draft: false
title: 'Leetcode 67 - Add Binary'
tags:
- LeetCode
- 67
categories:
- LeetCode
---

## Solution
```cpp
class Solution {
public:
    string addBinary(string a, string b) {
        int n = a.length(), m = b.length();
        int k = max(n, m);
        if (n < m) {
            for (int i = 0; i < m-n; i++) a = "0" + a;
        } else {
            for (int i = 0; i < n-m; i++) b = "0" + b;
        }
        
        string res = "";
        int carry = 0;
        for (int i = k-1; i >= 0; i--) {
            int x = a[i]-'0', y = b[i]-'0';
            int sum = x + y + carry;
            if (sum == 0) res = "0" + res, carry = 0;
            else if (sum == 1) res = "1" + res, carry = 0;
            else if (sum == 2) res = "0" + res, carry = 1;
            else if (sum == 3) res = "1" + res, carry = 1;
        }
        if (carry) res = "1" + res;
        return res;
    }
};
```

---

![](67.png)

~~我很抱歉~~
