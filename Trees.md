# Trees

A tree is a hierarchical data structure consisting of nodes, with a single node serving as the root of the tree. Each node contains a value and references to its child nodes. Trees are commonly used in various applications due to their efficiency in organizing and accessing data.

In C#, trees can be implemented in several ways, with the binary tree being one of the most fundamental types.

Binary Trees
A binary tree is a type of tree where each node has at most two children, referred to as the left child and the right child. Binary trees are widely used due to their simplicity and efficiency in operations like searching, inserting, and deleting elements.

# Tree Terminology
Understanding trees requires familiarity with specific terminology:

- **Node**: The basic unit of a tree, containing data and references to its children.
- **Root**: The top node in a tree, where all operations begin.
- **Edge**: The connection between two nodes.
- **Leaf**: A node with no children.
- **Parent**: A node that has one or more children.
- **Child**: A node directly connected to another node when moving away from the root.
- **Subtree**: A tree consisting of a node and its descendants.
- **Depth**: The number of edges from the root to a node.
- **Height**: The number of edges on the longest path from a node to a leaf.

# Types of Trees
### Binary Tree
A binary tree is a type of tree where each node has at most two children, referred to as the left child and the right child.

### Binary Search Tree (BST)
A BST is a binary tree where the left child of a node contains values less than the parent node, and the right child contains values greater than the parent node.

### AVL Tree
An AVL tree is a self-balancing binary search tree, where the heights of the two child subtrees of any node differ by at most one.

### Heap Tree
A heap is a special tree-based data structure that satisfies the heap property. In a max heap, for any given node, the value of the node is greater than or equal to the values of its children, and in a min heap, the value of the node is less than or equal to the values of its children.

### Trie
A trie, or prefix tree, is a type of search tree used to store a dynamic set of strings, where the keys are usually strings.

# Tree Traversal
Tree traversal refers to the process of visiting all the nodes in a tree in a specific order. Common traversal methods include:

### In-order Traversal
In-order traversal visits nodes in the following order: left subtree, root, right subtree.

### Pre-order Traversal
Pre-order traversal visits nodes in the following order: root, left subtree, right subtree.

### Post-order Traversal
Post-order traversal visits nodes in the following order: left subtree, right subtree, root.

### Level-order Traversal
Level-order traversal visits nodes level by level, starting from the root.

# Implementation of Tree Traversal in C#
```csharp

using System;
using System.Collections.Generic;

public class TreeNode
{
    public int Value;
    public TreeNode Left;
    public TreeNode Right;

    public TreeNode(int value)
    {
        Value = value;
        Left = null;
        Right = null;
    }
}

public class BinaryTree
{
    public TreeNode Root;

    public BinaryTree()
    {
        Root = null;
    }

    public void Insert(int value)
    {
        if (Root == null)
        {
            Root = new TreeNode(value);
        }
        else
        {
            InsertRec(Root, new TreeNode(value));
        }
    }

    private void InsertRec(TreeNode root, TreeNode newNode)
    {
        if (newNode.Value < root.Value)
        {
            if (root.Left == null)
            {
                root.Left = newNode;
            }
            else
            {
                InsertRec(root.Left, newNode);
            }
        }
        else
        {
            if (root.Right == null)
            {
                root.Right = newNode;
            }
            else
            {
                InsertRec(root.Right, newNode);
            }
        }
    }

    public void InOrderTraversal(TreeNode node)
    {
        if (node != null)
        {
            InOrderTraversal(node.Left);
            Console.Write(node.Value + " ");
            InOrderTraversal(node.Right);
        }
    }

    public void PreOrderTraversal(TreeNode node)
    {
        if (node != null)
        {
            Console.Write(node.Value + " ");
            PreOrderTraversal(node.Left);
            PreOrderTraversal(node.Right);
        }
    }

    public void PostOrderTraversal(TreeNode node)
    {
        if (node != null)
        {
            PostOrderTraversal(node.Left);
            PostOrderTraversal(node.Right);
            Console.Write(node.Value + " ");
        }
    }

    public void LevelOrderTraversal()
    {
        if (Root == null) return;

        Queue<TreeNode> queue = new Queue<TreeNode>();
        queue.Enqueue(Root);

        while (queue.Count > 0)
        {
            TreeNode node = queue.Dequeue();
            Console.Write(node.Value + " ");

            if (node.Left != null)
            {
                queue.Enqueue(node.Left);
            }

            if (node.Right != null)
            {
                queue.Enqueue(node.Right);
            }
        }
    }
}

class Program
{
    static void Main()
    {
        BinaryTree tree = new BinaryTree();

        tree.Insert(10);
        tree.Insert(5);
        tree.Insert(15);
        tree.Insert(3);
        tree.Insert(7);
        tree.Insert(12);
        tree.Insert(17);

        Console.WriteLine("In-order Traversal:");
        tree.InOrderTraversal(tree.Root);
        Console.WriteLine();

        Console.WriteLine("Pre-order Traversal:");
        tree.PreOrderTraversal(tree.Root);
        Console.WriteLine();

        Console.WriteLine("Post-order Traversal:");
        tree.PostOrderTraversal(tree.Root);
        Console.WriteLine();

        Console.WriteLine("Level-order Traversal:");
        tree.LevelOrderTraversal();
        Console.WriteLine();
    }
}
```
# Applications of Trees
### Binary Search Trees (BST)
BSTs are used to maintain a dynamic set of items, with fast insertion, deletion, and search operations.

