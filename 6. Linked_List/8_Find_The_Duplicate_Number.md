### Find the duplicate number

Leetcode 287 - https://leetcode.com/problems/find-the-duplicate-number/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

brute force
```python
for i in range(n):
    for j in range(i+1, n):
        if nums[i] == nums[j]:
            return nums[i]
```
Time: O(n²)
Space: O(1)


better
```python
seen = set()
for num in nums:
    if num in seen:
        return num
    seen.add(num)
```
Time: O(n)
Space: O(n)



user input
```python
def find_duplicate(nums):
    slow = nums[0]
    fast = nums[0]

    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break

    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]

    return slow


# -------- INPUT --------
nums = list(map(int, input("Enter array: ").split()))

# -------- OUTPUT --------
print("Duplicate number:", find_duplicate(nums))
```



```python
class Solution:
    def findDuplicate(self, nums):
        slow = nums[0]
        fast = nums[0]

        # Step 1: detect cycle
        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]
            if slow == fast:
                break

        # Step 2: find entrance
        slow = nums[0]
        while slow != fast:
            slow = nums[slow]
            fast = nums[fast]

        return slow
```

Time:
O(n)

Space:
O(1) 
