### Min Stack

Leetcode 155 - https://leetcode.com/problems/min-stack/description/?envType=problem-list-v2&envId=wqssdtc2

---

## Solution

user input
```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.minStack = []

    def push(self, val):
        self.stack.append(val)
        if not self.minStack:
            self.minStack.append(val)
        else:
            self.minStack.append(min(val, self.minStack[-1]))

    def pop(self):
        self.stack.pop()
        self.minStack.pop()

    def top(self):
        return self.stack[-1]

    def getMin(self):
        return self.minStack[-1]


# Driver code
minStack = MinStack()

n = int(input("Enter number of operations: "))

for _ in range(n):
    operation = input("Enter operation: ").split()

    if operation[0] == "push":
        val = int(operation[1])
        minStack.push(val)

    elif operation[0] == "pop":
        minStack.pop()

    elif operation[0] == "top":
        print("Top:", minStack.top())

    elif operation[0] == "getMin":
        print("Min:", minStack.getMin())
```

```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.minStack = []

    def push(self, val: int) -> None:
        self.stack.append(val)

        if not self.minStack:
            self.minStack.append(val)
        else:
            self.minStack.append(min(val, self.minStack[-1]))

    def pop(self) -> None:
        self.stack.pop()
        self.minStack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minStack[-1]
```


Operation	Time

push	O(1)

pop	O(1)

top	O(1)

getMin	O(1)


Space Complexity: O(n)

We store elements twice (stack + minStack)
