### Minimum window substring

Leetcode 76 - https://leetcode.com/problems/minimum-window-substring/description/?envType=problem-list-v2&envId=wq9nks7h

---

## Solution

user input
```python
s = input("Enter string s: ")
t = input("Enter string t: ")

from collections import Counter

if len(t) > len(s):
    print("")
else:
    need = Counter(t)
    window = {}

    have = 0
    need_count = len(need)

    left = 0
    res = [-1, -1]
    res_len = float("inf")

    for right in range(len(s)):
        char = s[right]
        window[char] = window.get(char, 0) + 1

        if char in need and window[char] == need[char]:
            have += 1

        # shrink window
        while have == need_count:
            # update result
            if (right - left + 1) < res_len:
                res = [left, right]
                res_len = right - left + 1

            window[s[left]] -= 1

            if s[left] in need and window[s[left]] < need[s[left]]:
                have -= 1

            left += 1

    l, r = res
    print(s[l:r+1] if res_len != float("inf") else "")
```

```python
from collections import Counter

class Solution:
    def minWindow(self, s: str, t: str) -> str:
        if len(t) > len(s):
            return ""

        need = Counter(t)
        window = {}

        have = 0
        need_count = len(need)

        left = 0
        res = [-1, -1]
        res_len = float("inf")

        for right in range(len(s)):
            char = s[right]
            window[char] = window.get(char, 0) + 1

            if char in need and window[char] == need[char]:
                have += 1

            while have == need_count:
                if (right - left + 1) < res_len:
                    res = [left, right]
                    res_len = right - left + 1

                window[s[left]] -= 1
                if s[left] in need and window[s[left]] < need[s[left]]:
                    have -= 1

                left += 1

        l, r = res
        return s[l:r+1] if res_len != float("inf") else ""
```

Time: O(m + n) 
Space: O(n)
