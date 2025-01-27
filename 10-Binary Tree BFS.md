> yyyy-mm-dd

---

[toc]

---

# Binary Tree BFS

## [Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view)  (☆☆) ͏

- 

```python

```

## [Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree)  (☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        queue = deque()
        result = []
        layer = [root]
        queue.append(layer)
        while layer:
            cur = []
            s = 0
            for node in layer:
                s += node.val
                if node.left:
                    cur.append(node.left)
                if node.right:
                    cur.append(node.right)
            result.append(s / len(layer))
            layer = cur
        return result
                
```

## [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal)  (☆☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        result = []
        result.append([root.val])
        cur = [root]
        while cur:
            now = []
            for node in cur:
                if node.left:
                    now.append(node.left)
                if node.right:
                    now.append(node.right)
            result.append([i.val for i in now])
            cur = now
        return result[:-1]
            
```

## [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal)  (☆☆) ͏

- 

```python

```

