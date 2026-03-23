### Valid Anagram

Leetcode 242 - https://leetcode.com/problems/valid-anagram/description/?envType=problem-list-v2&envId=wqhi32s1


## Brute Force

```python
s = input("Enter first string: ")
t = input("Enter second string: ")

if sorted(s) == sorted(t):
    print(True)
else:
    print(False)
```
Time: O(n log n) (sorting)
Space: O(n)

---

## Optimized ( Leetcode / Normal )

```python
s = input("Enter first string: ")
t = input("Enter second string: ")

if len(s) != len(t):
    print(False)
else:
    count = {}

    for ch in s:
        count[ch] = count.get(ch, 0) + 1

    for ch in t:
        if ch not in count:
            print(False)
            break
        count[ch] -= 1
        if count[ch] < 0:
            print(False)
            break
    else:
        print(True)
```

```python
from typing import List

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        count = {}

        for ch in s:
            count[ch] = count.get(ch, 0) + 1

        for ch in t:
            if ch not in count:
                return False
            count[ch] -= 1
            if count[ch] < 0:
                return False

        return True
```

Time: O(n)
Space: O(1) (fixed alphabet)

### Shortcut

```python
from collections import Counter

class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return Counter(s) == Counter(t)
```
