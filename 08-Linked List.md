> yyyy-mm-dd

---

[toc]

---

# Linked List

## [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle)  (☆) ͏

- 快慢指针

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        fast = head
        slow = head
        if not head:
            return False
        while slow and fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            if slow == fast:
                return True
        return False
```

## [Add Two Numbers](https://leetcode.com/problems/add-two-numbers)  (☆☆) ͏

- 直接遍历，数字位数过多，不要转换为int

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        root = ListNode()
        carry = 0
        cur1 = l1
        cur2 = l2
        cur = root
        val = 0
        while cur1 and cur2:
            val = cur1.val + cur2.val + carry
            carry = val // 10
            cur.next = ListNode(val % 10)
            cur = cur.next
            cur1 = cur1.next
            cur2 = cur2.next
        while cur1:
            val = cur1.val + carry
            carry = val // 10
            cur.next = ListNode(val % 10)
            cur = cur.next
            cur1 = cur1.next
        while cur2:
            val = cur2.val + carry
            carry = val // 10
            cur.next = ListNode(val % 10)
            cur = cur.next
            cur2 = cur2.next
        if carry:
            cur.next = ListNode(1)
        return root.next
```

## [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists)  (☆) ͏

- 

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        cur1 = list1
        cur2 = list2
        head = ListNode()
        cur = head
        if not cur1:
            return cur2
        if not cur2:
            return cur1
        while cur1 and cur2:
            if cur1.val < cur2.val:
                cur.next = cur1
                cur1 = cur1.next
                cur = cur.next
            else:
                cur.next = cur2
                cur2 = cur2.next
                cur = cur.next
        # if cur:
        #     print(cur.val)
        if cur1:
            cur.next = cur1
        if cur2:
            cur.next = cur2
        return head.next
        
```

## [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer)  (☆☆) ͏

- 直接先把A'复制在A后面，额外空间为O(1)
- We can avoid using extra space for old_node ---> new_node mapping by tweaking the original linked list. Simply interweave the nodes of the old and copied list. For example: Old List: A --> B --> C --> D InterWeaved List: A --> A' --> B --> B' --> C --> C' --> D --> D'

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, x: int, next: 'Node' = None, random: 'Node' = None):
        self.val = int(x)
        self.next = next
        self.random = random
"""

class Solution:
    def copyRandomList(self, head: 'Optional[Node]') -> 'Optional[Node]':
        if not head:
            return None
        cur = head
        while cur:
            new = Node(cur.val)
            new.next = cur.next
            cur.next = new
            cur = new.next
        root = head.next
        cur = head
        while cur:
            if cur.random:
                cur.next.random = cur.random.next
            tmp = cur.next.next
            if tmp:
                cur.next.next = cur.next.next.next
            cur = tmp
        return root
```

## [Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii)  (☆☆) ͏

- 

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        dummy = ListNode()
        dummy.next = head
        cur = dummy
        for _ in range(left - 1):
            cur = cur.next
        pre = cur
        cur = cur.next
        prenow = pre
        for _ in range(right - left):
            tmp = cur.next
            cur.next = prenow
            prenow = cur
            cur = tmp
        tmp = cur.next
        cur.next = prenow
        pre.next.next = tmp
        pre.next = cur
        return dummy.next

```

## [Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group)  (☆☆☆) ͏

- 

```python

```

## [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list)  (☆☆) ͏

- 快慢指针

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy = ListNode()
        dummy.next = head
        fast = dummy
        slow = dummy
        for _ in range(n - 1):
            fast = fast.next
        while fast.next.next:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        return dummy.next
```

## [Remove Duplicates from Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii)  (☆☆) ͏

- 

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(-200)
        dummy.next = head
        cur = -200
        node = dummy
        while node.next:
            cur = node.next.val
            if not node.next.next:
                return dummy.next
            elif node.next.val != node.next.next.val:
                node = node.next
            else:
                cur = node.next.val
                now = node
                while node.next and node.next.val == cur:
                    node = node.next
                now.next = node.next
                node = now
        return dummy.next
```

## [Rotate List](https://leetcode.com/problems/rotate-list)  (☆☆) ͏

- 

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        if not head:
            return None
        dummy = ListNode()
        dummy.next = head
        now = dummy
        fast = dummy
        slow = dummy
        n = 0
        while n < k:
            if not fast:
                break
            fast = fast.next
            n += 1
        if not fast:
            k = k % (n - 1)
            if k == 0:
                return dummy.next
            fast = dummy
            for _ in range(k):
                fast = fast.next
        if not fast.next:
            return dummy.next
        while fast.next:
            fast = fast.next
            slow = slow.next
        fast.next = dummy.next
        newhead = slow.next
        # print(slow.val, slow.next.val)
        slow.next = None
        return newhead
```

## [Partition List](https://leetcode.com/problems/partition-list)  (☆☆) ͏

- 

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def partition(self, head: Optional[ListNode], x: int) -> Optional[ListNode]:
        dummy = ListNode()
        dummy.next = head
        l = ListNode()
        g = ListNode()
        cur = head
        lc = l
        gc = g
        while cur:
            if cur.val < x:
                lc.next = cur
                lc = lc.next
            else:
                gc.next = cur
                gc = gc.next
            cur = cur.next
        gc.next = None
        lc.next = g.next
        return l.next
```

## [LRU Cache](https://leetcode.com/problems/lru-cache)  (☆☆) ͏

- 双向链表
- 字典实现查找
- 每次使用后放到head后面，每次超出限制从tail删除

```python
class Node:
    def __init__(self, key= 0, val = 0, nex = None, pre = None):
        self.key = key
        self.val = val
        self.next = nex
        self.pre = pre

class LRUCache:

    def __init__(self, capacity: int):
        self.capacity = capacity
        self.num = 0
        self.root = Node()
        self.tail = Node()
        self.root.next = self.tail
        self.tail.pre = self.root
        self.dic = {}

    def show(self):
        now = self.root
        result = []
        while now:
            result.append(now.key)
            now = now.next

    def move(self, key):
        self.root.next.pre = self.dic[key]
        self.dic[key].pre.next = self.dic[key].next
        self.dic[key].next.pre = self.dic[key].pre
        self.dic[key].next = self.root.next
        self.dic[key].pre = self.root
        self.root.next = self.dic[key]

    def get(self, key: int) -> int:
        if key in self.dic:
            if self.root.next != self.dic[key]:
                self.move(key)
            return self.dic[key].val
        else:
            return -1

    def put(self, key: int, value: int) -> None:
        if key in self.dic:
            if self.root.next != self.dic[key]:
                self.move(key)
            self.dic[key].val = value
        else:
            if len(self.dic) == self.capacity:
                del self.dic[self.tail.pre.key]
                self.tail.pre.pre.next = self.tail
                self.tail.pre = self.tail.pre.pre

            self.dic[key] = Node(key, value)
            self.root.next.pre = self.dic[key]
            self.dic[key].next = self.root.next
            self.dic[key].pre = self.root
            self.root.next = self.dic[key]


# Your LRUCache object will be instantiated and called as such:
# obj = LRUCache(capacity)
# param_1 = obj.get(key)
# obj.put(key,value)
```

