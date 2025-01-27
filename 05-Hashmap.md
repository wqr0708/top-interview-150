> yyyy-mm-dd

---

[toc]

---

# Hashmap

## [Ransom Note](https://leetcode.com/problems/ransom-note)  (☆) ͏

- Counter
- 字典&

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        st1, st2 = Counter(ransomNote), Counter(magazine)
        if st1 & st2 == st1:
            return True
        return False
```

## [Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings)  (☆) ͏

- 分别维护两个dic

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        dicss = {}
        dictt = {}
        for i in range(len(s)):
            if s[i] in dicss:
                if t[i] != dicss[s[i]]:
                    return False
            if t[i] in dictt:
                if s[i] != dictt[t[i]]:
                    return False
            else:
                dicss[s[i]] = t[i]
                dictt[t[i]] = s[i]
        return True
```

## [Word Pattern](https://leetcode.com/problems/word-pattern)  (☆) ͏

- 与上题一模一样

```python
class Solution:
    def wordPattern(self, pattern: str, s: str) -> bool:
        s, t = pattern, s.split(' ')
        print()
        if len(s) != len(t):
            return False
        dicss = {}
        dictt = {}
        for i in range(len(s)):
            if s[i] in dicss:
                if t[i] != dicss[s[i]]:
                    return False
            if t[i] in dictt:
                if s[i] != dictt[t[i]]:
                    return False
            else:
                dicss[s[i]] = t[i]
                dictt[t[i]] = s[i]
        return True
```

## [Valid Anagram](https://leetcode.com/problems/valid-anagram)  (☆) ͏

- from collections import Counter

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return Counter(s) == Counter(t)
```

## [Group Anagrams](https://leetcode.com/problems/group-anagrams)  (☆☆) ͏

- from collections import defaultdict
- defaultdict传参value默认类型
- 字符串排序需要join
- 返回values需要list(hm.values())

```python
from collections import defaultdict


class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        hm = defaultdict(list)

        for word in strs:
            sw = "".join(sorted(word))
            hm[sw].append(word)
        
        return list(hm.values())
```

## [Two Sum](https://leetcode.com/problems/two-sum)  (☆) ͏

- Defaultdict

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        n = len(nums)
        dic = defaultdict(int)
        for i in range(n):
            if nums[i] in dic:
                return dic[nums[i]], i
            else:
                dic[target - nums[i]] = i
        return -1
```

## [Happy Number](https://leetcode.com/problems/happy-number)  (☆) ͏

- sum(int(digit) ** 2 for digit in str(n))
- 判断是否出现过set更好用

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        ans = []
        result = n
        while result not in ans:
            ans.append(result)
            n = result
            result = 0
            while n:
                result += (n % 10)**2
                n //= 10
            if result == 1:
                return True
        return False

class Solution:
    def isHappy(self, n: int) -> bool:
        seen = set()
        while n != 1 and n not in seen:
            seen.add(n)
            n = sum(int(digit) ** 2 for digit in str(n))
        return n == 1    
```

## [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii)  (☆) ͏

- 

```python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        n = len(nums)
        dic = defaultdict()
        for i in range(n):
            if nums[i] in dic:
                if i - dic[nums[i]] <= k:
                    return True
                else:
                    dic[nums[i]] = i
            else:
                dic[nums[i]] = i
        return False
```

## [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence)  (☆☆) ͏

- 

```python

```

