> 2024-12-23

---

[toc]

---

# Array / String

## [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array)  (☆) ͏

- Inverse
- two pointer

```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i = m - 1
        j = n - 1
        k = m + n - 1
        while k >= 0 and j >= 0:
            if i >= 0 and nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
            # print(nums1)
```

## [Remove Element](https://leetcode.com/problems/remove-element)  (☆) ͏

- 2 pointer

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        i = 0
        for j in range(len(nums)):
            if nums[j] != val:
                nums[i] = nums[j]
                i+=1
        return i
```

## [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array)  (☆) ͏

- 2 pointer

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        i = 0
        for j in range(1, len(nums)):
            if nums[j]!= nums[i]:
                nums[i+1] = nums[j]
                i+=1
        return i+1
```

## [Remove Duplicates from Sorted Array II](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii)  (☆☆) ͏

- 记得开头先判断简单情况，避免边界以及速度更快
- 双指针，替换头的避免i干扰

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if len(nums) < 2:
            return len(nums)
        i = 0
        for j in range(0, len(nums)-2):
            if nums[j] != nums[j+2]:
                nums[i] = nums[j]
                i += 1
        nums[i] = nums[-2]
        nums[i+1] = nums[-1]
        return i + 2

# cpy 面向对象版本：
class Solution:
    class Allower:
        def __init__(self):
            self.lastNum = None
            self.lastCnt = 0

        def knowJustMet(self, num):
            if self.lastNum == num:
                self.lastCnt += 1
            else:
                self.lastNum = num
                self.lastCnt = 1
            print(">", self.lastNum, self.lastCnt)

        def allow(self, newNum):
            if self.lastCnt <= 1:
                return True
            else:
                isOk = newNum != self.lastNum
                return isOk


    def removeDuplicates(self, nums: List[int]) -> int:
        savePtr = 0

        allower = Solution.Allower()

        for num in nums:
            if allower.allow(num):
                nums[savePtr] = num
                savePtr += 1
            allower.knowJustMet(num)

        return savePtr
        

        
```

## [Majority Element](https://leetcode.com/problems/majority-element)  (☆) ͏

- 打擂台

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        major = nums[0]
        count = 1
        for i in range(1, len(nums)):
            if nums[i] == major:
                count += 1
            else:
                if count:
                    count -= 1
                else:
                    major = nums[i]
                    count = 1
        return major
```

## [Rotate Array](https://leetcode.com/problems/rotate-array)  (☆☆) ͏

