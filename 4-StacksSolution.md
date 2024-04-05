```python 
class TextEditor:
    def __init__(self):
        self.content = ""
        self.operations = []
    
    def insert(self, text):
        self.content += text
        self.operations.append(('insert', text))
    
    def delete(self, length):
        deleted_text = self.content[-length:]
        self.content = self.content[:-length]
        self.operations.append(('delete', deleted_text))
    
    def undo(self):
        if not self.operations:
            return
        last_operation = self.operations.pop()
        operation, data = last_operation
        if operation == 'insert':
            self.content = self.content[:-len(data)]
        elif operation == 'delete':
            self.content += data
    
    def reverse_last_operations(self, n):
        for _ in range(n):
            self.undo()

    def display(self):
        print(self.content)

# Example Usage
#YOUR WORDS DO NOT HAVE TO MATCH AS LONG AS IT WORKS CORRECTLY
editor = TextEditor()
editor.insert("The quick brown fox ")
editor.insert("jumps over the lazy dog.")
editor.display()  # Output: The quick brown fox jumps over the lazy dog.
editor.delete(9)  # Deleting 'lazy dog.'
editor.display()  # Output: The quick brown fox jumps over the 
editor.insert("leaps over the sleeping cat.")
editor.display()  # Output: The quick brown fox leaps over the sleeping cat.

# Undo the last three operations: delete 'leaps over the sleeping cat.', 
# insert 'leaps over the sleeping cat.', and delete 'lazy dog.'
editor.reverse_last_operations(3)
editor.display()  # Output: The quick brown fox jumps over the lazy dog.
```

Back to [Stacks](1-stacks.md) page

OR

Back to [Welcome Page](0-welcome.md)