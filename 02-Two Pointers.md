> yyyy-mm-dd

---

[toc]

---

# Two Pointers

## [Valid Palindrome](https://leetcode.com/problems/valid-palindrome)  (☆) ͏

- isalnum()
- char.lower()

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s_list = [char.lower() for char in s if char.isalnum()]
        l = 0
        r = len(s_list) - 1
        while l <= r:
            if s_list[l] == s_list[r]:
                l += 1
                r -= 1
                continue
            else:
                return False
        return True
```

## [Is Subsequence](https://leetcode.com/problems/is-subsequence)  (☆) ͏

- 

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i = 0
        j = 0
        n = len(s)
        m = len(t)
        while i < n and j < m:
            if s[i] == t[j]:
                i += 1
                j += 1
            else:
                j += 1
        if i == n:
            return True
        else:
            return False
```

## [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted)  (☆☆) ͏

- 

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        if not numbers:
            return -1

        l = 0
        r = len(numbers) - 1
        while l < r:
            now = numbers[l] + numbers[r]
            if now == target:
                return l + 1, r + 1
            elif now > target:
                r -= 1
            else:
                l += 1
        return -1
```

## [Container With Most Water](https://leetcode.com/problems/container-with-most-water)  (☆☆) ͏

- 

```python

```

## [3Sum](https://leetcode.com/problems/3sum)  (☆☆) ͏

- 不管是第一个数还是2pointer里面的数字，都是遇到重复的就避开。这样只有第一次遇到一个数的时候才会加入判断。既使得可以遍历所有可能（包括重复的元素），又不会计入重复的三元组

```python

```

