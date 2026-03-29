### Find minimum in rotated sorted array


Leetcode 153 - https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/?envType=problem-list-v2&envId=wqs4pyq1

---

## Solution


user input
```python
def findMin(nums):
    left, right = 0, len(nums) - 1

    while left < right:
        mid = (left + right) // 2

        if nums[mid] > nums[right]:
            left = mid + 1
        else:
            right = mid

    return nums[left]


# Input
nums = list(map(int, input("Enter rotated sorted array: ").split()))

print("Minimum element:", findMin(nums))
```


```python
class Solution:
    def findMin(self, nums):
        left, right = 0, len(nums) - 1

        while left < right:
            mid = (left + right) // 2

            if nums[mid] > nums[right]:
                left = mid + 1
            else:
                right = mid

        return nums[left]
```


Time: O(log n)

Binary search

Space: O(1)


## Shortcut

```python
return min(nums) - O(n)
```
