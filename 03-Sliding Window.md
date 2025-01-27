> yyyy-mm-dd

---

[toc]

---

# Sliding Window

## [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum)  (☆☆) ͏

- 

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        if not nums:
            return 0
        l = 0
        r = 0
        result = len(nums) + 1
        current = 0
        for r in range(len(nums)):
            current += nums[r]
            while current - nums[l] >= target:
                current -= nums[l]
                l += 1
            if current >= target:
                result = min(result, r - l + 1)
        if result >len(nums):
            return 0
        return result
```

## [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters)  (☆☆) ͏

- 

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        if not s:
            return 0

        n = len(s)
        l = 0
        result = 1
        current = set()
        current.add(s[l])
        for r in range(1, n):
            while s[r] in current:
                current.remove(s[l])
                l += 1
            current.add(s[r])
            result = max(result, r - l + 1)
        return result
```

## [Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words)  (☆☆☆) ͏

- 

```python

```

## [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring)  (☆☆☆) ͏

- 

```python

```