- gcd方法，[-k : ]延长拼接方法，旋转方法，一个一个挪方法
- nums[:]来进行in-place操作，否则不是原位修改
- 注意k取模情况
- gcd递归求取
- 获取gcd，得知需要轮换turn = gcd(k, n)轮，每轮n // turn个数字，进行轮换
- 需要def reverse(nums, left, right)， 否则需要nums[:-k] = reverse(nums[:-k])。 因为传进去的nums[:-k]是另外的空间，并不能使得nums原位替代

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k = k % len(nums)
        nums[:] = nums[-k:] + nums[:-k]
        return
    
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        def gcd(a, b):    
            if a == 1 or b == 1:
                return 1
            if a == 0:
                return b
            if b == 0:
                return a            
            return gcd(a % b, b % a)

        n = len(nums)
        k = k % n
        tmp = 0
        turn = gcd(k, n)
        count_turn = n // turn

        for i in range(turn):
            tmp = nums[i % n]
            for j in range(1, count_turn):
                nex = nums[(i + k * j) % n]
                nums[(i + k * j) % n] = tmp
                tmp = nex
            nums[(i) % n] = tmp
        return
    
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        def reverse(nums):
            n = len(nums)
            for i in range(n // 2):
                nums[i], nums[-1-i] = nums[-1-i], nums[i]
            return nums

        k = k % len(nums)
        nums[:-k] = reverse(nums[:-k])
        nums[-k:] = reverse(nums[-k:])
        reverse(nums)
        
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        def reverse(nums, left, right):
            n = right - left
            for i in range(n // 2):
                nums[left + i], nums[right - 1 - i] = nums[right - 1 - i], nums[left + i]
            return nums

        n = len(nums)
        k = k % len(nums)
        reverse(nums, 0, n - k)
        reverse(nums, n - k, n)
        reverse(nums, 0, n)
```

## [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock)  (☆) ͏

- 开头添加特判，安全快速
- =float('inf')来表示正无穷
- 使用比较而不是min(), max()可以加快速度，减少调用和赋值次数

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if not prices:
            return 0
            
        min_price = prices[0]
        max_profit = 0
        
        for price in prices[1:]:
            if price < min_price:
                min_price = price
            elif price - min_price > max_profit:
                max_profit = price - min_price
                
        return max_profit
```

## [Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii)  (☆☆) ͏

- 不需要存储手上股票价值，只需要判断相邻是否递增即可
- range迭代器开销占大头，换成while会更快

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        result = 0
        for i in range(1, len(prices)):
            if prices[i] >= prices[i - 1]:
                result += prices[i] - prices[i - 1]
        return result
```

## [Jump Game](https://leetcode.com/problems/jump-game)  (☆☆) ͏

- 只需判断是否可以跳到即可

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        n = len(nums)
        l = 0
        r = nums[0]
        while l <= r:
            if l + nums[l] >= r:
                r = l + nums[l]
                if r >= n - 1:
                    return True
            l += 1
        return False
```

## [Jump Game II](https://leetcode.com/problems/jump-game-ii)  (☆☆) ͏

- 注意边界条件，开闭区间

```python
class Solution:
    def jump(self, nums) -> int:
        n = len(nums)
        l = 1
        r = nums[0]
        if n == 1:
            return 0
        count = 1
        if r >= n - 1:
            return 1
        while l <= r:
            i = l
            count += 1
            last_r = r
            while i <= last_r:
                if i + nums[i] > r:
                    r = i + nums[i]
                    if r >= n - 1:
                        return count
                i += 1
            l = last_r + 1
        return 0
```

## [H-Index](https://leetcode.com/problems/h-index)  (☆☆) ͏

- 二分法

```python
class Solution:
    def hIndex(self, citations: List[int]) -> int:
        l = 0
        r = len(citations)
        while l < r:
            m = l + (r - l) // 2 + 1
            if m <= sum([1 for i in citations if i >= m]):
                l = m
            else:
                r = m - 1
        return l
```

## [Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1)  (☆☆) ͏

- O(1)时间即可考虑使用{}
- list remove是O(n)
- rand.randint(a, b)闭区间随机取值
- Rand.choice([])列表中随机选取元素

```python
class RandomizedSet:

    def __init__(self):
        self.dict = {}
        self.list = []
        self.num = 0

    def insert(self, val: int) -> bool:
        if val in self.dict:
            return False
        self.dict[val] = self.num
        if len(self.list) > self.num:
            self.list[self.num] = val
        else:
            self.list.append(val)
        self.num += 1
        return True
        

    def remove(self, val: int) -> bool:
        if val not in self.dict:
            return False
        self.num -= 1
        self.list[self.dict[val]] = self.list[self.num]
        self.dict[self.list[self.num]] = self.dict[val]
        del self.dict[val]
        return True

    def getRandom(self) -> int:
        return self.list[random.randint(0, self.num - 1)]

# Your RandomizedSet object will be instantiated and called as such:
# obj = RandomizedSet()
# param_1 = obj.insert(val)
# param_2 = obj.remove(val)
# param_3 = obj.getRandom()
```

## [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self)  (☆☆) ͏

- 记得查看题目里面变量的范围

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        prefix = [1] * n
        suffix = [1] * n
        prefix[0] = nums[0]
        suffix[-1] = nums[-1]
        for i in range(1, n):
            prefix[i] = prefix[i - 1] * nums[i]
            suffix[-1-i] = suffix[-i] * nums[-1-i]
        result = [suffix[1]]
        for i in range(1, n-1):
            result.append(prefix[i-1] * suffix[i+1])
        result.append(prefix[-2])
        return result
```

## [Gas Station](https://leetcode.com/problems/gas-station)  (☆☆) ͏

- 

```python

```

## [Candy](https://leetcode.com/problems/candy)  (☆☆☆) ͏

- 

```python

```

## [Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water)  (☆☆☆) ͏

- 

```python

```

## [Roman to Integer](https://leetcode.com/problems/roman-to-integer)  (☆) ͏

- 只有IX这种，才会小的数字排在大的数字前面

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        m = {
            'I': 1,
            'V': 5,
            'X': 10,
            'L': 50,
            'C': 100,
            'D': 500,
            'M': 1000
        }
        
        ans = 0
        
        for i in range(len(s)):
            if i < len(s) - 1 and m[s[i]] < m[s[i+1]]:
                ans -= m[s[i]]
            else:
                ans += m[s[i]]
        
        return ans
```

## [Integer to Roman](https://leetcode.com/problems/integer-to-roman)  (☆☆) ͏

- 

```python

```

## [Length of Last Word](https://leetcode.com/problems/length-of-last-word)  (☆) ͏

- s.split(" ")字符串在前，分隔符在后
- 不填充分隔符默认为**空白字符（空格、制表符、换行符等）**
- s.split(" ")会对连续的空格进行分割，它会在这些空格之间生成空字符串 `''`

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        print(s.split())
        return len(s.split()[-1])
```

## [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix)  (☆) ͏

- 写在类里面的辅助函数记得参数里写self, 调用的时候写self.f()
- 也可以直接写在解题函数里面
- 时间复杂度O(n⋅L⋅log⁡L), `check` 的时间复杂度为 **`O(n * m)`**，其中 `m` 是当前检查的前缀长度，二分查找的次数为 **`O(log L)`**。

```python
class Solution:
    def check(self, s, m):
        n = len(s)
        template = s[0][:m]
        for i in range(n):
            if s[i][:m] != template:
                return False
        return True

    def longestCommonPrefix(self, strs: List[str]) -> str:
        l = 0
        r = len(strs[0])
        while l < r:
            m = l + (r - l) // 2 + 1
            if self.check(strs, m):
                l = m
            else:
                r = m - 1
        return strs[0][:l]
```

## [Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string)  (☆☆) ͏

- 

```python

```

## [Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion)  (☆☆) ͏

- 也可以直接模拟，遍历一遍就行

```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1:
            return s
        row = 0
        result =""
        period = 2 * numRows - 2
        cycle_num = (len(s) + period - 1) // period
        result = ("").join([s[i] for i in range(len(s)) if i % period == 0])
        row = 1
        while row < numRows - 1:
            current_row_result = ""
            for i in range(cycle_num):
                if i * period + row < len(s):
                    current_row_result += s[i * period + row]
                if i * period + period - row < len(s):
                    current_row_result += s[i * period + period - row]
            result += current_row_result
            row += 1
        result += ("").join([s[i] for i in range(len(s)) if (i - numRows + 1) % period == 0])
        return result
```

## [Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string)  (☆) ͏

- 

```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        hay_size = len(haystack)
        needle_size = len(needle)
        for i in range(hay_size - needle_size + 1):
            if haystack[i: i+ needle_size] == needle:
                return i
        return -1
```

## [Text Justification](https://leetcode.com/problems/text-justification)  (☆☆☆) ͏

- 

```python

```

