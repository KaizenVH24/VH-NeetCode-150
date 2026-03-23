### Product of array except self

Leetcode 238 - https://leetcode.com/problems/product-of-array-except-self/description/?envType=problem-list-v2&envId=wqhi32s1


## Brue Force

```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))

result = []

for i in range(n):
    prod = 1
    for j in range(n):
        if i != j:
            prod *= nums[j]
    result.append(prod)

print(result)
```

Time: O(n²) 
Space: O(1)

---


## Better / Optimized

```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))

left = [1] * n
right = [1] * n

# build left
for i in range(1, n):
    left[i] = left[i - 1] * nums[i - 1]

# build right
for i in range(n - 2, -1, -1):
    right[i] = right[i + 1] * nums[i + 1]

# final result
result = []
for i in range(n):
    result.append(left[i] * right[i])

print(result)
```

```python
o(1) - space
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))

result = [1] * n

# left pass
prefix = 1
for i in range(n):
    result[i] = prefix
    prefix *= nums[i]

# right pass
suffix = 1
for i in range(n - 1, -1, -1):
    result[i] *= suffix
    suffix *= nums[i]

print(result)
```

```
from typing import List

class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        result = [1] * n

        prefix = 1
        for i in range(n):
            result[i] = prefix
            prefix *= nums[i]

        suffix = 1
        for i in range(n - 1, -1, -1):
            result[i] *= suffix
            suffix *= nums[i]

        return result
```

Time: O(n)
Space: O(n)
