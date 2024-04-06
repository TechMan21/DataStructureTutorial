

# BST Solution

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

    def delete(self, key):
        self.root = self._delete(self.root, key)

    def _delete(self, root, key):
        if root is None:
            return root

        if key < root.key:
            root.left = self._delete(root.left, key)
        elif key > root.key:
            root.right = self._delete(root.right, key)
        else:
            if root.left is None:
                return root.right
            elif root.right is None:
                return root.left

            # Node with two children: Get the inorder successor
            successor = self._min_value_node(root.right)

            # Copy the inorder successor's key to this node
            root.key = successor.key

            # Delete the inorder successor
            root.right = self._delete(root.right, successor.key)

        return root

    def _min_value_node(self, node):
        current = node
        while current.left is not None:
            current = current.left
        return current

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
bst.insert(6)
bst.insert(8)

print("Inorder Traversal before deletion:", bst.inorder_traversal())

bst.delete(3)
bst.delete(7)

print("Inorder Traversal after deletion:", bst.inorder_traversal())
```

## Full solution with all options included:

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

    def delete(self, key):
        self.root = self._delete(self.root, key)

    def _delete(self, root, key):
        if root is None:
            return root
        if key < root.key:
            root.left = self._delete(root.left, key)
        elif key > root.key:
            root.right = self._delete(root.right, key)
        else:
            if root.left is None:
                return root.right
            elif root.right is None:
                return root.left

            # Node with two children: Get the inorder successor (smallest in the right subtree)
            temp = self._min_value_node(root.right)

            # Copy the inorder successor's content to this node
            root.key = temp.key

            # Delete the inorder successor
            root.right = self._delete(root.right, temp.key)
        return root

    def _min_value_node(self, node):
        current = node
        while current.left is not None:
            current = current.left
        return current

    def inorder_traversal(self):
        return self._inorder_traversal(self.root)

    def _inorder_traversal(self, root):
        result = []
        if root:
            result.extend(self._inorder_traversal(root.left))
            result.append(root.key)
            result.extend(self._inorder_traversal(root.right))
        return result

# Example usage:
bst = BinarySearchTree()
bst.insert(5)
bst.insert(3)
bst.insert(7)
bst.insert(1)
bst.insert(4)
bst.insert(6)
bst.insert(8)

print("Inorder Traversal before deletion:", bst.inorder_traversal())

bst.delete(4)  # Trying to delete node with key 3
bst.delete(1)  # Trying to delete node with key 7

print("Inorder Traversal after deletion:", bst.inorder_traversal())

```
NOTE: Both solutions, with or without the optional exercises, will have the same output if you delete the same numbers. The optional exercises effect how the internal BST functions. 