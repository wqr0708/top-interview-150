> yyyy-mm-dd

---

[toc]

---

# Trie

## [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree)  (☆☆) ͏

- 可以直接写一个helper，不传递列表，而是l, r

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        if not nums:
            return None
        n = len(nums)
        mid = n // 2
        root = TreeNode(nums[mid])
        root.left = self.sortedArrayToBST(nums[:mid])
        root.right = self.sortedArrayToBST(nums[mid+1:])
        return root
```

## [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure)  (☆☆) ͏

- 

```python

```

## [Word Search II](https://leetcode.com/problems/word-search-ii)  (☆☆☆) ͏

- 

```python

```

