# **Linked Lists**

A linked list is a fundamental data structure in computer science used to store a sequence of elements.

**What is a Linked List?** 

 Unlike arrays, where elements are stored in contiguous memory locations, a linked list consists of nodes, each containing a data element and a reference (or pointer) to the next node in the sequence. 

 ![ Image showing a new link being added to a Linked List](https://github.com/TechMan21/DataStructureTutorial/blob/8ad7738f32efb7c000709944bb2f8f7f4b78a741/C_language_linked_list.png "Link added- LinkedList Example")

## **Structure**
### Components of a Linked list are:
- **Node**: The fundamental unit of a linked list, which holds two pieces of information:
  - **Data**: The actual value stored in the node.
  - **Next**: A pointer (or reference) to the next node in the list. In the case of a singly linked list, this is a single reference. In a doubly linked list, there are two references per node: one to the next node and one to the previous node.
- **Head**: The first node in the linked list. The entry point for any traversal or operation on the list, as it gives access to the rest of the elements by following the next references.

- **Tail**: The last node in the linked list, which is unique because its next reference is null (or None in Python), indicating the end of the list.

### There are different types of linked lists, such as:

- **Singly Linked List**: Each node points to the next node in the sequence.
- **Doubly Linked List**: Each node points to both the next and previous nodes in the sequence.
- **Circular Linked List**: The last node points back to the first node, creating a circular structure.

### Advantages of Linked Lists:
- Dynamic Size: Unlike arrays, linked lists are dynamic in size and can grow or shrink as needed, without needing to allocate or deallocate memory upfront.

- Ease of Insertion/Deletion: Adding or removing nodes from a linked list is relatively simple and efficient. Unlike arrays, there's no need to shift elements after an insertion or deletion operation, except when updating pointers.

### Disadvantages of Linked Lists:
- Linear Access: Elements in a linked list must be accessed sequentially from the beginning (head). Random access is not feasible as it is with arrays.

- Memory Overhead: Each node in a linked list requires extra memory for storing the reference to the next (and possibly previous) node, in addition to the data itself.


## **Insertion Process**
   Inserting into a linked list differs from a dynamic list, as it requires a multi-step process rather than a single command like `.append()`. There are distinct procedures for inserting at the beginning, end, or middle of the list, each involving specific steps to adjust node links.

1. **Insertion at the Beginning:**
   - Inserting at the beginning involves four key steps to rearrange node links:
     1. Create the new node.
     2. Update the `next` link of the new node to point to the current head (`new_node.next = self.head`).
     3. Update the `prev` link of the current head node to point to the new node (`self.head.prev = new_node`).
     4. Set the head of the list to the new node (`self.head = new_node`).

2. **Insertion at the End:**
   - Similarly, adding an element to the end of the list follows a sequence of steps:
     1. Update the `prev` link of the new node to point to the current tail (`new_node.prev = self.tail`).
     2. Update the `next` link of the current tail node to point to the new node (`self.tail.next = new_node`).
     3. Set the tail of the list to the new node (`self.tail = new_node`).

3. **Insertion in the Middle:**
   - Inserting into the middle of the list requires five steps:
     1. Create the new node.
     2. Update the `prev` link of the new node to point to the current node (`new_node.prev = current`).
     3. Update the `next` link of the new node to point to the next node (`new_node.next = current.next`).
     4. Update the `prev` link of the next node to point to the new node (`current.next.prev = new_node`).
     5. Update the `next` link of the current node to point to the new node (`current.next = new_node`).



## **Removal Process:**
   Removing an element from a linked list requires updating the links between nodes to exclude the element to be removed. Similar to insertion, there are distinct procedures for removing from the beginning, end, or middle of the list, each involving specific steps to adjust node links.

1. **Removal from the Beginning:**
   - Removing from the beginning involves three key steps to rearrange node links:
     1. Update the head of the list to point to the next node (`self.head = self.head.next`).
     2. Set the `prev` link of the new head node to `None` if it exists (`if self.head: self.head.prev = None`).

2. **Removal from the End:**
   - Similarly, removing an element from the end of the list follows a sequence of steps:
     1. Update the tail of the list to point to the previous node (`self.tail = self.tail.prev`).
     2. Set the `next` link of the new tail node to `None` if it exists (`if self.tail: self.tail.next = None`).

3. **Removal in the Middle:**
   - Removing from the middle of the list requires four steps:
     1. Traverse the list to locate the node to be removed.
     2. Update the `next` link of the previous node to point to the next node of the node to be removed (`previous_node.next = current_node.next`).
     3. Update the `prev` link of the next node to point to the previous node of the node to be removed (`if current_node.next: current_node.next.prev = previous_node`).
     4. Set the `next` and `prev` links of the node to be removed to `None` to disconnect it from the list (`current_node.next = current_node.prev = None`).




## **The Accessing Process (finding the node you want)**
Accessing an element in a linked list requires traversing the list from the head (or tail) until the desired position is reached. This traversal involves following the `next` links of each node until the target node is found.

**Access by Position:**
- Accessing by position involves traversing the list starting from the head (or tail) and moving to the next node until the desired position is reached. This process continues until the desired position is reached or until the end of the list is reached.
   - Sample: 
   ```python
   def access_by_position(self, position):
       current = self.head
       count = 0
       while current is not None and count < position:
           current = current.next
           count += 1
       if current is None:
           # Handle out-of-bounds access
           return None
       else:
           return current.data
        
           

**Access by Value:**
- Accessing by value requires traversing the list starting from the head (or tail) and comparing the value of each node with the target value. If a match is found, the corresponding node is returned; otherwise, the traversal continues until the end of the list is reached.
    - Sample: 
   ```python
   def access_by_value(self, value):
    current = self.head
    while current is not None:
        if current.data == value:
            return current
        current = current.next
    # Handle case when value is not found
    return None


**Handling Edge Cases:**
- When accessing by position, it's important to check for edge cases such as accessing positions beyond the bounds of the list. In such cases, appropriate error handling or default return values should be implemented to handle out-of-bounds access.
    - Sample: 
   ```python
   def access_by_position(self, position):
    # Check if position is out of bounds
    if position < 0 or position >= self.length():
        # Handle out-of-bounds access
        return None
    # Continue with traversal
    ...


**Efficiency Considerations:**
- The efficiency of accessing elements in a linked list depends on the length of the list and the position of the target element. Accessing elements closer to the head or tail is generally more efficient than accessing elements in the middle of a large list.

**Traversal Techniques:**
- Traversal can be implemented using iterative or recursive techniques, depending on the preferences and requirements of the implementation. Iterative traversal involves using a loop to move through the list, while recursive traversal involves calling a function recursively to traverse the list.


## **Example Code**
Here's an example code of a singly linked list in Python:

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None  # Initialize next pointer to None

class LinkedList:
    def __init__(self):
        self.head = None  # Initialize empty linked list
    
    def append(self, data):
        new_node = Node(data)
        if not self.head:  # If the linked list is empty
            self.head = new_node
            return
        last_node = self.head
        while last_node.next:  # Traverse until the last node
            last_node = last_node.next
        last_node.next = new_node  # Link the new node to the last node
    
    def display(self):
        current = self.head
        while current:
            print(current.data, end=" ")
            current = current.next
        print()

# Example Usage
if __name__ == "__main__":
    # Creating a linked list
    ll = LinkedList()
    ll.append(1)
    ll.append(2)
    ll.append(3)

    # Displaying the linked list
    print("Linked List:")
    ll.display()

```

## **Try-It-Out**

**Task:** Implement a Method to Reverse a Linked List
Objective: Extend the provided linked list implementation with a method to reverse the list in place. This means you'll modify the list so that the elements are in the opposite order from their original insertion order.

**Background**: Reversing a linked list is a common operation in data structures, which tests your understanding of pointers and the manipulation of node connections.

**Instructions:**
Review the Provided Code: Start with the linked list implementation we discussed. Understand how nodes are added and how the list is traversed.

**Plan Your Approach:** Think about how you can reverse the pointers between nodes to reverse the list. You might need temporary variables to hold nodes as you adjust their .next pointers.

**Implement the reverse Method:** Add a new method to the LinkedList class named reverse. This method should reverse the nodes' order in the linked list. After reversing, what was the last node will become the first, and the original first node will become the last, with all pointers correctly adjusted.

**Test Your Implementation:** After implementing the reverse method, create a linked list, append a few numbers to it, and use the .display() method to print out the list. Then, call your reverse method and display the list again to ensure it is now in reverse order.

**Reflect on Your Solution:** Consider the time and space complexity of your solution. Can you identify any improvements or alternative approaches?

**Once you have completed the task you can view the [solution](5-LinkedListSolution.md) to check for accuracy and completeness.**

Back to [Welcome Page](0-welcome.md)