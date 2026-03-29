### Time based key-value store

Leetcode 981 - https://leetcode.com/problems/time-based-key-value-store/description/?envType=problem-list-v2&envId=wqs4pyq1

---

## Solution

user input
```python
class TimeMap:

    def __init__(self):
        self.store = {}

    def set(self, key, value, timestamp):
        if key not in self.store:
            self.store[key] = []
        self.store[key].append((timestamp, value))

    def get(self, key, timestamp):
        if key not in self.store:
            return ""

        arr = self.store[key]

        left, right = 0, len(arr) - 1
        res = ""

        while left <= right:
            mid = (left + right) // 2

            if arr[mid][0] <= timestamp:
                res = arr[mid][1]
                left = mid + 1
            else:
                right = mid - 1

        return res


# Driver
tm = TimeMap()

n = int(input("Enter number of operations: "))

for _ in range(n):
    op = input().split()

    if op[0] == "set":
        tm.set(op[1], op[2], int(op[3]))
    elif op[0] == "get":
        print(tm.get(op[1], int(op[2])))
```

```python
import bisect

class TimeMap:

    def __init__(self):
        self.store = {}

    def set(self, key, value, timestamp):
        if key not in self.store:
            self.store[key] = []
        self.store[key].append((timestamp, value))

    def get(self, key, timestamp):
        if key not in self.store:
            return ""

        arr = self.store[key]

        # Binary search
        left, right = 0, len(arr) - 1
        res = ""

        while left <= right:
            mid = (left + right) // 2

            if arr[mid][0] <= timestamp:
                res = arr[mid][1]
                left = mid + 1
            else:
                right = mid - 1

        return res
```

---

```python
import bisect

class TimeMap:

    def __init__(self):
        self.store = {}

    def set(self, key, value, timestamp):
        if key not in self.store:
            self.store[key] = []
        self.store[key].append((timestamp, value))

    def get(self, key, timestamp):
        if key not in self.store:
            return ""

        arr = self.store[key]

        i = bisect.bisect_right(arr, (timestamp, chr(127)))

        if i == 0:
            return ""
        return arr[i - 1][1]
```


set(): O(1)

get():
O(log n) (binary search)

Space:
O(n)
