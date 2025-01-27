> yyyy-mm-dd

---

[toc]

---

# Multidimensional DP

## [Triangle](https://leetcode.com/problems/triangle)  (☆☆) ͏

- 

```python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        dp = [row[:] for row in triangle]
        dp[0][0] = triangle[0][0]
        for i in range(1, len(triangle)):
            dp[i][0] = dp[i - 1][0] + triangle[i][0]
            dp[i][-1] = dp[i - 1][-1] + triangle[i][-1]
            for j in range(1, len(dp[i]) - 1):
                dp[i][j] = min(dp[i - 1][j - 1], dp[i - 1][j]) + triangle[i][j]
        # print(dp)
        return min(dp[-1])
```

## [Minimum Path Sum](https://leetcode.com/problems/minimum-path-sum)  (☆☆) ͏

- 一个dp来循环改变，每一行迭代，替代二维dp

```python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        if not grid:
            return 0
        n = len(grid)
        m = len(grid[0])
        dp = [0] * m
        dp[0] = grid[0][0]
        for j in range(1, m):
            dp[j] = dp[j - 1] + grid[0][j]
        
        for i in range(1, n):
            dp[0] = dp[0] + grid[i][0]
            for j in range(1, m):
                dp[j] = min(dp[j], dp[j - 1]) + grid[i][j]
        return dp[-1]
```

## [Unique Paths II](https://leetcode.com/problems/unique-paths-ii)  (☆☆) ͏

- 

```python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        if not obstacleGrid:
            return 0
        n = len(obstacleGrid)
        m = len(obstacleGrid[0])
        dp = [1] * m
        path = 1
        for j in range(m):
            if obstacleGrid[0][j]:
                path = 0
            dp[j] = path
        for i in range(1, n):
            if obstacleGrid[i][0]:
                dp[0] = 0
            else:
                dp[0] = dp[0]
            for j in range(1, m):
                if obstacleGrid[i][j]:
                    dp[j] = 0
                else:
                    dp[j] = dp[j] + dp[j - 1]
            print(dp)
        return dp[-1]
```

## [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring)  (☆☆) ͏

- 

```python

```

## [Interleaving String](https://leetcode.com/problems/interleaving-string)  (☆☆) ͏

- 

```python

```

## [Edit Distance](https://leetcode.com/problems/edit-distance)  (☆☆) ͏

- 

```python

```

## [Best Time to Buy and Sell Stock III](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii)  (☆☆☆) ͏

- 

```python

```

## [Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv)  (☆☆☆) ͏

- 

```python

```

## [Maximal Square](https://leetcode.com/problems/maximal-square)  (☆☆) ͏

- 

```python

```

