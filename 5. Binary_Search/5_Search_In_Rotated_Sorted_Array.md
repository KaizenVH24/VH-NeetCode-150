### Search in rotated sorted array

Leetcode 33 - https://leetcode.com/problems/search-in-rotated-sorted-array/description/?envType=problem-list-v2&envId=wqs4pyq1

---

## Solution

Brute force
```python
for i in range(len(nums)):
    if nums[i] == target:
        return i
```

user input
```python
def search(nums, target):
    left, right = 0, len(nums) - 1

    while left <= right:
        mid = (left + right) // 2

        if nums[mid] == target:
            return mid

        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1

    return -1


# Input
nums = list(map(int, input("Enter rotated array: ").split()))
target = int(input("Enter target: "))

print("Index:", search(nums, target))
```

```python
class Solution:
    def search(self, nums, target):
        left, right = 0, len(nums) - 1

        while left <= right:
            mid = (left + right) // 2

            if nums[mid] == target:
                return mid

            # Left half sorted
            if nums[left] <= nums[mid]:
                if nums[left] <= target < nums[mid]:
                    right = mid - 1
                else:
                    left = mid + 1

            # Right half sorted
            else:
                if nums[mid] < target <= nums[right]:
                    left = mid + 1
                else:
                    right = mid - 1

        return -1
```


Time: O(log n)

Binary search

Space: O(1)
