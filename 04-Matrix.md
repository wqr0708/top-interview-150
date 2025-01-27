> yyyy-mm-dd

---

[toc]

---

# Matrix

## [Valid Sudoku](https://leetcode.com/problems/valid-sudoku)  (☆☆) ͏

- 

```python

```

## [Spiral Matrix](https://leetcode.com/problems/spiral-matrix)  (☆☆) ͏

- 

```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        if not matrix:
            return []
        n = len(matrix)
        m = len(matrix[0])
        result = []
        i = 0
        j = 0
        t = 0
        while m > 2 * t + 1 and n > 2 * t + 1:
            for j in range(t, m - t):
                # print(1)
                result.append(matrix[i][j])
            for i in range(t + 1, n - t):
                # print(2)
                result.append(matrix[i][m - t -1])
            for j in range(m - 2 - t, -1 + t, -1):
                # print(3)
                result.append(matrix[n - t - 1][j])
            for i in range(n - 2 - t, t, -1):
                # print(4)
                result.append(matrix[i][j])
            # m -= 2
            # n -= 2
            t += 1
        if m == 2 * t + 1:
            for i in range(t, n - t):
                result.append(matrix[i][t])
        elif n == 2 * t + 1:
            for j in range(t, m - t):
                result.append(matrix[i][j])
        return result
```

## [Rotate Image](https://leetcode.com/problems/rotate-image)  (☆☆) ͏

- 

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        def rotateLayer(layer):
            r, c = layer, layer
            tmp = matrix[r][c]
            for i in range(layer, n - layer - 1):
                tmp = matrix[layer][i]
                matrix[layer][i] = matrix[n - 1 - i][layer]
                matrix[n - 1 - i][layer] = matrix[n - 1 - layer][n - 1 - i]
                matrix[n - 1 - layer][n - 1 - i] = matrix[i][n - 1 - layer]
                matrix[i][n - 1 - layer] = tmp

        if not matrix:
            return
        n = len(matrix)
        for layer in range(0, n // 2):
            rotateLayer(layer)
```

## [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes)  (☆☆) ͏

- O(1)空间
- 0行0列单独用O(1)元素存储，其余用这两行列存储

```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        if not matrix:
            return
        n = len(matrix)
        m = len(matrix[0])
        r = 0
        c = 0
        if 0 in matrix[0]:
            r = 1
        if 0 in [i[0] for i in matrix]:
            c = 1
        for i in range(n):
            for j in range(m):
                if matrix[i][0] == 0 and matrix[0][j] == 0:
                    continue
                if matrix[i][j] == 0:
                    matrix[i][0] = 0
                    matrix[0][j] = 0
        # print(matrix)
        for i in range(1, n):
            for j in range(1, m):
                if matrix[i][0] == 0 or matrix[0][j] == 0:
                    matrix[i][j] = 0
        if r == 1:
            for j in range(m):
                matrix[0][j] = 0
        if c == 1:
            for i in range(n):
                matrix[i][0] = 0
            
        
        
```

## [Game of Life](https://leetcode.com/problems/game-of-life)  (☆☆) ͏

- 

```python

```

