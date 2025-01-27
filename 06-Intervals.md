> yyyy-mm-dd

---

[toc]

---

# Intervals

## [Summary Ranges](https://leetcode.com/problems/summary-ranges)  (☆) ͏

- 

```python
class Solution:
    def summaryRanges(self, nums: List[int]) -> List[str]:
        if not nums:
            return []
        result = []
        l = 0
        n = len(nums)
        for i in range(1, n): 
            if nums[i] == nums[i - 1] + 1:
                continue
            else:
                if i > l + 1:
                    result.append(str(nums[l]) + "->" + str(nums[i - 1]))
                else:
                    result.append(str(nums[l]))
                l = i
        if n - 1 > l:
            result.append(str(nums[l]) + "->" + str(nums[n - 1]))
        else:
            result.append(str(nums[l]))
        return result
        
```

## [Merge Intervals](https://leetcode.com/problems/merge-intervals)  (☆☆) ͏

- \# 先按第零个位置排序，再按第一个位置排序 sorted_data = sorted(data, key=lambda x: (x[0], x[1]))

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals:
            return []
        intervals.sort(key = lambda x: x[0])
        n = len(intervals)
        result = []
        left = intervals[0][0]
        right = intervals[0][1]
        for i in range(1, n):
            if intervals[i][0] > right:
                result.append([left, right])
                left, right = intervals[i]
            else:
                right = max(right, intervals[i][1])
        result.append([left, right])
        return result
```

## [Insert Interval](https://leetcode.com/problems/insert-interval)  (☆☆) ͏

- 

```python

```

## [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons)  (☆☆) ͏

- 排序【1】更快
- 根据比较end可以得知需要排【1】

```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        if not points:
            return 0
        points.sort(key = lambda x: x[0])
        n = len(points)
        r = 1
        end = points[0][1]
        for i in range(1, n):
            if points[i][0] <= end:
                end = min(end, points[i][1])
            else:
                end = points[i][1]
                r += 1
        return r
```

