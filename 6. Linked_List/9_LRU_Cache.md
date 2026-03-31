### LRU cache

Leetcode 146 - https://leetcode.com/problems/lru-cache/description/?envType=problem-list-v2&envId=wqf75mvs

---

## Solution

user input
```python
cache = None

while True:
    cmd = input("Enter command (init/get/put/exit): ")

    if cmd == "init":
        capacity = int(input("Enter capacity: "))
        cache = LRUCache(capacity)

    elif cmd == "put":
        key, val = map(int, input("Enter key value: ").split())
        cache.put(key, val)

    elif cmd == "get":
        key = int(input("Enter key: "))
        print(cache.get(key))

    elif cmd == "exit":
        break
```

```python
class Node:
    def __init__(self, key, val):
        self.key = key
        self.val = val
        self.prev = None
        self.next = None


class LRUCache:

    def __init__(self, capacity):
        self.cap = capacity
        self.cache = {}

        # Dummy nodes
        self.left = Node(0, 0)   # LRU
        self.right = Node(0, 0)  # MRU

        self.left.next = self.right
        self.right.prev = self.left

    # Remove node
    def remove(self, node):
        prev, nxt = node.prev, node.next
        prev.next = nxt
        nxt.prev = prev

    # Insert at right (most recent)
    def insert(self, node):
        prev, nxt = self.right.prev, self.right
        prev.next = node
        node.prev = prev
        node.next = nxt
        nxt.prev = node

    def get(self, key):
        if key in self.cache:
            node = self.cache[key]
            self.remove(node)
            self.insert(node)
            return node.val
        return -1

    def put(self, key, value):
        if key in self.cache:
            self.remove(self.cache[key])

        node = Node(key, value)
        self.cache[key] = node
        self.insert(node)

        if len(self.cache) > self.cap:
            # remove LRU
            lru = self.left.next
            self.remove(lru)
            del self.cache[lru.key]
```


Time:

get - O(1)

put - O(1)

Space:
O(capacity)
