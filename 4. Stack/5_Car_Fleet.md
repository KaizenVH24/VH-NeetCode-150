### Car fleet

Leetcode 853 - https://leetcode.com/problems/car-fleet/description/?envType=problem-list-v2&envId=wqssdtc2

---

## Solution

user input
```python
def carFleet(target, position, speed):
    pairs = sorted(zip(position, speed), reverse=True)

    fleets = 0
    prev_time = 0

    for p, s in pairs:
        time = (target - p) / s

        if time > prev_time:
            fleets += 1
            prev_time = time

    return fleets


# Input
target = int(input("Enter target: "))
position = list(map(int, input("Enter positions: ").split()))
speed = list(map(int, input("Enter speeds: ").split()))

print("Number of fleets:", carFleet(target, position, speed))
```

```python
class Solution:
    def carFleet(self, target, position, speed):
        pairs = [(p, s) for p, s in zip(position, speed)]
        pairs.sort(reverse=True)  # sort by position descending

        stack = []

        for p, s in pairs:
            time = (target - p) / s
            stack.append(time)

            # if current car catches up
            if len(stack) >= 2 and stack[-1] <= stack[-2]:
                stack.pop()

        return len(stack)
```

without using stack
```python
class Solution:
    def carFleet(self, target, position, speed):
        pairs = sorted(zip(position, speed), reverse=True)

        fleets = 0
        prev_time = 0

        for p, s in pairs:
            time = (target - p) / s

            if time > prev_time:
                fleets += 1
                prev_time = time

        return fleets
```


Time: O(n log n)

Space: O(n)