### Heap Trees
Heaps are used in implementing priority queues and heap sort algorithms. They are efficient in finding the minimum or maximum element.

### Syntax Trees
Syntax trees are used in compilers to represent the structure of program code. They help in parsing and analyzing the source code.

### Trie
Tries are used in applications involving dynamic spell checking, auto-completion, and IP routing.

### File System
File systems use tree structures to represent the hierarchy of files and directories.

### Network Routing
Trees are used to model and optimize routing paths in networks.

# Efficiency of Common Operations

In C#, trees provide various operations, each with different time complexities depending on the type of tree and the specific operation. Below, we discuss the efficiency of common operations: Insertion, Deletion, Search, Traversal, Find Minimum, and Find Maximum for Binary Search Trees (BST).


### Insertion
- Operation: Adds an element to the tree.
- Efficiency: O(log n) on average, O(n) in the worst case.

Explanation: In a balanced BST, insertion requires traversing the tree from the root to the appropriate leaf position, which takes logarithmic time. However, in the worst case (e.g., a degenerate tree), insertion can take linear time.
###  Deletion
- Operation: Removes an element from the tree.
- Efficiency: O(log n) on average, O(n) in the worst case.

Explanation: Similar to insertion, deletion in a balanced BST involves traversing the tree and possibly restructuring it, taking logarithmic time on average. In the worst case, it can take linear time.
### Search
- Operation: Finds an element in the tree.
- Efficiency: O(log n) on average, O(n) in the worst case.

Explanation: Searching in a balanced BST involves traversing the tree from the root to a leaf, taking logarithmic time on average. In the worst case, it can take linear time.
### Traversal
- Operation: Visits all nodes in the tree.
- Efficiency: O(n)

Explanation: Traversal (in-order, pre-order, post-order, or level-order) visits each node exactly once, taking linear time.
### Find Minimum
- Operation: Finds the smallest element in the tree.
- Efficiency: O(log n) on average, O(n) in the worst case.
- Explanation: Finding the minimum involves traversing the leftmost path from the root, taking logarithmic time on average. In the worst case, it can take linear time.
### Find Maximum
- Operation: Finds the largest element in the tree.
- Efficiency: O(log n) on average, O(n) in the worst case.
- Explanation: Finding the maximum involves traversing the rightmost path from the root, taking logarithmic time on average. In the worst case, it can take linear time.

