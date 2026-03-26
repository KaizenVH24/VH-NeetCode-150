### Longest repeating character replacement


Leetcode 424 - https://leetcode.com/problems/longest-repeating-character-replacement/description/?envType=problem-list-v2&envId=wq9nks7h

---

## Solution

user input
```python
s = input("Enter string: ")
k = int(input("Enter k: "))

count = {}
left = 0
max_freq = 0
max_length = 0

for right in range(len(s)):
    count[s[right]] = count.get(s[right], 0) + 1

    max_freq = max(max_freq, count[s[right]])

    # check if window is invalid
    while (right - left + 1) - max_freq > k:
        count[s[left]] -= 1
        left += 1

    max_length = max(max_length, right - left + 1)

print(max_length)
```

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        count = {}
        left = 0
        max_freq = 0
        max_length = 0

        for right in range(len(s)):
            count[s[right]] = count.get(s[right], 0) + 1

            max_freq = max(max_freq, count[s[right]])

            while (right - left + 1) - max_freq > k:
                count[s[left]] -= 1
                left += 1

            max_length = max(max_length, right - left + 1)

        return max_length
```


Time: O(n) 
Space: O(1) (only 26 chars)
