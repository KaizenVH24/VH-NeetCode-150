### Top k frequent elements

Leetcode 347 - https://leetcode.com/problems/top-k-frequent-elements/description/?envType=problem-list-v2&envId=wqhi32s1

---

## Brute Force

```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))
k = int(input("Enter k: "))

from collections import Counter

count = Counter(nums)

sorted_items = sorted(count.items(), key=lambda x: x[1], reverse=True)

result = [item[0] for item in sorted_items[:k]]

print(result)
```

Time: O(n log n) (sorting)
Space: O(n)

--- 

## Better / Optimized

```python
import heapq
from collections import Counter

n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))
k = int(input("Enter k: "))

count = Counter(nums)

heap = []

for num, freq in count.items():
    heapq.heappush(heap, (-freq, num))

result = []

for _ in range(k):
    result.append(heapq.heappop(heap)[1])

print(result)
```

Time: O(n log k)
Space: O(n)

---

```python
from collections import Counter

n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))
k = int(input("Enter k: "))

count = Counter(nums)

bucket = [[] for _ in range(len(nums) + 1)]

for num, freq in count.items():
    bucket[freq].append(num)

result = []

for i in range(len(bucket) - 1, -1, -1):
    for num in bucket[i]:
        result.append(num)
        if len(result) == k:
            print(result)
            exit()
```

```python
from typing import List
from collections import Counter

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        count = Counter(nums)

        bucket = [[] for _ in range(len(nums) + 1)]

        for num, freq in count.items():
            bucket[freq].append(num)

        result = []

        for i in range(len(bucket) - 1, -1, -1):
            for num in bucket[i]:
                result.append(num)
                if len(result) == k:
                    return result
```

Time: O(n)
Space: O(n)
