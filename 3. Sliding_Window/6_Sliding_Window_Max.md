### Sliding window maximum

Leetcode 239 - https://leetcode.com/problems/sliding-window-maximum/description/?envType=problem-list-v2&envId=wq9nks7h

--- 

## Solution

user input
```python
from collections import deque

n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))
k = int(input("Enter k: "))

dq = deque()
result = []

for i in range(n):

    # remove smaller elements from back
    while dq and nums[dq[-1]] < nums[i]:
        dq.pop()

    dq.append(i)

    # remove out-of-window index
    if dq[0] <= i - k:
        dq.popleft()

    # add result when window is ready
    if i >= k - 1:
        result.append(nums[dq[0]])

print(result)
```

```python
from typing import List
from collections import deque

class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        dq = deque()
        result = []

        for i in range(len(nums)):

            while dq and nums[dq[-1]] < nums[i]:
                dq.pop()

            dq.append(i)

            if dq[0] <= i - k:
                dq.popleft()

            if i >= k - 1:
                result.append(nums[dq[0]])

        return result
```


Time: O(n)
Space: O(k)
