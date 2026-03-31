### Add two numbers

Leetcode 02 - https://leetcode.com/problems/add-two-numbers/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def add_two_numbers(l1, l2):
    dummy = ListNode(0)
    curr = dummy

    carry = 0

    while l1 or l2 or carry:
        val1 = l1.val if l1 else 0
        val2 = l2.val if l2 else 0

        total = val1 + val2 + carry

        carry = total // 10
        digit = total % 10

        curr.next = ListNode(digit)
        curr = curr.next

        if l1:
            l1 = l1.next
        if l2:
            l2 = l2.next

    return dummy.next


# -------- INPUT --------
list1_vals = list(map(int, input("Enter list1: ").split()))
list2_vals = list(map(int, input("Enter list2: ").split()))

def create_list(values):
    head = ListNode(values[0])
    curr = head
    for val in values[1:]:
        curr.next = ListNode(val)
        curr = curr.next
    return head

l1 = create_list(list1_vals)
l2 = create_list(list2_vals)

# Add
result = add_two_numbers(l1, l2)

# -------- OUTPUT --------
curr = result
while curr:
    print(curr.val, end=" -> ")
    curr = curr.next
print("None")
```

```python
class Solution:
    def addTwoNumbers(self, l1, l2):
        dummy = ListNode(0)
        curr = dummy

        carry = 0

        while l1 or l2 or carry:
            val1 = l1.val if l1 else 0
            val2 = l2.val if l2 else 0

            total = val1 + val2 + carry

            carry = total // 10
            digit = total % 10

            curr.next = ListNode(digit)
            curr = curr.next

            if l1:
                l1 = l1.next
            if l2:
                l2 = l2.next

        return dummy.next
```



Time:
Traverse both lists - O(max(n, m)

Space:
New list created - O(max(n, m))
