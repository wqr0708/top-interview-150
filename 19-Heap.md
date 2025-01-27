> yyyy-mm-dd

---

[toc]

---

# Heap

## [Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array)  (☆☆) ͏

- 大根堆，函数是自上而下调整，然后自下而上调用函数

```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        def heapify(arr, i, end):
            j = 2 * i + 1
            while j<end:
                if j + 1 < end and arr[j + 1] > arr[j]:
                    j = j + 1
                if arr[j] > arr[i]:
                    arr[i], arr[j] = arr[j], arr[i]
                    i = j
                    j = 2 * i + 1
                else:
                    break
        
        n = len(nums)
        for j in range(n-1, -1, -1):
            heapify(nums, j, n)
        # print(nums)
        for j in range(n-1, -1, -1):
            nums[0], nums[j] = nums[j], nums[0]
            heapify(nums, 0, j)
        # print(nums)
        return nums[-k]
```

## [IPO](https://leetcode.com/problems/ipo)  (☆☆☆) ͏

- 

```python

```

## [Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums)  (☆☆) ͏

- 

```python

```

## [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream)  (☆☆☆) ͏

- 

```python

```

