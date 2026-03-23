### Valid Sudoku

Leetcode 36 - https://leetcode.com/problems/valid-sudoku/description/?envType=problem-list-v2&envId=wqhi32s1


## Optimized Solutions

```python
board = []

print("Enter Sudoku board (9 rows, space separated):")
for _ in range(9):
    row = input().split()
    board.append(row)

rows = [set() for _ in range(9)]
cols = [set() for _ in range(9)]
boxes = [set() for _ in range(9)]

valid = True

for r in range(9):
    for c in range(9):
        val = board[r][c]

        if val == '.':
            continue

        box_index = (r // 3) * 3 + (c // 3)

        if val in rows[r] or val in cols[c] or val in boxes[box_index]:
            valid = False
            break

        rows[r].add(val)
        cols[c].add(val)
        boxes[box_index].add(val)

    if not valid:
        break

print(valid)
```

```python
from typing import List

class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        rows = [set() for _ in range(9)]
        cols = [set() for _ in range(9)]
        boxes = [set() for _ in range(9)]

        for r in range(9):
            for c in range(9):
                val = board[r][c]

                if val == '.':
                    continue

                box_index = (r // 3) * 3 + (c // 3)

                if val in rows[r] or val in cols[c] or val in boxes[box_index]:
                    return False

                rows[r].add(val)
                cols[c].add(val)
                boxes[box_index].add(val)

        return True
```

Time: O(1)
(Board is always 9×9 → constant)


Space: O(1)
(Fixed size sets)
