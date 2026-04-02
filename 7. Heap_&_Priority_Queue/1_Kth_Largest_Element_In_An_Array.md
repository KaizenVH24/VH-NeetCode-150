### Kth largest element in array

Leetcode 215 - https://leetcode.com/problems/kth-largest-element-in-an-array/description/?envType=problem-list-v2&envId=wqfi8slc

---

## Solution


Brute Force
```python
def kth_largest(nums, k):
    nums.sort()
    return nums[-k]

nums = list(map(int, input("Enter numbers: ").split()))
k = int(input("Enter k: "))

print(kth_largest(nums, k))

#Time: O(n log n) (sorting)
#Space: O(1)
```

Optimal ( min heap )
```python
import heapq

def kth_largest(nums, k):
    heap = []

    for num in nums:
        heapq.heappush(heap, num)
        
        if len(heap) > k:
            heapq.heappop(heap)

    return heap[0]

nums = list(map(int, input("Enter numbers: ").split()))
k = int(input("Enter k: "))

print(kth_largest(nums, k))

#Time: O(n log k) (better than n log n)
#Space: O(k)
```


other approach ( quick sort )
```python
import random

def quickselect(nums, k):
    k = len(nums) - k  # convert to kth smallest index

    def helper(left, right):
        pivot = nums[right]
        p = left

        for i in range(left, right):
            if nums[i] <= pivot:
                nums[p], nums[i] = nums[i], nums[p]
                p += 1

        nums[p], nums[right] = nums[right], nums[p]

        if p == k:
            return nums[p]
        elif p < k:
            return helper(p + 1, right)
        else:
            return helper(left, p - 1)

    return helper(0, len(nums) - 1)


nums = list(map(int, input("Enter numbers: ").split()))
k = int(input("Enter k: "))

print(quickselect(nums, k))

#Average: O(n)
#Worst: O(n²)
#Space: O(1)
```
