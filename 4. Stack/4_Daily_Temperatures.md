### Daily Temperatures

Leetcode 739 - https://leetcode.com/problems/daily-temperatures/description/?envType=problem-list-v2&envId=wqssdtc2

---

## Solution

user input
```python
def dailyTemperatures(temperatures):
    n = len(temperatures)
    answer = [0] * n
    stack = []

    for i in range(n):
        while stack and temperatures[i] > temperatures[stack[-1]]:
            prev = stack.pop()
            answer[prev] = i - prev

        stack.append(i)

    return answer


# Input
temperatures = list(map(int, input("Enter temperatures: ").split()))

result = dailyTemperatures(temperatures)
print("Output:", result)
```

```python
class Solution:
    def dailyTemperatures(self, temperatures):
        n = len(temperatures)
        answer = [0] * n
        stack = []  # stores indices

        for i in range(n):
            while stack and temperatures[i] > temperatures[stack[-1]]:
                prev = stack.pop()
                answer[prev] = i - prev

            stack.append(i)

        return answer
```

Time: O(n)
Each index pushed & popped once

Space: O(n)
Stack + answer array
