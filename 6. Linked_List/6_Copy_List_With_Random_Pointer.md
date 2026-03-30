### Copy list with random pointer

Leetcode 138 - https://leetcode.com/problems/copy-list-with-random-pointer/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None
        self.random = None


def copy_random_list(head):
    if not head:
        return None

    # Step 1
    curr = head
    while curr:
        new_node = Node(curr.val)
        new_node.next = curr.next
        curr.next = new_node
        curr = new_node.next

    # Step 2
    curr = head
    while curr:
        if curr.random:
            curr.next.random = curr.random.next
        curr = curr.next.next

    # Step 3
    curr = head
    copy_head = head.next
    copy = copy_head

    while curr:
        curr.next = curr.next.next
        if copy.next:
            copy.next = copy.next.next

        curr = curr.next
        copy = copy.next

    return copy_head
```


```python
class Solution:
    def copyRandomList(self, head):
        if not head:
            return None

        # Step 1: Insert copy nodes
        curr = head
        while curr:
            new_node = Node(curr.val)
            new_node.next = curr.next
            curr.next = new_node
            curr = new_node.next

        # Step 2: Assign random pointers
        curr = head
        while curr:
            if curr.random:
                curr.next.random = curr.random.next
            curr = curr.next.next

        # Step 3: Separate lists
        curr = head
        copy_head = head.next
        copy = copy_head

        while curr:
            curr.next = curr.next.next
            if copy.next:
                copy.next = copy.next.next

            curr = curr.next
            copy = copy.next

        return copy_head
```


Time:
Traverse 3 times - O(n) 

Space:
O(1) 
