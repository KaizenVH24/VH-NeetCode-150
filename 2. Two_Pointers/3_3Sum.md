### 3Sum

Leetcode 15 - https://leetcode.com/problems/3sum/description/?envType=problem-list-v2&envId=wq9noq2t

--- 

## Solution


user input
```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))

nums.sort()
result = []

for i in range(n):
    
    # skip duplicates
    if i > 0 and nums[i] == nums[i - 1]:
        continue

    left = i + 1
    right = n - 1

    while left < right:
        total = nums[i] + nums[left] + nums[right]

        if total == 0:
            result.append([nums[i], nums[left], nums[right]])

            left += 1
            right -= 1

            # skip duplicates
            while left < right and nums[left] == nums[left - 1]:
                left += 1

        elif total < 0:
            left += 1
        else:
            right -= 1

print(result)
```



```python
from typing import List

class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        result = []

        for i in range(len(nums)):
            
            if i > 0 and nums[i] == nums[i - 1]:
                continue

            left, right = i + 1, len(nums) - 1

            while left < right:
                total = nums[i] + nums[left] + nums[right]

                if total == 0:
                    result.append([nums[i], nums[left], nums[right]])

                    left += 1
                    right -= 1

                    while left < right and nums[left] == nums[left - 1]:
                        left += 1

                elif total < 0:
                    left += 1
                else:
                    right -= 1

        return result
```

Time: O(n²) 
Space: O(1) (ignoring output)
