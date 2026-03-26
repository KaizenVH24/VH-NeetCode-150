### Evaluate reverse polish notation


Leetcode 150 - https://leetcode.com/problems/evaluate-reverse-polish-notation/description/?envType=problem-list-v2&envId=wqssdtc2

---

## Solution

user input
```python
def evalRPN(tokens):
    stack = []

    for token in tokens:
        if token not in "+-*/":
            stack.append(int(token))
        else:
            b = stack.pop()
            a = stack.pop()

            if token == "+":
                stack.append(a + b)
            elif token == "-":
                stack.append(a - b)
            elif token == "*":
                stack.append(a * b)
            else:
                stack.append(int(a / b))

    return stack[0]


# Taking input
tokens = input("Enter tokens separated by space: ").split()

result = evalRPN(tokens)
print("Result:", result)
```

```python
class Solution:
    def evalRPN(self, tokens):
        stack = []

        for token in tokens:
            if token not in "+-*/":
                stack.append(int(token))
            else:
                b = stack.pop()
                a = stack.pop()

                if token == "+":
                    stack.append(a + b)
                elif token == "-":
                    stack.append(a - b)
                elif token == "*":
                    stack.append(a * b)
                else:
                    stack.append(int(a / b))  # truncate toward 0

        return stack[0]
```


Time: O(n)
Each token processed once

Space: O(n)
Stack holds numbers
