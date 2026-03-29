### Binary Search

Leetcode 704 - https://leetcode.com/problems/binary-search/?envType=problem-list-v2&envId=wqs4pyq1

---

## Solution

user input
```python
def binary_search(nums, target):
    left, right = 0, len(nums) - 1

    while left <= right:
        mid = (left + right) // 2

        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1

    return -1


# Input
nums = list(map(int, input("Enter sorted array: ").split()))
target = int(input("Enter target: "))

result = binary_search(nums, target)

if result != -1:
    print("Found at index:", result)
else:
    print("Not found")
```


```python
class Solution:
    def search(self, nums, target):
        left, right = 0, len(nums) - 1

        while left <= right:
            mid = (left + right) // 2

            if nums[mid] == target:
                return mid

            elif nums[mid] < target:
                left = mid + 1

            else:
                right = mid - 1

        return -1
```


Time: O(log n) 

Each step cuts array in half

Space: O(1)

No extra memory
