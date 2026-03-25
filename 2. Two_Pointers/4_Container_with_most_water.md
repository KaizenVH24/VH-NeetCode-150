### Container with most water


Leetcode 11 - https://leetcode.com/problems/container-with-most-water/?envType=problem-list-v2&envId=wq9noq2t

---

## Solution

user input
```python
n = int(input("Enter number of elements: "))
height = list(map(int, input("Enter heights: ").split()))

left = 0
right = n - 1
max_area = 0

while left < right:
    h = min(height[left], height[right])
    w = right - left
    area = h * w

    max_area = max(max_area, area)

    # move the shorter line
    if height[left] < height[right]:
        left += 1
    else:
        right -= 1

print(max_area)
```

```python
from typing import List

class Solution:
    def maxArea(self, height: List[int]) -> int:
        left, right = 0, len(height) - 1
        max_area = 0

        while left < right:
            h = min(height[left], height[right])
            w = right - left
            max_area = max(max_area, h * w)

            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return max_area
```


Time: O(n)
Space: O(1)
