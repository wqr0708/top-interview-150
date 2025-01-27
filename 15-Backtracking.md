> yyyy-mm-dd

---

[toc]

---

# Backtracking

## [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number)  (☆☆) ͏

- 

```python

```

## [Combinations](https://leetcode.com/problems/combinations)  (☆☆) ͏

- 

```python
class Solution:
    def combine(self, n: int, k: int) -> List[List[int]]:
        def backtrack(start, n, k, r):
            if k == 0:
                output.append(r)
            elif start > n or n - start + 1 < k:
                return
            else:
                backtrack(start + 1, n, k - 1, r + [start])
                backtrack(start + 1, n, k, r)

        output = []
        backtrack(1, n, k, [])
        return output
```

## [Permutations](https://leetcode.com/problems/permutations)  (☆☆) ͏

- set([num])
- 回溯，set删减更快

```python
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        def backtrack(sn, cur):
            if len(cur) == n:
                output.append(cur)
            for num in sn:
                backtrack(sn - set([num]), cur + [num])

        n = len(nums)
        output = []
        backtrack(set(nums), [])
        return output
```

## [Combination Sum](https://leetcode.com/problems/combination-sum)  (☆☆) ͏

- 

```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        def backtrack(cur, target, start):
            if target == 0:
                output.append(cur)
            elif target < 0:
                return
            else:
                for i in range(start, n):
                    if target >= candidates[i]:
                        backtrack(cur+[candidates[i]], target - candidates[i], i)

        output = []
        n = len(candidates)
        backtrack([], target, 0)
        return output
```

## [N-Queens II](https://leetcode.com/problems/n-queens-ii)  (☆☆☆) ͏

- 

```python

```

## [Generate Parentheses](https://leetcode.com/problems/generate-parentheses)  (☆☆) ͏

- 

```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        result = []
        def backtrack(cur, left, right):
            if left == 0:
                result.append(cur + right * ')')
                return
            elif left > right:
                return
            elif left == right:
                backtrack(cur + '(', left - 1, right)
            else:
                backtrack(cur + '(', left - 1, right)
                backtrack(cur + ')', left, right - 1)
        backtrack("", n, n)
        return result
```

## [Word Search](https://leetcode.com/problems/word-search)  (☆☆) ͏

- Dfs

```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        if not word:
            return True
        if not board:
            return False
        n = len(board)
        m = len(board[0])
        visited = [[0] * m for _ in range(n)]
        word_len = len(word)
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
        def dfs(index, row, col):
            # print(index, row, col)
            if index == word_len:
                return True
            for r, c in directions:
                nr = row + r
                nc = col + c
                if 0 <= nr < n and 0 <= nc < m:
                    if not visited[nr][nc]:
                        if board[nr][nc] == word[index]:
                            visited[nr][nc] = 1
                            if dfs(index + 1, nr, nc):
                                return True
                            visited[nr][nc] = 0
            return False
        
        for i in range(n):
            for j in range(m):
                if board[i][j] == word[0]:
                    visited[i][j] = 1
                    if dfs(1, i, j):
                        return True
                    visited[i][j] = 0
        return False

```

