---
date: '2026-02-05T08:24:06+08:00'
draft: false
title: 'Leetcode 3379 - Transformed Array'
---
## Approach
基本上照著題目的敘述寫就好了，很簡單。不過取模的時候要注意，C的模運算不一定會是正的，所以寫的時候要避免產生負的index，我竟然不知道這件事情qwq
## Code
```c
int* constructTransformedArray(int* nums, int numsSize, int* returnSize) {
    *returnSize = numsSize;
    int* result = (int*)malloc(sizeof(int) * numsSize);
    for (int i = 0; i < numsSize; i++) {
        result[i] = nums[((i + nums[i])%numsSize + numsSize) % numsSize];
    }
    return result;
}
```
