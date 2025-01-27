> yyyy-mm-dd

---

[toc]

---

# Math

## [Palindrome Number](https://leetcode.com/problems/palindrome-number)  (☆) ͏

- 也可以直接和[::-1]做比较

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        if x < 0:
            return False
        digits = str(x)
        n = len(digits)
        for i in range(n // 2):
            if digits[i] != digits[n - i - 1]:
                return False
        return True
```

## [Plus One](https://leetcode.com/problems/plus-one)  (☆) ͏

- 

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        carry = 0
        n = len(digits)
        for i in range(n - 1, -1, -1):
            if digits[i] == 9:
                digits[i] = 0
                carry = 1
            else:
                digits[i] += 1
                return digits
        if carry:
            return [1] + digits
        return digits
```

## [Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes)  (☆☆) ͏

- 

```python

```

## [Sqrt(x)](https://leetcode.com/problems/sqrtx)  (☆) ͏

- 寻找一个范围内的有序列中的值：二分法

```python
class Solution:
    def mySqrt(self, x: int) -> int:
        l = 0
        r = x
        while l < r:
            m = l + (r - l) // 2 + 1
            if m * m > x:
                r = m - 1
            elif m * m == x:
                return m
            else:
                l = m
        return l
```

## [Pow(x, n)](https://leetcode.com/problems/powx-n)  (☆☆) ͏

- 

```python

```

## [Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line)  (☆☆☆) ͏

- 

```python

```

