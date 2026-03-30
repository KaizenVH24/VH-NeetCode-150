### Reorder list

Leetcode 143 - https://leetcode.com/problems/reorder-list/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def reorder_list(head):
    if not head or not head.next:
        return head

    # Step 1: Find middle
    slow, fast = head, head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

    # Step 2: Reverse second half
    prev = None
    curr = slow.next
    slow.next = None

    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node

    # Step 3: Merge
    first, second = head, prev

    while second:
        temp1 = first.next
        temp2 = second.next

        first.next = second
        second.next = temp1

        first = temp1
        second = temp2

    return head


# -------- INPUT --------
values = list(map(int, input("Enter values: ").split()))

# Create list
if not values:
    head = None
else:
    head = ListNode(values[0])
    curr = head
    for val in values[1:]:
        curr.next = ListNode(val)
        curr = curr.next

# Reorder
reorder_list(head)

# -------- OUTPUT --------
curr = head
while curr:
    print(curr.val, end=" -> ")
    curr = curr.next
print("None")
```


```python
class Solution:
    def reorderList(self, head):
        if not head or not head.next:
            return

        # Step 1: Find middle
        slow, fast = head, head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

        # Step 2: Reverse second half
        prev = None
        curr = slow.next
        slow.next = None  # break list

        while curr:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node

        # Step 3: Merge two halves
        first, second = head, prev

        while second:
            temp1 = first.next
            temp2 = second.next

            first.next = second
            second.next = temp1

            first = temp1
            second = temp2
```


Time:
Find middle - O(n)
Reverse - O(n)
Merge - O(n)

Total = O(n) 

Space:
No extra memory - O(1) 
