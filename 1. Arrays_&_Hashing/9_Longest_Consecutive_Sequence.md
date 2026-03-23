### Longest Consecutive Sequence

Leetcode 128 - https://leetcode.com/problems/longest-consecutive-sequence/description/?envType=problem-list-v2&envId=wqhi32s1


## Optimized Solutions

```python
n = int(input("Enter number of elements: "))
nums = list(map(int, input("Enter elements: ").split()))

num_set = set(nums)
longest = 0

for num in num_set:
    # check if it's a sequence start
    if num - 1 not in num_set:
        current = num
        length = 1

        while current + 1 in num_set:
            current += 1
            length += 1

        longest = max(longest, length)

print(longest)
```

```python
from typing import List

class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        num_set = set(nums)
        longest = 0

        for num in num_set:
            if num - 1 not in num_set:
                current = num
                length = 1

                while current + 1 in num_set:
                    current += 1
                    length += 1

                longest = max(longest, length)

        return longest
```

Time: O(n) 
Space: O(n)

