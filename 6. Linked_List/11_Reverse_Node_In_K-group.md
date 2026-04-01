### Reverse node in k-group

Leetcode 25 - https://leetcode.com/problems/reverse-nodes-in-k-group/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution


user input
```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def reverse_k_group(head, k):
    dummy = ListNode(0)
    dummy.next = head
    groupPrev = dummy

    while True:
        kth = groupPrev
        for _ in range(k):
            kth = kth.next
            if not kth:
                return dummy.next

        groupNext = kth.next

        prev = groupNext
        curr = groupPrev.next

        while curr != groupNext:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp

        temp = groupPrev.next
        groupPrev.next = kth
        groupPrev = temp


# -------- INPUT --------
values = list(map(int, input("Enter values: ").split()))
k = int(input("Enter k: "))

# Create list
if not values:
    head = None
else:
    head = ListNode(values[0])
    curr = head
    for val in values[1:]:
        curr.next = ListNode(val)
        curr = curr.next

# Reverse
new_head = reverse_k_group(head, k)

# -------- OUTPUT --------
curr = new_head
while curr:
    print(curr.val, end=" -> ")
    curr = curr.next
print("None")
```


```python
class Solution:
    def reverseKGroup(self, head, k):
        dummy = ListNode(0)
        dummy.next = head
        groupPrev = dummy

        while True:
            # Step 1: find kth node
            kth = groupPrev
            for _ in range(k):
                kth = kth.next
                if not kth:
                    return dummy.next

            groupNext = kth.next

            # Step 2: reverse group
            prev = groupNext
            curr = groupPrev.next

            while curr != groupNext:
                temp = curr.next
                curr.next = prev
                prev = curr
                curr = temp

            # Step 3: reconnect
            temp = groupPrev.next
            groupPrev.next = kth
            groupPrev = temp
```


Time:
Each node visited once - O(n)

Space:
No extra memory - O(1)
