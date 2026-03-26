### Largest rectangle in histogram

Leetcode 84 - https://leetcode.com/problems/largest-rectangle-in-histogram/description/?envType=problem-list-v2&envId=wqssdtc2

---

## Solution

user input
```python
def largestRectangleArea(heights):
    stack = []
    max_area = 0

    for i in range(len(heights)):
        while stack and heights[i] < heights[stack[-1]]:
            h = heights[stack.pop()]

            if not stack:
                width = i
            else:
                width = i - stack[-1] - 1

            max_area = max(max_area, h * width)

        stack.append(i)

    n = len(heights)
    while stack:
        h = heights[stack.pop()]

        if not stack:
            width = n
        else:
            width = n - stack[-1] - 1

        max_area = max(max_area, h * width)

    return max_area


# Input
heights = list(map(int, input("Enter heights: ").split()))

print("Max Area:", largestRectangleArea(heights))
```

```python
class Solution:
    def largestRectangleArea(self, heights):
        stack = []  # (index)
        max_area = 0

        for i in range(len(heights)):
            while stack and heights[i] < heights[stack[-1]]:
                h = heights[stack.pop()]
                
                if not stack:
                    width = i
                else:
                    width = i - stack[-1] - 1

                max_area = max(max_area, h * width)

            stack.append(i)

        # process remaining stack
        n = len(heights)
        while stack:
            h = heights[stack.pop()]
            
            if not stack:
                width = n
            else:
                width = n - stack[-1] - 1

            max_area = max(max_area, h * width)

        return max_area
```


Time: O(n)
Each element pushed + popped once

Space: O(n)
Stack
