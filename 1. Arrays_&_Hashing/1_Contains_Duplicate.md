### Contains Duplicate 

Leetcode - 217 - https://leetcode.com/problems/contains-duplicate/description/?envType=problem-list-v2&envId=wqhi32s1

---

## Brute Force 

```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))

found = False

for i in range(n):
    for j in range(i + 1, n):
        if nums[i] == nums[j]:
            found = True
            break
    if found:
        break

print(found)
```

-- 
Time: O(n²)
Space: O(1)

---

## Optimized Solution

Leetcode Style
```python
from typing import List

class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        seen = set()

        for num in nums:
            if num in seen:
                return True
            seen.add(num)

        return False
```

Normal
```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))

seen = set()
found = False

for num in nums:
    if num in seen:
        found = True
        break
    seen.add(num)

print(found)
```

--
Time: O(n)
Space: O(n) (extra memory for set)


