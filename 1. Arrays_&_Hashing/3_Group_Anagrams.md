### Group Anagram

Leetcode 42 - https://leetcode.com/problems/group-anagrams/description/?envType=problem-list-v2&envId=wqhi32s1

## Solution ( sorting )

```python
n = int(input("Enter number of strings: "))
strs = []

for _ in range(n):
    strs.append(input())

groups = {}

for word in strs:
    key = ''.join(sorted(word))

    if key not in groups:
        groups[key] = []

    groups[key].append(word)

print(list(groups.values()))
```

Time: O(n * k log k) (sorting each word)
Space: O(n * k)

---

### Optimized

```python
n = int(input("Enter number of strings: "))
strs = [input() for _ in range(n)]

groups = {}

for word in strs:
    count = [0] * 26

    for ch in word:
        count[ord(ch) - ord('a')] += 1

    key = tuple(count)

    if key not in groups:
        groups[key] = []

    groups[key].append(word)

print(list(groups.values()))
```

```python
from typing import List
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        groups = defaultdict(list)

        for word in strs:
            count = [0] * 26

            for ch in word:
                count[ord(ch) - ord('a')] += 1

            groups[tuple(count)].append(word)

        return list(groups.values())
```

Time: O(n * k) (no sorting)
Space: O(n * k)
