### Trapping Rain Water

Leetcode 42 - https://leetcode.com/problems/trapping-rain-water/?envType=problem-list-v2&envId=wq9noq2t


## Solution


```python
n = int(input("Enter number of elements: "))
height = list(map(int, input("Enter heights: ").split()))

left_max = [0] * n
right_max = [0] * n

# left max
left_max[0] = height[0]
for i in range(1, n):
    left_max[i] = max(left_max[i-1], height[i])

# right max
right_max[n-1] = height[n-1]
for i in range(n-2, -1, -1):
    right_max[i] = max(right_max[i+1], height[i])

water = 0

for i in range(n):
    water += min(left_max[i], right_max[i]) - height[i]

print(water)
```

Time: O(n) 
Space: O(n)

---

## Better Solution


```python
n = int(input("Enter number of elements: "))
height = list(map(int, input("Enter heights: ").split()))

left = 0
right = n - 1

left_max = 0
right_max = 0

water = 0

while left < right:

    if height[left] < height[right]:

        if height[left] >= left_max:
            left_max = height[left]
        else:
            water += left_max - height[left]

        left += 1

    else:

        if height[right] >= right_max:
            right_max = height[right]
        else:
            water += right_max - height[right]

        right -= 1

print(water)
```

```python
from typing import List

class Solution:
    def trap(self, height: List[int]) -> int:
        left, right = 0, len(height) - 1
        left_max = right_max = 0
        water = 0

        while left < right:
            if height[left] < height[right]:
                if height[left] >= left_max:
                    left_max = height[left]
                else:
                    water += left_max - height[left]
                left += 1
            else:
                if height[right] >= right_max:
                    right_max = height[right]
                else:
                    water += right_max - height[right]
                right -= 1

        return water
```

Time: O(n) 
Space: O(1) 
