> yyyy-mm-dd

---

[toc]

---

# Bit Manipulation

## [Add Binary](https://leetcode.com/problems/add-binary)  (☆) ͏

- 考虑字符串长短
- 逆序
- 类型转换
-  c = (int(a[i]) + int(b[j]) + c) // 2三个都需要考虑
-  Addition of **1 and 1** will lead to **carry 1** and **print 0**
- ord获取asc

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        if len(a) < len(b):
            a, b = b, a
        n = len(a)
        m = len(b)
        i = n - 1
        j = m - 1
        r = ""
        c = 0
        while j > -1:
            r = str(int(a[i]) ^ int(b[j]) ^ c) + r
            c = (int(a[i]) + int(b[j]) + c) // 2
            j -= 1
            i -= 1
        while i > -1:
            r = str(int(a[i]) ^ c) + r
            c = int(a[i]) & c
            i -= 1
        if c:
            r = str(c) + r
        return r
        
        
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        res = ""
        i, j, carry = len(a) - 1, len(b) - 1, 0
        while i >= 0 or j >= 0:
            sum = carry;
            if i >= 0 : sum += ord(a[i]) - ord('0') # ord is use to get value of ASCII character
            if j >= 0 : sum += ord(b[j]) - ord('0')
            i, j = i - 1, j - 1
            carry = 1 if sum > 1 else 0;
            res += str(sum % 2)

        if carry != 0 : res += str(carry);
        return res[::-1]       
```

## [Reverse Bits](https://leetcode.com/problems/reverse-bits)  (☆) ͏

- 位运算用来进行2指数的操作
- follow up: chunk table, 256byte存储空间

```python
class Solution:
    def reverseBits(self, n: int) -> int:
        r = 0
        bit_now = 0
        for i in range(32):
            bit_now = n % 2
            r = 2 * r + bit_now
            n = n // 2
        return r
    
public int reverseBits(int n) {
    if (n == 0) return 0;
    
    int result = 0;
    for (int i = 0; i < 32; i++) {
        result <<= 1;
        if ((n & 1) == 1) result++;
        n >>= 1;
    }
    return result;
}
```

## [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits)  (☆) ͏

- 位运算，没啥可说的

```python
class Solution:
    def hammingWeight(self, n: int) -> int:
        r = 0
        while n:
            r += (1 & n)
            n >>= 1
        return r
```

## [Single Number](https://leetcode.com/problems/single-number)  (☆) ͏

- 异或消除相同

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        r = 0
        for i in nums:
            r ^= i
        return r
```

## [Single Number II](https://leetcode.com/problems/single-number-ii)  (☆☆) ͏

- 

```python

```

## [Bitwise AND of Numbers Range](https://leetcode.com/problems/bitwise-and-of-numbers-range)  (☆☆) ͏

- 

```python

```

