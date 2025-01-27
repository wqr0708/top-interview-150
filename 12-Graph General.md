> yyyy-mm-dd

---

[toc]

---

# Graph General

## [Number of Islands](https://leetcode.com/problems/number-of-islands)  (☆☆) ͏

- 

```python

```

## [Surrounded Regions](https://leetcode.com/problems/surrounded-regions)  (☆☆) ͏

- 我是用一个数组记录，遍历所有中间块，记录当前dfs是否经过靠边的块，若有则使用color进行记录，来判断是否需要改色
- 但其实只需要dfs遍历靠边的块就可以了，就可以将这些块改变为2色，然后将所有其他块都变成X，这些块变成O

```python
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
        def dfs(i, j, c):
            for d in directions:
                ni = i + d[0]
                nj = j + d[1]
                if ni < 0 or ni > n - 1 or nj < 0 or nj > m - 1 or board[ni][nj] == "X" or visited[ni][nj]:
                    continue
                if (ni == 0 or ni == n - 1 or nj == 0 or nj == m - 1):
                    c = "O"
                    # print(ni, nj)
                visited[ni][nj] = 1
                cur.append([ni, nj])
                c = dfs(ni, nj, c)
            return c

        if not board:
            return
        n = len(board)
        m = len(board[0])
        cur = []
        visited = [[0] * m for _ in range(n)]
        color = ""
        for i in range(1, n - 1):
            for j in range(1, m - 1):
                if board[i][j] == "O" and not visited[i][j]:
                    cur = [[i, j]]
                    color = "X"
                    color = dfs(i, j, color)
                    # print(cur, color)
                    for place in cur:
                        board[place[0]][place[1]] = color
                        
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        def dfs(i: int, j: int):
            if not (0 <= i < m and 0 <= j < n and board[i][j] == "O"):
                return
            board[i][j] = "."
            for a, b in pairwise((-1, 0, 1, 0, -1)):
                dfs(i + a, j + b)

        m, n = len(board), len(board[0])
        for i in range(m):
            dfs(i, 0)
            dfs(i, n - 1)
        for j in range(n):
            dfs(0, j)
            dfs(m - 1, j)
        for i in range(m):
            for j in range(n):
                if board[i][j] == ".":
                    board[i][j] = "O"
                elif board[i][j] == "O":
                    board[i][j] = "X"
```

## [Clone Graph](https://leetcode.com/problems/clone-graph)  (☆☆) ͏

- 

```python

```

## [Evaluate Division](https://leetcode.com/problems/evaluate-division)  (☆☆) ͏

- 

```python

```

## [Course Schedule](https://leetcode.com/problems/course-schedule)  (☆☆) ͏

- 拓扑序列
- DFS+三重染色/DFS+visited记录：都是判断需求节点是已经处理过的（✅）还是正在处理的（❌）

```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        def buildAdjacencyList(n, edgesList):
            adjList = [[] for _ in range(n)]
            for c1, c2 in edgesList:
                adjList[c2].append(c1)
            return adjList
        
        def topoBFS(numNodes, edgesList):
            adjList = buildAdjacencyList(numNodes, edgesList)

            inDegrees = [0] * numNodes
            for v1,v2 in edgesList:
                inDegrees[v1] += 1

            queue = []
            for v in range(numNodes):
                if inDegrees[v] == 0:
                    queue.append(v)

            count = 0
            topoOrder = []

            while queue:
                v = queue.pop()
                topoOrder.append(v)

                count += 1

                for des in adjList[v]:
                    inDegrees[des] -= 1
                    if inDegrees[des] == 0:
                        queue.append(des)

            if count != numNodes:
                return None
            else:
                return topoOrder

        return True if topoBFS(numCourses, prerequisites) else False

    
    
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        def buildAdjacencyList(n, edgesList):
            adjList = [[] for _ in range(n)]
            for c1, c2 in edgesList:
                adjList[c2].append(c1)
            return adjList
        
        adjList = buildAdjacencyList(numCourses, prerequisites)
        state = [0] * numCourses

        def hasCycle(v):
            if state[v] == 1:
                return False
            if state[v] == -1:
                return True

            state[v] = -1

            for i in adjList[v]:
                if hasCycle(i):
                    return True

            state[v] = 1
            return False

        for v in range(numCourses):
            if hasCycle(v):
                return False

        return True
```

## [Course Schedule II](https://leetcode.com/problems/course-schedule-ii)  (☆☆) ͏

- 

```python

```

