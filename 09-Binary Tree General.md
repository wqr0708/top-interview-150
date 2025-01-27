> yyyy-mm-dd

---

[toc]

---

# Binary Tree General

## [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree)  (☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        return max(self.maxDepth(root.left), self.maxDepth(root.right)) + 1
```

## [Same Tree](https://leetcode.com/problems/same-tree)  (☆) ͏

- 

```python
 # Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p and not q:
            return True
        if not p or not q:
            return False
        if p.val != q.val:
            return False
        return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```

## [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree)  (☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return root
        root.right, root.left = self.invertTree(root.left), self.invertTree(root.right)
        return root
```

## [Symmetric Tree](https://leetcode.com/problems/symmetric-tree)  (☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def ref(root1, root2):
            if not root1 and not root2:
                return True
            if not root1 or not root2:
                return False
            if root1.val != root2.val:
                return False
            return ref(root1.left, root2.right) and ref(root1.right, root2.left)
        if not root:
            return True
        return ref(root.left, root.right)
```

## [Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal)  (☆☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        if not preorder:
            return None
        root = TreeNode(preorder[0])
        r_index = 0
        while inorder[r_index]!=preorder[0]:
            r_index += 1
        root.left = self.buildTree(preorder[1:r_index + 1], inorder[:r_index])
        root.right = self.buildTree(preorder[r_index + 1:], inorder[r_index + 1:])
        return root
            
```

## [Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal)  (☆☆) ͏

- 

```python

```

## [Populating Next Right Pointers in Each Node II](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii)  (☆☆) ͏

- O(1)时间复杂度，依靠上一行的next来获得

```python
class TreeLinkNode:
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None
        self.next = None

class Solution:
    def connect(self, root: TreeLinkNode):
        # Initialize pointers for level order traversal
        head = None  # Head of the next level
        prev = None  # The leading node on the next level
        cur = root  # Current node of the current level

        while cur:
            while cur:
                # Connect the left child
                if cur.left:
                    if prev:
                        prev.next = cur.left
                    else:
                        head = cur.left
                    prev = cur.left
                
                # Connect the right child
                if cur.right:
                    if prev:
                        prev.next = cur.right
                    else:
                        head = cur.right
                    prev = cur.right
                
                # Move to the next node at the same level
                cur = cur.next

            # Move to the next level
            cur = head
            head = None
            prev = None

        return root
```

## [Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list)  (☆☆) ͏

- 

```python

```

## [Path Sum](https://leetcode.com/problems/path-sum)  (☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        if not root.left and not root.right:
            return targetSum == root.val
        return self.hasPathSum(root.left, targetSum - root.val) or self.hasPathSum(root.right, targetSum-root.val)
```

## [Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers)  (☆☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def sumNumbers(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        result = [0]
        def traverse(node, nums):
            if not node.left and not node.right:
                result[0] += int("".join([str(i) for i in nums]+[str(node.val)]))
                return
            if node.left:
                traverse(node.left, nums + [node.val])
            if node.right:
                traverse(node.right, nums + [node.val])
        traverse(root, [])
        return result[0]
                
```

## [Binary Tree Maximum Path Sum](https://leetcode.com/problems/binary-tree-maximum-path-sum)  (☆☆☆) ͏

- 

```python

```

## [Binary Search Tree Iterator](https://leetcode.com/problems/binary-search-tree-iterator)  (☆☆) ͏

- 

```python

```

## [Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes)  (☆) ͏

- 

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        h = 0
        nodes = [root]
        cur = []
        while nodes:
            for i in range(len(nodes)):
                if not nodes[i].left:
                    return 2 ** (h + 1) + 2 * i - 1
                if not nodes[i].right:
                    return 2 ** (h + 1) + 2 * i
                cur.append(nodes[i].left)
                cur.append(nodes[i].right)
            h += 1
            nodes = cur
            cur = []
        return 2 ** (h - 1)              
```

## [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree)  (☆☆) ͏

- 

```python

```

