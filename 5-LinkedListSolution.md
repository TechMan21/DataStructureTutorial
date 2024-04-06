
# Linked List Try-It-Out Solution 

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        if not self.head:
            self.head = Node(data)
        else:
            current = self.head
            while current.next:
                current = current.next
            current.next = Node(data)

    def display(self):
        elements = []
        current = self.head
        while current:
            elements.append(current.data)
            current = current.next
        print(" ".join(map(str, elements)))

    def reverse(self):
        prev = None
        current = self.head
        while current:
            next_node = current.next
            current.next = prev
            prev = current
            current = next_node
        self.head = prev

# Example Usage
if __name__ == "__main__":
    ll = LinkedList()
    for i in range(1, 6):  # Creating a list of numbers 1-5
        ll.append(i)
    
    print("Original Linked List:")
    ll.display()

    ll.reverse()  # Reversing the linked list

    print("Reversed Linked List:")
    ll.display()
```

**Solution does not need to match exactly, just work the same.**


Back to [Linked List Information](2-linkedList.md) page

OR

Back to [Welcome Page](0-welcome.md)