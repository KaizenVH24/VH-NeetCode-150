## Two Sum

Leetcode 1 - https://leetcode.com/problems/two-sum/description/?envType=problem-list-v2&envId=wqhi32s1

## Brute Force

```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))
target = int(input("Enter target: "))

for i in range(n):
    for j in range(i + 1, n):
        if nums[i] + nums[j] == target:
            print([i, j])
            break
```
Time: O(n²) 
Space: O(1)

---

## Optimized

```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))
target = int(input("Enter target: "))

seen = {}

for i in range(n):
    needed = target - nums[i]

    if needed in seen:
        print([seen[needed], i])
        break

    seen[nums[i]] = i
```

```python
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = {}

        for i, num in enumerate(nums):
            needed = target - num

            if needed in seen:
                return [seen[needed], i]

            seen[num] = i
```

Time: O(n) 
Space: O(n)
