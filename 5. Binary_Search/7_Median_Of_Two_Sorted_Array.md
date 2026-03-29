### Median of two sorted array

Leetcode 04 - https://leetcode.com/problems/median-of-two-sorted-arrays/description/?envType=problem-list-v2&envId=wqs4pyq1

---

## Solution

user input
```python
def findMedian(nums1, nums2):
    if len(nums1) > len(nums2):
        nums1, nums2 = nums2, nums1

    m, n = len(nums1), len(nums2)
    left, right = 0, m

    while left <= right:
        cut1 = (left + right) // 2
        cut2 = (m + n + 1) // 2 - cut1

        l1 = float('-inf') if cut1 == 0 else nums1[cut1 - 1]
        r1 = float('inf')  if cut1 == m else nums1[cut1]

        l2 = float('-inf') if cut2 == 0 else nums2[cut2 - 1]
        r2 = float('inf')  if cut2 == n else nums2[cut2]

        if l1 <= r2 and l2 <= r1:
            if (m + n) % 2 == 0:
                return (max(l1, l2) + min(r1, r2)) / 2
            else:
                return max(l1, l2)

        elif l1 > r2:
            right = cut1 - 1
        else:
            left = cut1 + 1


# Input
nums1 = list(map(int, input("Enter nums1: ").split()))
nums2 = list(map(int, input("Enter nums2: ").split()))

print("Median:", findMedian(nums1, nums2))
```

```python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        if len(nums1) > len(nums2):
            nums1, nums2 = nums2, nums1

        m, n = len(nums1), len(nums2)
        left, right = 0, m

        while left <= right:
            cut1 = (left + right) // 2
            cut2 = (m + n + 1) // 2 - cut1

            l1 = float('-inf') if cut1 == 0 else nums1[cut1 - 1]
            r1 = float('inf')  if cut1 == m else nums1[cut1]

            l2 = float('-inf') if cut2 == 0 else nums2[cut2 - 1]
            r2 = float('inf')  if cut2 == n else nums2[cut2]

            if l1 <= r2 and l2 <= r1:
                if (m + n) % 2 == 0:
                    return (max(l1, l2) + min(r1, r2)) / 2
                else:
                    return max(l1, l2)

            elif l1 > r2:
                right = cut1 - 1
            else:
                left = cut1 + 1
```

Time: O(log(min(m,n))) 

Binary search only on smaller array

Space: O(1)

--- 

```python
class Solution:
    def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        merged = sorted(nums1+nums2)
        n = len(merged)

        if n % 2 == 1:
            return merged[n//2]
        else:
            return (merged[n//2-1] + merged[n//2]) / 2
```
