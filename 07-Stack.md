> yyyy-mm-dd

---

[toc]

---

# Stack

## [Valid Parentheses](https://leetcode.com/problems/valid-parentheses)  (☆) ͏

- 

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        p = {'(': 0, ')': 1, '[': 2, ']': 3, '{': 4, '}': 5}
        for i in s:
            if stack and (p[stack[-1]]%2) ==0 and (p[stack[-1]] + 1) == p[i]:
                stack.pop()
            else:
                stack.append(i)
        if len(stack) == 0:
            return True
        return False
```

## [Simplify Path](https://leetcode.com/problems/simplify-path)  (☆☆) ͏

- 

```python

```

## [Min Stack](https://leetcode.com/problems/min-stack)  (☆☆) ͏

- 栈里维护一个二元组，第一个是当前元素，第二个是该元素入栈前栈里最小值

```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.minN = float('inf')

    def push(self, val: int) -> None:
        self.stack.append([val, self.minN])
        self.minN = min(self.minN, val)

    def pop(self) -> None:
        val, self.minN = self.stack.pop()

    def top(self) -> int:
        return self.stack[-1][0]

    def getMin(self) -> int:
        return self.minN


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```

## [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation)  (☆☆) ͏

- 

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        operator = "+-*/"
        stack = []
        for token in tokens:
            if token in operator:
                num1 = stack.pop()
                num2 = stack.pop()
                if token == "+":
                    stack.append(num2 + num1)
                elif token == "-":
                    stack.append(num2 - num1)
                elif token == "*":
                    stack.append(num2 * num1)
                elif token == "/":
                    stack.append(int(num2 / num1))
            else:
                stack.append(int(token))
        return stack[-1]
```

## [Basic Calculator](https://leetcode.com/problems/basic-calculator)  (☆☆☆) ͏

- 

```python

```

