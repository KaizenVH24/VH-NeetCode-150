### Valid Palindrome

Leetcode 125 - https://leetcode.com/problems/valid-palindrome/description/?envType=problem-list-v2&envId=wq9noq2t

---


## Solution


```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s)-1

        while l < r:
            while l < r and not s[l].isalnum():
                l += 1
            while l < r and not s[r].isalnum():
                r -= 1
            
            if s[l].lower() != s[r].lower():
                return False
            
            l += 1
            r -= 1
        return True
```

User Input
```python
s = input("Enter string: ")

left = 0
right = len(s) - 1

valid = True

while left < right:

    # skip non-alphanumeric
    while left < right and not s[left].isalnum():
        left += 1

    while left < right and not s[right].isalnum():
        right -= 1

    if s[left].lower() != s[right].lower():
        valid = False
        break

    left += 1
    right -= 1

print(valid)
```

Time: O(n) 
Space: O(1) (no extra string)
