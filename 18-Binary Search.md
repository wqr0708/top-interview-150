> yyyy-mm-dd

---

[toc]

---

# Binary Search

## [Search Insert Position](https://leetcode.com/problems/search-insert-position)  (☆) ͏

- 

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:
        l = 0
        r = len(nums) - 1
        while l < r:
            m = l + (r - l) // 2
            if nums[m] == target:
                return m
            elif nums[m] < target:
                l = m + 1
            else:
                r = m - 1
        # print(l, r)
        if r < 0 or nums[r] < target:
            return r + 1
        return r
```

## [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix)  (☆☆) ͏

- 

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        if not matrix:
            return target == 0
        l = 0
        r = len(matrix) * len(matrix[0]) - 1
        n = len(matrix[0])
        while l <= r:
            m = l + (r - l)// 2
            row = m // n
            col = m % n
            if matrix[row][col] == target:
                return True
            elif matrix[row][col] > target:
                r = m - 1
            else:
                l = m + 1
        # print(l, r)
        return False
```

## [Find Peak Element](https://leetcode.com/problems/find-peak-element)  (☆☆) ͏

- 

```python
class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        if not nums:
            return -1
        l = 1
        r = len(nums)
        nums = [nums[0] - 1] + nums + [nums[-1] + 1]
        while l < r - 1:
            m = l + (r - l) // 2
            if nums[m] > nums[m - 1] and nums[m] > nums[m + 1]:
                print(nums, m)
                return m - 1
            elif nums[m + 1] > nums[m]:
                l = m
            else:
                r = m
        if nums[r] > nums[l]:
            return r - 1
        else:
            return l - 1
```

## [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array)  (☆☆) ͏

- while left < right:

  ​            mid = left + (right - left + 1) // 2

  返回right

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        if not nums:
            return -1
        front = False
        if target == nums[0]:
            return 0
        elif target > nums[0]:
            front = True
        left = 0
        right = len(nums) - 1
        print(left, right)
        while left < right:
            mid = left + (right - left + 1) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] > nums[0]:
                if front:
                    if nums[mid] > target:
                        right = mid - 1
                    else:
                        left = mid + 1
                else:
                    left = mid + 1
            else:
                if front:
                    right = mid - 1
                else:
                    if nums[mid] > target:
                        right = mid - 1
                    else:
                        left = mid + 1
        print(left, right)
        if nums[right] == target:
            return right
        return -1

```

## [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array)  (☆☆) ͏

- 

```python

```

## [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array)  (☆☆) ͏

- 

```python

```

## [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays)  (☆☆☆) ͏

- 

```python

```

