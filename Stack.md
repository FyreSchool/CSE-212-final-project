# Stacks

Imagine you have a pile of plates stacked one on top of the other. If you want to take a plate to use, you take the one on the top. If you want to put a plate back, you place it on the top of the stack.

In C#, a stack works the same way. It's a way to store things where you can only add or take things from the top. When you add something, it's called "pushing," and when you take something, it's called "popping." You always `push` or `pop` from the top, just like with the plates.

Stack is a collection that stores elements in a Last-In-First-Out (LIFO). Like was said above we can't access an item in the stack that is not on the top of the stack. For example if we wanted to grab a plate that fourth from the top we would first have to remove all three plates that were above it one at a time to reach that plate. 

# Stack Operations

There are many ways that we can interact with stacks. That may involve either altering a stack or just check on the status of it. Lets go over the most common operations that we can use with stacks. 

### Push
`Push` is one of the most common of the stack operations. It is used to add an element to the top of a stack. 

``` csharp
stack.Push("Element");
```
This would add the word Element to the top of our stack.

### Pop
`Pop` is another common stack opperation that is used to remove the top element off a stack. If a stack is empty and we called the `pop` operation then we would recieve an error. 
``` csharp
object topElement = stack.Pop();
```
This code pops the top element of our stack. 

### Peek
`Peek` is an operation that we can use with stack to return the top element of a stack without popping it. 
``` csharp
object topElement = stack.Peek();
```
This code returns the top element of our stack but leaves the element untouched on our stack.

### Count
The `count` operation returns the number of elements that are currently in our stack.
``` csharp
int count = stack.Count;
```
This code sets the variable count equal to the number of elements that are in our list

### Clear
The `Clear` operation removes all the elements in our stack that we are working with.
``` csharp
stack.Clear();
```
This code just cleared our stack so it is now empty.

### Contains
We also have the `contains` operation. `Contains` will check to see if there is a certian element withen the stack that we are working with. 
``` csharp
bool contains = stack.Contains("Element");
```
This code checked to see if there was a string in the stack called element. We also need to make sure when using the `contains` operation that the stack is not empty or we will get an error. 

# Implementation of Stacks
A stack is a collection of elements with two main principal operations:

1. **Push**: Adds an element to the collection.
2. **Pop**: Removes the most recently added element that was not yet removed.

Stacks follow the Last In First Out (LIFO) principle.

## Implementation of a Stack in C#

In C#, the `Stack` class is provided in the `System.Collections.Generic` namespace. Below is an example of how to implement and use a stack in C#:

