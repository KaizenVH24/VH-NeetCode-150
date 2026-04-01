### Merge k sorted list

Leetcode 23 - https://leetcode.com/problems/merge-k-sorted-lists/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution


user input
```python
import heapq

class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None


def merge_k_lists(lists):
    heap = []

    for i, l in enumerate(lists):
        if l:
            heapq.heappush(heap, (l.val, i, l))

    dummy = ListNode(0)
    curr = dummy

    while heap:
        val, i, node = heapq.heappop(heap)

        curr.next = node
        curr = curr.next

        if node.next:
            heapq.heappush(heap, (node.next.val, i, node.next))

    return dummy.next


def create_list(values):
    if not values:
        return None
    head = ListNode(values[0])
    curr = head
    for v in values[1:]:
        curr.next = ListNode(v)
        curr = curr.next
    return head


# -------- INPUT --------
k = int(input("Enter number of lists: "))
lists = []

for _ in range(k):
    values = list(map(int, input("Enter list: ").split()))
    lists.append(create_list(values))

# Merge
result = merge_k_lists(lists)

# -------- OUTPUT --------
curr = result
while curr:
    print(curr.val, end=" -> ")
    curr = curr.next
print("None")
```


Divide and conquer
```python
class Solution:
    def mergeKLists(self, lists):
        if not lists:
            return None

        while len(lists) > 1:
            merged = []

            for i in range(0, len(lists), 2):
                l1 = lists[i]
                l2 = lists[i+1] if i+1 < len(lists) else None
                merged.append(self.merge(l1, l2))

            lists = merged

        return lists[0]

    def merge(self, l1, l2):
        dummy = ListNode(0)
        curr = dummy

        while l1 and l2:
            if l1.val < l2.val:
                curr.next = l1
                l1 = l1.next
            else:
                curr.next = l2
                l2 = l2.next
            curr = curr.next

        curr.next = l1 or l2
        return dummy.next
```

Time: O(N log k)

Space: O(1) (excluding recursion)



using heap
```python
import heapq

class Solution:
    def mergeKLists(self, lists):
        heap = []

        # Step 1: push first nodes
        for i, l in enumerate(lists):
            if l:
                heapq.heappush(heap, (l.val, i, l))

        dummy = ListNode(0)
        curr = dummy

        while heap:
            val, i, node = heapq.heappop(heap)

            curr.next = node
            curr = curr.next

            if node.next:
                heapq.heappush(heap, (node.next.val, i, node.next))

        return dummy.next
```

