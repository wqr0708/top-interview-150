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

```

## [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted)  (☆☆) ͏

- 

```python

```

## [Container With Most Water](https://leetcode.com/problems/container-with-most-water)  (☆☆) ͏

- 

```python

```

## [3Sum](https://leetcode.com/problems/3sum)  (☆☆) ͏

- 不管是第一个数还是2pointer里面的数字，都是遇到重复的就避开。这样只有第一次遇到一个数的时候才会加入判断。既使得可以遍历所有可能（包括重复的元素），又不会计入重复的三元组

```python

```

