> yyyy-mm-dd

---

[toc]

---

# Array / String

## [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array)  (☆) ͏

- Inverse
- two pointer

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i = m - 1
        j = n - 1
        k = m + n - 1
        while k >= 0 and j >= 0:
            if i >= 0 and nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
            # print(nums1)
```

## [Remove Element](https://leetcode.com/problems/remove-element)  (☆) ͏

- 

```python

```

## [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array)  (☆) ͏

- 

```python

```

## [Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii)  (☆☆) ͏

- 

```python

```

## [Majority Element](https://leetcode.com/problems/majority-element)  (☆) ͏

- 

```python

```

## [Rotate Array](https://leetcode.com/problems/rotate-array)  (☆☆) ͏

- 

```python

```

## [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock)  (☆) ͏

- 

```python

```

## [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii)  (☆☆) ͏

- 

```python

```

## [Jump Game](https://leetcode.com/problems/jump-game)  (☆☆) ͏

- 

```python

```

## [Jump Game II](https://leetcode.com/problems/jump-game-ii)  (☆☆) ͏

- 

```python

```

## [H-Index](https://leetcode.com/problems/h-index)  (☆☆) ͏

- 

```python

```

## [Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1)  (☆☆) ͏

- 

```python

```

## [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self)  (☆☆) ͏

- 

```python

```

## [Gas Station](https://leetcode.com/problems/gas-station)  (☆☆) ͏

- 

```python

```

## [Candy](https://leetcode.com/problems/candy)  (☆☆☆) ͏

- 

```python

```

## [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water)  (☆☆☆) ͏

- 

```python

```

## [Roman to Integer](https://leetcode.com/problems/roman-to-integer)  (☆) ͏

- 

```python

```

## [Integer to Roman](https://leetcode.com/problems/integer-to-roman)  (☆☆) ͏

- 

```python

```

## [Length of Last Word](https://leetcode.com/problems/length-of-last-word)  (☆) ͏

- 

```python

```

## [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix)  (☆) ͏

- 

```python

```

## [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string)  (☆☆) ͏

- 

```python

```

## [Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion)  (☆☆) ͏

- 

```python

```

## [Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string)  (☆) ͏

- 

```python

```

## [Text Justification](https://leetcode.com/problems/text-justification)  (☆☆☆) ͏

- 

```python

```

