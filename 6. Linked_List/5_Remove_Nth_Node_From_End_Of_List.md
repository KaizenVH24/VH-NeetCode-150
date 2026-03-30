### Remove nth node from end of list

Leetcode 19 - https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def remove_nth_from_end(head, n):
    dummy = ListNode(0)
    dummy.next = head

    slow = dummy
    fast = dummy

    for _ in range(n):
        fast = fast.next

    while fast.next:
        slow = slow.next
        fast = fast.next

    slow.next = slow.next.next

    return dummy.next


# -------- INPUT --------
values = list(map(int, input("Enter values: ").split()))
n = int(input("Enter n: "))

# Create list
if not values:
    head = None
else:
    head = ListNode(values[0])
    curr = head
    for val in values[1:]:
        curr.next = ListNode(val)
        curr = curr.next

# Remove node
new_head = remove_nth_from_end(head, n)

# -------- OUTPUT --------
curr = new_head
while curr:
    print(curr.val, end=" -> ")
    curr = curr.next
print("None")
```


```python
class Solution:
    def removeNthFromEnd(self, head, n):
        dummy = ListNode(0)
        dummy.next = head

        slow = dummy
        fast = dummy

        # Move fast n steps
        for _ in range(n):
            fast = fast.next

        # Move both
        while fast.next:
            slow = slow.next
            fast = fast.next

        # Delete node
        slow.next = slow.next.next

        return dummy.next
```

Time:
Single traversal - O(n) 

Space:
No extra memory - O(1) 
