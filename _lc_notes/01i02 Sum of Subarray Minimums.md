---
categories: array stack
date: 2024-01-01 00:00:00 +0000
index: '01i02'
layout: post
status: done
title: 01i02 Sum of Subarray Minimums
tags: [monotonic stack]
---

## Sum of Subarray Minimums [LC#907]
> Given an array of integers `arr`, find the sum of `min(b)`, where `b` ranges over every (contiguous) subarray of `arr`. Since the answer may be large, return the answer modulo $10^9 + 7$.

### Intuition
If `arr[k]` is minimum element in `[i, j]`, then `arr[k]` appears in `(k - i) * (j - k)` subarrays. 

**Monotonic Stack**
```python
def sum_subarrray_mins(arr: List[int]) -> int:
    stack = []
    sum_of_minimums = 0
    arr.append(-math.inf) # so that everything gets popped out in the end
    for i in range(len(arr)):
        while stack and arr[stack[-1]] >= arr[i]:
            mid = stack.pop()
            left = -1 if not stack else stack[-1]
            right = i

            count = (mid - left) * (right - mid)
            sum_of_minimums += (count * arr[mid])
        stack.append(i)
    return sum_of_minimums
```
### Time Complexity
- $T(n) = O(n)$ ; $S(n) = O(n)$