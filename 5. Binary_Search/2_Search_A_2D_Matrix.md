### Search a 2D matrix

Leetcode 74 - https://leetcode.com/problems/search-a-2d-matrix/description/?envType=problem-list-v2&envId=wqs4pyq1

---

## Solution

user input
```python
def searchMatrix(matrix, target):
    m, n = len(matrix), len(matrix[0])

    left, right = 0, m * n - 1

    while left <= right:
        mid = (left + right) // 2

        row = mid // n
        col = mid % n

        if matrix[row][col] == target:
            return True
        elif matrix[row][col] < target:
            left = mid + 1
        else:
            right = mid - 1

    return False


# Input
m = int(input("Enter number of rows: "))
n = int(input("Enter number of columns: "))

matrix = []
for i in range(m):
    row = list(map(int, input().split()))
    matrix.append(row)

target = int(input("Enter target: "))

print(searchMatrix(matrix, target))
```


```python
class Solution:
    def searchMatrix(self, matrix, target):
        m, n = len(matrix), len(matrix[0])

        left, right = 0, m * n - 1

        while left <= right:
            mid = (left + right) // 2

            row = mid // n
            col = mid % n

            value = matrix[row][col]

            if value == target:
                return True
            elif value < target:
                left = mid + 1
            else:
                right = mid - 1

        return False
```


Time: O(log(m × n)) 

Binary search on total elements

Space: O(1)

No extra memory
