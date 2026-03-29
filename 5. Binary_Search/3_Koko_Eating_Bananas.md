### Koko eating bananas

Leetcode 875 - https://leetcode.com/problems/koko-eating-bananas/description/?envType=problem-list-v2&envId=wqs4pyq1

---


## Solution


user input
```python
def minEatingSpeed(piles, h):
    left, right = 1, max(piles)

    while left <= right:
        mid = (left + right) // 2

        total_hours = 0
        for p in piles:
            total_hours += (p + mid - 1) // mid

        if total_hours <= h:
            right = mid - 1
        else:
            left = mid + 1

    return left


# Input
piles = list(map(int, input("Enter piles: ").split()))
h = int(input("Enter hours: "))

print("Minimum speed:", minEatingSpeed(piles, h))
```


```python
class Solution:
    def minEatingSpeed(self, piles, h):
        left, right = 1, max(piles)

        while left <= right:
            mid = (left + right) // 2

            total_hours = 0
            for p in piles:
                total_hours += (p + mid - 1) // mid

            if total_hours <= h:
                right = mid - 1  # try smaller speed
            else:
                left = mid + 1   # need more speed

        return left
```


Time: O(n log max(pile))

binary search - log(max)
| each check - O(n)

Space: O(1)