### Example

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Creating a stack
        Stack<int> stack = new Stack<int>();

        // Pushing elements onto the stack
        // Adding 1, 2, and 3 to the stack
        stack.Push(1);
        stack.Push(2);
        stack.Push(3);

        // Displaying the elements in the stack
        // Displays 1, 2, 3
        Console.WriteLine("Stack elements:");
        foreach (int item in stack)
        {
            Console.WriteLine(item);
        }

        // Popping elements from the stack
        // Pops 3 off the top
        Console.WriteLine("\nPopped element: " + stack.Pop());

        // Peeking at the top element of the stack
        // Top element is now 2
        Console.WriteLine("Top element: " + stack.Peek());

        // Displaying the remaining elements in the stack
        // Displays 1, 2 
        Console.WriteLine("\nStack elements after pop:");
        foreach (int item in stack)
        {
            Console.WriteLine(item);
        }
    }
}
```
# Applications of Stacks
Stacks are a fundamental data structure that find applications in various areas of computer science and software development. Due to their Last In First Out (LIFO) nature, stacks are particularly useful in scenarios where a reversible, order-dependent process is required. Below are some key applications of stacks:

## Applications of Stacks

### 1. **Expression Evaluation and Syntax Parsing**

Stacks are widely used in evaluating arithmetic expressions, especially in converting expressions from infix to postfix notation and vice versa. They are also used in the parsing of syntax in compilers and interpreters.

- **Infix to Postfix Conversion**: Using the Shunting Yard algorithm, stacks can convert infix expressions (e.g., `A + B`) to postfix expressions (e.g., `AB+`).
- **Expression Evaluation**: Postfix expressions can be easily evaluated using stacks.

### 2. **Backtracking Algorithms**

Stacks are employed in algorithms that require backtracking, such as depth-first search (DFS) in graph traversal, solving puzzles (e.g., mazes, Sudoku), and more.

- **DFS in Graphs**: Stacks are used to keep track of vertices to be explored.
- **Maze Solving**: Stacks help in storing the path taken and backtracking when a dead end is encountered.

### 3. **Function Call Management**

In many programming languages, the call stack is used to manage function calls. Each function call is pushed onto the stack, and the return address and local variables are stored until the function completes and control is returned to the caller.

- **Recursion**: Stacks are inherently used to manage recursive function calls.
- **Call Stack**: Keeps track of active functions and their states.

### 4. **Undo Mechanisms in Software**

Stacks are used to implement undo functionality in various applications like text editors, drawing applications, etc. Each action is pushed onto a stack, and an undo operation pops the last action to revert it.

- **Text Editors**: Track changes to allow users to undo/redo actions.
- **Drawing Applications**: Store actions like drawing, erasing, etc., to undo the last action.

### 5. **Syntax Parsing and Expression Matching**

Stacks are used to match parentheses and other delimiters in expressions. They help in checking for balanced parentheses and other nested structures.

- **Parentheses Matching**: Check if all opening parentheses have corresponding closing parentheses.
- **HTML/XML Tag Matching**: Ensure that tags are properly opened and closed.

### 6. **Implementing Algorithms**

Stacks are crucial in implementing various algorithms, such as the Tower of Hanoi, where the recursive solution inherently uses a stack-based approach to move disks.

- **Tower of Hanoi**: Solve the puzzle using recursive function calls managed by stacks.
- **Sorting Algorithms**: Implement non-recursive versions of algorithms like quicksort using stacks.

# Efficiency of common operations

In C#, the `Stack` class provides several operations. Understanding their efficiency is crucial for writing optimized code. Below, we discuss the efficiency of six common stack operations: `Push`, `Pop`, `Clear`, `Contains`, `Count`, and `Peek`.

### Push
- **Operation:** Adds an element to the top of the stack.
- **Efficiency:** O(1)
- **Explanation:** The push operation involves adding an element to the end of an internal array or linked list, which is a constant time operation.

### Pop
- **Operation:** Removes the top element from the stack.
- **Efficiency:** O(1)
- **Explanation:** The pop operation removes the last element from the internal array or linked list, which can be done in constant time.

### Clear
- **Operation:** Removes all elements from the stack.
- **Efficiency:** O(n)
- **Explanation:** The clear operation involves setting the count of elements to zero and possibly deallocating the internal array. It requires iterating over all elements if they need to be explicitly removed or deallocated.

### Contains
- **Operation:** Determines whether an element is in the stack.
- **Efficiency:** O(n)
- **Explanation:** The contains operation requires a linear search through the internal array or linked list to check if the element exists, which takes linear time.

### Count
- **Operation:** Gets the number of elements in the stack.
- **Efficiency:** O(1)
- **Explanation:** The count operation simply returns the current count of elements, which is stored as a property of the stack and can be accessed in constant time.

### Peek
- **Operation:** Returns the top element of the stack without removing it.
- **Efficiency:** O(1)
- **Explanation:** The peek operation accesses the last element of the internal array or linked list, which can be done in constant time.

Here's a summary table of the efficiencies:

| Operation | Efficiency |
|-----------|------------|
| Push      | O(1)       |
| Pop       | O(1)       |
| Clear     | O(n)       |
| Contains  | O(n)       |
| Count     | O(1)       |
| Peek      | O(1)       |



# Example Problem
### Parentheses Matching
Lets say that we wanted to build a program that checks to see if an expression has both an opening and closeing parathesis around it. Here is a simple C# code example that demonstrates the use of a stack to check for balanced parentheses in an expression:

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static bool AreParenthesesBalanced(string expression)
    {
        Stack<char> stack = new Stack<char>();

        foreach (char ch in expression)
        {
            if (ch == '(')
            {
                stack.Push(ch);
            }
            else if (ch == ')')
            {
                if (stack.Count == 0)
                {
                    return false;
                }
                stack.Pop();
            }
        }

        return stack.Count == 0;
    }

    static void Main()
    {
        string expression = "(1 + (2 * 3) + (4 / 2))";
        bool isBalanced = AreParenthesesBalanced(expression);

        Console.WriteLine("The expression has balanced parentheses: " + isBalanced);
    }
}
```
# Problem to Solve
### Next Greater Element


Given an array of integers, find the next greater element for each element in the array. The next greater element for an element `x` is the first greater element on the right side of `x` in the array. If there is no greater element, then the next greater element for `x` is -1.

### Example Input and Output
- **Input:** `[4, 5, 2, 10]`
- **Output:** `[5, 10, 10, -1]`

- **Input:** `[3, 2, 1]`
- **Output:** `[-1, -1, -1]`


### Solution
* [Solution](StackSolution.md)