## Summary Table
Here’s a summary table of the efficiencies:

|Operation	  | BST (Average) | BST (Worst)	|
|-------------|---------------|-------------|
|Insertion	  | O(log n)	  |  O(n)	    |
|Deletion	  | O(log n)	  |  O(n)       |	
|Search	      | O(log n)	  |  O(n)	    |
|Traversal	  | O(n)	      |  O(n)	    |
|Find Minimum |	O(log n)	  |  O(n)	    |
|Find Maximum |	O(log n)	  |  O(n)	    |

# Example Problem
### Binary Tree Traversal
Let's solve a problem that requires us to perform different types of tree traversals on a binary tree. Implement a function that prints the in-order, pre-order, and post-order traversal of a given binary tree.

### Example Input and Output
- Input: Binary Tree with elements [10, 5, 15, 3, 7, 12, 17]
- Output:
    - In-order: [3, 5, 7, 10, 12, 15, 17]
    - Pre-order: [10, 5, 3, 7, 15, 12, 17]
    - Post-order: [3, 7, 5, 12, 17, 15, 10]

The provided C# code defines a binary tree and includes methods for inserting elements and performing in-order, pre-order, and post-order traversals. The Main method demonstrates creating a binary tree, inserting elements, and printing the traversals.

```csharp
using System;
using System.Collections.Generic;

class TreeNode
{
    public int Value;
    public TreeNode Left;
    public TreeNode Right;

    public TreeNode(int value)
    {
        Value = value;
        Left = null;
        Right = null;
    }
}

class BinaryTree
{
    public TreeNode Root;

    public BinaryTree()
    {
        Root = null;
    }

    public void Insert(int value)
    {
        Root = InsertRec(Root, value);
    }

    private TreeNode InsertRec(TreeNode root, int value)
    {
        if (root == null)
        {
            root = new TreeNode(value);
            return root;
        }

        if (value < root.Value)
        {
            root.Left = InsertRec(root.Left, value);
        }
        else if (value > root.Value)
        {
            root.Right = InsertRec(root.Right, value);
        }

        return root;
    }

    public void InOrderTraversal(TreeNode node)
    {
        if (node == null)
        {
            return;
        }

        InOrderTraversal(node.Left);
        Console.Write(node.Value + " ");
        InOrderTraversal(node.Right);
    }

    public void PreOrderTraversal(TreeNode node)
    {
        if (node == null)
        {
            return;
        }

        Console.Write(node.Value + " ");
        PreOrderTraversal(node.Left);
        PreOrderTraversal(node.Right);
    }

    public void PostOrderTraversal(TreeNode node)
    {
        if (node == null)
        {
            return;
        }

        PostOrderTraversal(node.Left);
        PostOrderTraversal(node.Right);
        Console.Write(node.Value + " ");
    }
}

class Program
{
    static void Main()
    {
        BinaryTree tree = new BinaryTree();

        tree.Insert(10);
        tree.Insert(5);
        tree.Insert(15);
        tree.Insert(3);
        tree.Insert(7);
        tree.Insert(12);
        tree.Insert(17);

        Console.WriteLine("In-order traversal:");
        tree.InOrderTraversal(tree.Root);
        Console.WriteLine();

        Console.WriteLine("Pre-order traversal:");
        tree.PreOrderTraversal(tree.Root);
        Console.WriteLine();

        Console.WriteLine("Post-order traversal:");
        tree.PostOrderTraversal(tree.Root);
        Console.WriteLine();
    }
}
```
# Problem to Solve
#### Lowest Common Ancestor (LCA)
Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree. The LCA is defined as the lowest node that has both nodes as descendants (where we allow a node to be a descendant of itself).

### Example Input and Output
- Input: Binary Tree with elements [10, 5, 15, 3, 7, 12, 17], and nodes 3 and 7
- Output: 5


### Solution
* [Solution](TreeSolution.md)
