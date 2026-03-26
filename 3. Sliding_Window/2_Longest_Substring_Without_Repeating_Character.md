### Longest substring without repeating characters


Leetcode 3 - https://leetcode.com/problems/longest-substring-without-repeating-characters/?envType=problem-list-v2&envId=wq9nks7h

---

## Solution


user input
```python
s = input("Enter string: ")

char_set = set()
left = 0
max_length = 0

for right in range(len(s)):

    # remove until no duplicate
    while s[right] in char_set:
        char_set.remove(s[left])
        left += 1

    char_set.add(s[right])
    max_length = max(max_length, right - left + 1)

print(max_length)
```

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        char_set = set()
        left = 0
        max_length = 0

        for right in range(len(s)):

            while s[right] in char_set:
                char_set.remove(s[left])
                left += 1

            char_set.add(s[right])
            max_length = max(max_length, right - left + 1)

        return max_length
```

Time: O(n) 
Space: O(n)

---

## Other Approach

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:

        last_seen = {}
        left = 0
        max_len = 0
        
        for right in range(len(s)):
            if s[right] in last_seen and last_seen[s[right]] >= left:
                left = last_seen[s[right]] + 1

            last_seen[s[right]] = right
            max_len = max(max_len, right-left+1)

        return max_len
```
