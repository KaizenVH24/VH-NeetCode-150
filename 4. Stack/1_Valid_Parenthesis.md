### Valid Parenthesis 

Leetcode 20 - https://leetcode.com/problems/valid-parentheses/description/?envType=problem-list-v2&envId=wqssdtc2

---

## Solution

user input
```python
def isValid(s):
    stack = []
    mapping = {
        ')': '(',
        ']': '[',
        '}': '{'
    }

    for ch in s:
        if ch in mapping:
            if not stack or stack[-1] != mapping[ch]:
                return False
            stack.pop()
        else:
            stack.append(ch)

    return len(stack) == 0


# Taking input from user
s = input("Enter the parentheses string: ")

if isValid(s):
    print("Valid")
else:
    print("Invalid")
```

```python
def isValid(s):
    stack = []
    mapping = {
        ')': '(',
        ']': '[',
        '}': '{'
    }

    for ch in s:
        if ch in mapping:  # closing bracket
            if not stack or stack[-1] != mapping[ch]:
                return False
            stack.pop()
        else:
            stack.append(ch)

    return len(stack) == 0
```

Time Complexity: O(n)

Space Complexity: O(n)

---


## Other solution

```python
class Solution:
    def isValid(self, s: str) -> bool:
        
        while "()" in s or "{}" in s or "[]" in s:
            s = s.replace("()", "")
            s = s.replace("{}", "")
            s = s.replace("[]", "")
        
        return s == ""
```
