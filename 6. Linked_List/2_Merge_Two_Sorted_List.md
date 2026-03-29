### Merge two sorted list

Leetcode 21 - https://leetcode.com/problems/merge-two-sorted-lists/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def merge_lists(l1, l2):
    dummy = ListNode(0)
    tail = dummy

    while l1 and l2:
        if l1.val < l2.val:
            tail.next = l1
            l1 = l1.next
        else:
            tail.next = l2
            l2 = l2.next
        tail = tail.next

    if l1:
        tail.next = l1
    else:
        tail.next = l2

    return dummy.next


# -------- INPUT --------
list1_vals = list(map(int, input("Enter list1: ").split()))
list2_vals = list(map(int, input("Enter list2: ").split()))

def create_list(values):
    if not values:
        return None
    head = ListNode(values[0])
    curr = head
    for val in values[1:]:
        curr.next = ListNode(val)
        curr = curr.next
    return head

l1 = create_list(list1_vals)
l2 = create_list(list2_vals)

# Merge
merged = merge_lists(l1, l2)

# -------- OUTPUT --------
curr = merged
while curr:
    print(curr.val, end=" -> ")
    curr = curr.next
print("None")
```


```python
class Solution:
    def mergeTwoLists(self, list1, list2):
        dummy = ListNode(0)
        tail = dummy

        while list1 and list2:
            if list1.val < list2.val:
                tail.next = list1
                list1 = list1.next
            else:
                tail.next = list2
                list2 = list2.next

            tail = tail.next

        # Attach remaining
        if list1:
            tail.next = list1
        else:
            tail.next = list2

        return dummy.next
```

Time:
We traverse both lists once - O(n + m) 

Space:
No extra memory - O(1)

---

Recursive Code
```python
class Solution:
    def mergeTwoLists(self, list1, list2):
        if not list1:
            return list2
        if not list2:
            return list1

        if list1.val < list2.val:
            list1.next = self.mergeTwoLists(list1.next, list2)
            return list1
        else:
            list2.next = self.mergeTwoLists(list1, list2.next)
            return list2
```

Time: O(n + m)

Space: O(n + m) (stack) 
