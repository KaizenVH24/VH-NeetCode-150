## Two Sum II - Input array is sorted

Leetcode 167 - https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/?envType=problem-list-v2&envId=wq9noq2t

---

### Solutiom


User Input:
```python
n = int(input("Enter number of elements: "))
numbers = list(map(int, input("Enter sorted elements: ").split()))
target = int(input("Enter target: "))

left = 0
right = n - 1

while left < right:
    curr_sum = numbers[left] + numbers[right]

    if curr_sum == target:
        print([left + 1, right + 1])  # 1-based index
        break

    elif curr_sum < target:
        left += 1

    else:
        right -= 1
```

```python
from typing import List

class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        left, right = 0, len(numbers) - 1

        while left < right:
            curr_sum = numbers[left] + numbers[right]

            if curr_sum == target:
                return [left + 1, right + 1]

            elif curr_sum < target:
                left += 1
            else:
                right -= 1
```


Time: O(n) 
Space: O(1)

