# Stacks

Stacks are used all the time, especially when using documents! Without the programming structure of stacks you wouldnt be able to undo a mistake, put back accidentlly deleted information, restore a photo or document back to its original state after a change, and so on.


**What is a stack?** 

A Stack is a linear data structure that operates on a Last In, First Out principle. Things that are last added are at the top of the stack. You can only get to items lower in the stack if you remove what is on top first. Therefore the last in is first to come out or off.  

 ![ IMage showing Layers seperated with highlighted top layer](https://github.com/TechMan21/DataStructureTutorial/blob/c7608369f26e717da142435bfe4e9dde277e52ff/LIFO-CSE212.png "Layers colored- Stack Example")

## Undo Option & Stacking

This data structure gives us the ability to "Undo" on copmuter programs. It is a common functionality on software applications like grpahic design tools, text editors, word processors, and more. A user can manage state changes or actions which the user themselves have performed.

Software applications will save the users action (like type a word) and make it into an object, then push it to a "undo" stack. When a user clicks the undo button (or uses the shortcut Crtl + Z) for an undo request the application "pops" the last action /top object off of the stack. 


![ IMage showing Layers seperated with highlighted top layer](https://upload.wikimedia.org/wikipedia/commons/9/93/Stack-sv.svg "Layers colored- Stack Example")

Most applications also have a "Redo" button (or keyboard shortcut of Ctrl + Y). When Undo is performed, the action/object is not thrown away but added to another stack. If a user chooses Redo, then the application pops the action off the the redo stack and applies it back to the record/document and added to the undo stack. 

## Software & Function

In Software the call stack is a stack data structure used by programming languages to keep track of active subroutines (functions or methods) in a program. When a function is called, its return address and sometimes its parameters are "pushed" onto the call stack. When the function returns, its frame is "popped" from the stack. This ensures that execution returns to the correct location and that the function's local variables are managed correctly.
In coding, a debugger uses the call stack.

![Image showing Call Stack Example from VS Code Screenshot](https://github.com/TechMan21/DataStructureTutorial/blob/c7608369f26e717da142435bfe4e9dde277e52ff/PythonCallStackExample.png "Call Stack Example from VS Code")


In application, like web-browsers, stacking helps with page navigation (back and forward arrow). It saves a history of web pages as each new link or page is opened. 

## Example Code
Here's an example code of the redo and undo function:

```python
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        if not self.is_empty():
            return self.items.pop()
        else:
            return None

    def is_empty(self):
        return len(self.items) == 0

    def peek(self):
        if not self.is_empty():
            return self.items[-1]
        else:
            return None

class TextEditor:
    def __init__(self):
        self.text = ""
        self.undo_stack = Stack()
        self.redo_stack = Stack()

    def insert_text(self, text):
        self.undo_stack.push(self.text)
        self.text += text

    def delete_last_character(self):
        if len(self.text) > 0:
            self.undo_stack.push(self.text)
            self.text = self.text[:-1]

    def undo(self):
        if not self.undo_stack.is_empty():
            self.redo_stack.push(self.text)
            self.text = self.undo_stack.pop()

    def redo(self):
        if not self.redo_stack.is_empty():
            self.undo_stack.push(self.text)
            self.text = self.redo_stack.pop()

    
#Example Use:
editor = TextEditor()
editor.insert_text("Hello, ")
print(editor.text)  # Output should be: Hello, 
editor.insert_text("world!")
print(editor.text)  # Output should be: Hello, world!
editor.delete_last_character()
print(editor.text)  # Output should be: Hello, world
editor.undo()
print(editor.text)  # Output should be: Hello, world!
editor.undo()
print(editor.text)  # Output should be: Hello, 
editor.redo()
print(editor.text)  # Output should be: Hello, world!
```

## Try-It-Out

Your text editor application, built around a stack structure for undo and redo functionality, has become quite popular. Users love the simplicity and effectiveness of the undo and redo features. However, several users have requested a feature that allows them to reverse the effects of the last N operations in one go, where N can be any number. This feature should be able to reverse a combination of text insertions, deletions, and even previous undos and redos.

Task
Your task is to extend the TextEditor class with a new method called reverse_last_operations(n), which reverses the effects of the last N operations. This method should consider text insertions and deletions as operations. Undoing or redoing an action counts as an operation as well.

Requirements
- Implement the reverse_last_operations(n) Method: This method should reverse the last N operations performed by the user. If N is greater than the number of operations performed, reverse all the operations.

- Update Undo and Redo Stacks Appropriately: Ensure that after reversing the last N operations, the undo and redo functionality still works correctly for future operations.

- Maintain Text Integrity: The method should not introduce any text errors or inconsistencies. After reversing operations, the text editor should reflect the exact state it would be in if those operations had never been performed in the first place.

- Edge Cases: Consider edge cases such as trying to reverse more operations than have been performed or calling the reverse operation on an empty undo stack.

Suggested Test Cases
- Insert text, delete text, and then reverse the last 2 operations to see if the editor - returns to the initial state.

- Perform a series of undos and redos, then reverse a subset of those operations.

- Attempt to reverse more operations than have been performed to test edge case handling.

Feel free to examine the example code to help you in your task.

**Once you have completed the task you can view the [solution](4-StacksSolution.md) to check for correctness.**

Back to [Welcome Page](0-welcome.md)