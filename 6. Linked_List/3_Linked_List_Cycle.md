### Linked list cycle

Leetcode 141 - https://leetcode.com/problems/linked-list-cycle/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def create_list(values, pos):
    if not values:
        return None

    head = ListNode(values[0])
    curr = head
    nodes = [head]

    for val in values[1:]:
        new_node = ListNode(val)
        curr.next = new_node
        curr = new_node
        nodes.append(new_node)

    # Create cycle
    if pos != -1:
        curr.next = nodes[pos]

    return head


def has_cycle(head):
    slow = head
    fast = head

    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next

        if slow == fast:
            return True

    return False


# -------- INPUT --------
values = list(map(int, input("Enter values: ").split()))
pos = int(input("Enter cycle position (-1 for no cycle): "))

head = create_list(values, pos)

# -------- OUTPUT --------
print("Cycle exists?" , has_cycle(head))
```


Brute Force 
```python
class Solution:
    def hasCycle(self, head):
        visited = set()

        curr = head
        while curr:
            if curr in visited:
                return True
            visited.add(curr)
            curr = curr.next

        return False
```

Time: O(n)
Space: O(n)



Optimal **(Floyd’s Cycle Detection)**
```python
class Solution:
    def hasCycle(self, head):
        slow = head
        fast = head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next

            if slow == fast:
                return True

        return False
```

Time: O(n)

Space: O(1) 
