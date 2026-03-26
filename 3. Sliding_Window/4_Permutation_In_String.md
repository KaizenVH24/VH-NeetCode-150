### Permutation in string

Leetcode 567 - https://leetcode.com/problems/permutation-in-string/description/?envType=problem-list-v2&envId=wq9nks7h

---

## Solution

user input
```python
s1 = input("Enter s1: ")
s2 = input("Enter s2: ")

from collections import Counter

len1 = len(s1)
len2 = len(s2)

if len1 > len2:
    print(False)
else:
    count1 = Counter(s1)
    window = Counter(s2[:len1])

    if count1 == window:
        print(True)
    else:
        for i in range(len1, len2):
            # add new char
            window[s2[i]] += 1

            # remove old char
            window[s2[i - len1]] -= 1
            if window[s2[i - len1]] == 0:
                del window[s2[i - len1]]

            if window == count1:
                print(True)
                break
        else:
            print(False)
```

```python
from collections import Counter

class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        if len(s1) > len(s2):
            return False

        count1 = Counter(s1)
        window = Counter(s2[:len(s1)])

        if count1 == window:
            return True

        for i in range(len(s1), len(s2)):
            window[s2[i]] += 1
            window[s2[i - len(s1)]] -= 1

            if window[s2[i - len(s1)]] == 0:
                del window[s2[i - len(s1)]]

            if window == count1:
                return True

        return False
```

Time: O(n)
Space: O(1) (26 chars)
