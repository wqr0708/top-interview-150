> yyyy-mm-dd

---

[toc]

---

# Binary Search Tree

## [Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst)  (☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        cur, stack, minDiff, prev = root, [], 10**5, -10**5

        while stack or cur:
            while cur:
                stack.append(cur)
                cur = cur.left
            node = stack.pop()
            minDiff = min(minDiff, node.val - prev)
            prev = node.val
            cur = node.right

        return minDiff
```

## [Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst)  (☆☆) ͏

- 利用中序遍历
- stack先存储left，直到没有左子节点，弹出，换成right

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
        stack = []
        cur = root
        while stack or cur:
            while cur:
                stack.append(cur)
                cur = cur.left
            cur = stack.pop()
            k -= 1
            if not k:
                return cur.val
            cur = cur.right
        return -1
```

## [Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree)  (☆☆) ͏

- 

```python

```

