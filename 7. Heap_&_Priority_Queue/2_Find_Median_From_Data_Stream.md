### Find median from data stream

Leetcode 295 - https://leetcode.com/problems/find-median-from-data-stream/description/?envType=problem-list-v2&envId=wqfi8slc

---

## Solution

Brute force
```python
class MedianFinder:

    def __init__(self):
        self.arr = []

    def addNum(self, num: int) -> None:
        self.arr.append(num)
        self.arr.sort()

    def findMedian(self) -> float:
        n = len(self.arr)
        if n % 2 == 1:
            return self.arr[n // 2]
        else:
            return (self.arr[n // 2] + self.arr[n // 2 - 1]) / 2

addNum: O(n log n)
findMedian: O(1)
```

optimal - two heaps
```python
import heapq

class MedianFinder:

    def __init__(self):
        self.small = []  # max heap (store negative)
        self.large = []  # min heap

    def addNum(self, num: int) -> None:
        # Step 1: push into max heap
        heapq.heappush(self.small, -num)

        # Step 2: balance heaps (ensure order)
        if self.small and self.large and (-self.small[0] > self.large[0]):
            val = -heapq.heappop(self.small)
            heapq.heappush(self.large, val)

        # Step 3: maintain size balance
        if len(self.small) > len(self.large) + 1:
            val = -heapq.heappop(self.small)
            heapq.heappush(self.large, val)

        if len(self.large) > len(self.small):
            val = heapq.heappop(self.large)
            heapq.heappush(self.small, -val)

    def findMedian(self) -> float:
        if len(self.small) > len(self.large):
            return -self.small[0]
        return (-self.small[0] + self.large[0]) / 2
```


user input
```python
import heapq

class MedianFinder:
    def __init__(self):
        self.small = []
        self.large = []

    def addNum(self, num):
        heapq.heappush(self.small, -num)

        if self.small and self.large and (-self.small[0] > self.large[0]):
            val = -heapq.heappop(self.small)
            heapq.heappush(self.large, val)

        if len(self.small) > len(self.large) + 1:
            val = -heapq.heappop(self.small)
            heapq.heappush(self.large, val)

        if len(self.large) > len(self.small):
            val = heapq.heappop(self.large)
            heapq.heappush(self.small, -val)

    def findMedian(self):
        if len(self.small) > len(self.large):
            return -self.small[0]
        return (-self.small[0] + self.large[0]) / 2


mf = MedianFinder()

n = int(input("How many numbers? "))
for _ in range(n):
    num = int(input("Enter number: "))
    mf.addNum(num)
    print("Current Median:", mf.findMedian())

addNum	O(log n) 
findMedian	O(1) 
Space: O(n)
```

