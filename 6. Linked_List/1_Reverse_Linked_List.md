### Reverse linked list

Leetcode 206 - https://leetcode.com/problems/reverse-linked-list/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def reverse_list(head):
    prev = None
    curr = head

    while curr:
        next_node = curr.next
        curr.next = prev
        prev = curr
        curr = next_node

    return prev


# -------- INPUT --------
values = list(map(int, input("Enter values: ").split()))

# Create linked list
head = None
if values:
    head = ListNode(values[0])
    curr = head
    for val in values[1:]:
        curr.next = ListNode(val)
        curr = curr.next

# Reverse
new_head = reverse_list(head)

# -------- OUTPUT --------
curr = new_head
while curr:
    print(curr.val, end=" -> ")
    curr = curr.next
print("None")
```


Optimal Code
```python
class Solution:
    def reverseList(self, head):
        prev = None
        curr = head

        while curr:
            next_node = curr.next  # store next
            curr.next = prev       # reverse link
            prev = curr            # move prev
            curr = next_node       # move curr

        return prev
```

Time Complexity:
Loop runs once - O(n)

Space Complexity:
No extra memory - O(1) 


---

Recursive Code
```python
class Solution:
    def reverseList(self, head):
        if not head or not head.next:
            return head

        new_head = self.reverseList(head.next)

        head.next.next = head
        head.next = None

        return new_head
```


Time: O(n)

Space: O(n) (call stack)
