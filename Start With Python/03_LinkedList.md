#### Linked List
```
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next
```
##### Creating 
1. Using Python List
```
def build_linked_list(arr):
    dummy = ListNode()
    curr = dummy
    for x in arr:
        curr.next = ListNode(x)
        curr = curr.next
    return dummy.next

```
2. Manually
```
head = ListNode(1)
head.next = ListNode(2)
head.next.next = ListNode(3)
```
3. Reverse A LinkedList
```
def reverseList(head):
    prev = None
    curr = head
    while curr:
        nxt = curr.next
        curr.next = prev
        prev = curr
        curr = nxt
    return prev
```
