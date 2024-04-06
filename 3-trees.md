# **Trees**

**What is a Tree?** 

In computer science, a tree is a hierarchical data structure that consists of nodes connected by edges. It resembles an upside-down tree, with a single root node at the top and branches extending downwards to other nodes. Each node can have zero or more child nodes, and these child nodes are typically referred to as the node's children.


## **Binary Trees**
A binary tree is a type of tree in which each node has at most two children, referred to as the left child and the right child. The structure of a binary tree naturally lends itself to recursive algorithms due to its hierarchical nature.


   ![ Image showing Binary Tree](https://github.com/TechMan21/DataStructureTutorial/blob/70fb22606883b0c9369970563621231d7b075701/BinaryTreeExColored.png "Binary Tree Example Example")

## **Binary Search Trees**

A binary search tree (BST) is a type of binary tree with an additional property: for any node in the tree, all nodes in its left subtree have values less than its value, and all nodes in its right subtree have values greater than its value. This property allows for efficient searching, insertion, and deletion operations.

  ![Image showing Binary Search Tree](https://github.com/TechMan21/DataStructureTutorial/blob/70fb22606883b0c9369970563621231d7b075701/BinarySearchTree.png "Binary Search Tree Example" )
  

- ### **Unbalanced Balanced Binary Search Trees**
   An unbalanced BST is a binary search tree in which the tree's height is not optimized, leading to inefficient operations. In the worst case, an unbalanced BST can degrade to a linear data structure, resulting in O(n) time complexity for operations like search, insertion, and deletion.

   ![Image showing Unbalanced BST](https://github.com/TechMan21/DataStructureTutorial/blob/70fb22606883b0c9369970563621231d7b075701/UnbalancedBSTEx.png "Unbalanced BST")
   <img src="https://github.com/TechMan21/DataStructureTutorial/blob/39cc9964bcbb17e38f59a6202b8674545dbac090/BYUI-unbalanced_bst.jpeg" alt="BYUI BST" width="300" height="300"/>

   <sup>Right Image sourced from BYU-Idaho CSE212: W09 Reading</sup>

   


- ### **Balanced Binary Search Trees**
   A balanced BST, also known as a height-balanced BST or simply a balanced tree, is a binary search tree in which the height of the left and right subtrees of any node differs by at most one. Examples of balanced BSTs include AVL trees, red-black trees, and B-trees. These balanced tree structures ensure that operations like search, insertion, and deletion have optimal time complexity, typically O(log n), where n is the number of nodes in the tree.

   Balanced BSTs are crucial for maintaining efficient performance in applications that involve frequent data manipulation operations, as they prevent the tree from becoming overly skewed and maintain a more uniform distribution of nodes.

- #### Live BST Example:
  ![Live gif showing how a BST works](https://github.com/TechMan21/DataStructureTutorial/blob/70fb22606883b0c9369970563621231d7b075701/Binary_search_tree_example.gif "Live BST")

## Big O Notation
   For binary search trees (BSTs), the time complexity of operations such as search, insertion, and deletion depends on the tree's height. In a balanced BST, the height of the tree is typically logarithmic in relation to the number of nodes (i.e., O(log n)), where n is the number of nodes in the tree. This means that these operations have efficient time complexities even as the size of the tree grows.

   However, in unbalanced BSTs, the height of the tree can degrade to linear in the worst case (i.e., O(n)), leading to inefficient operations. This occurs when nodes are added in a sorted order, resulting in a tree with a structure similar to a linked list. In such cases, operations like search, insertion, and deletion take linear time, which can be undesirable for large datasets.

   Balanced BSTs, on the other hand, ensure that the height of the tree remains logarithmic even as nodes are added or removed. This optimal height balancing results in efficient operations with time complexities of O(log n).


## **Example Code**
Here's an example code of the redo and undo function:

```python
class TreeNode:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None

class BinarySearchTree:
    def __init__(self):
        self.root = None

    def insert(self, key):
        self.root = self._insert(self.root, key)

    def _insert(self, root, key):
        if root is None:
            return TreeNode(key)
        if key < root.key:
            root.left = self._insert(root.left, key)
        elif key > root.key:
            root.right = self._insert(root.right, key)
        return root

    def search(self, key):
        return self._search(self.root, key)

    def _search(self, root, key):
        if root is None or root.key == key:
            return root
        if key < root.key:
            return self._search(root.left, key)
        return self._search(root.right, key)

    def inorder_traversal(self):
        return self._inorder_traversal(self.root)

    def _inorder_traversal(self, root):
        result = []
        if root:
            result += self._inorder_traversal(root.left)
            result.append(root.key)
            result += self._inorder_traversal(root.right)
        return result

# Example usage:
bst = BinarySearchTree()
bst.insert(5)
bst.insert(3)
bst.insert(7)
bst.insert(1)
bst.insert(4)

print("Inorder Traversal:", bst.inorder_traversal())
print("Search for key 3:", bst.search(3))
print("Search for key 6:", bst.search(6))
```


## **Try-It-Out**

**Implement Deletion in Binary Search Tree**

**Objective**: Implement a method to delete a node from a Binary Search Tree (BST).

**Instructions:**
Use the provided example code for the Binary Search Tree (BST) implementation as a reference.
Implement a delete method in the BinarySearchTree class that removes a given key from the BST while maintaining its binary search tree property.
Test your implementation with various test cases to ensure correctness and handle edge cases appropriately.

**Expected Output:**
After implementing the delete method, you should be able to delete nodes from the BST and verify that the tree remains a valid BST after deletion.

**Optional:** If you're feeling up for a challenge, you can also implement additional features such as:
- Handling deletion of nodes with two children.
- Implementing deletion with iterative traversal instead of recursive traversal.
- Adding additional methods to the BinarySearchTree class for other operations like    finding the minimum or maximum element in the tree.


**Once you have completed the task you can view the [solution](6-treeSolution.md) to check for accuracy and completeness.**

Back to [Welcome Page](0-welcome.md)