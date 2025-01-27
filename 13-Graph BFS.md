> yyyy-mm-dd

---

[toc]

---

# Graph BFS

## [Snakes and Ladders](https://leetcode.com/problems/snakes-and-ladders)  (☆☆) ͏

- 

```python

```

## [Minimum Genetic Mutation](https://leetcode.com/problems/minimum-genetic-mutation)  (☆☆) ͏

- 构造一个graph，每个可变化的node之间构造边，用dict记录图，bfs

```python
class Solution:
    def compare(sefl, s1, s2):
        dif = 0
        for i in range(8):
            if s1[i] != s2[i]:
                if dif > 0:
                    return False
                dif = 1
        return True

    def minMutation(self, startGene: str, endGene: str, bank: List[str]) -> int:
        queue = deque()
        queue.append(startGene)
        gr = defaultdict(list)
        
        if startGene not in bank:
            bank.append(startGene)

        n = len(bank)
        for i in range(n - 1):
            for j in range(i + 1, n):
                if self.compare(bank[i], bank[j]):
                    gr[bank[i]].append(bank[j])
                    gr[bank[j]].append(bank[i])
        
        queue = deque()
        queue.append([startGene, 0])
        visited = set()
        visited.add(startGene)
        while queue:
            cur, step = queue.popleft()
            for new in gr[cur]:
                if new == endGene:
                    return step + 1
                if new not in visited:
                    visited.add(new)
                    queue.append([new, step + 1])
        return -1
```

## [Word Ladder](https://leetcode.com/problems/word-ladder)  (☆☆☆) ͏

- 

```python

```

