---
date: 2024-01-01 00:00:00 +0000
index: 01j01
layout: post
status: done
title: 01j01 Maximum Subarray Sum
---

## Maximum Subarray Sum [LC#53]
> Given an integer array `nums`, find the subarray with the largest sum, and return its sum.


**Kadane's algorithm**
- Find the max sum of subarray ending at location `i`.
- $T(n) = O(n)$; $S(n) = O(1)$

```python
def max_subarray_sum(nums: List[int]) -> int:
    curr, ans = 0, nums[0]
    for num in nums:
        curr = max(curr + num, num)
        ans = max(ans, curr)
    return ans
```