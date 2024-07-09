# Code Solution

This is the code solution for the problem to solve in the trees tutorial

```csharp
Copy code
using System;

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

    public TreeNode FindLCA(TreeNode root, int n1, int n2)
    {
        if (root == null) return null;

        if (root.Value == n1 || root.Value == n2)
            return root;

        TreeNode leftLCA = FindLCA(root.Left, n1, n2);
        TreeNode rightLCA = FindLCA(root.Right, n1, n2);

        if (leftLCA != null && rightLCA != null) return root;

        return leftLCA != null ? leftLCA : rightLCA;
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

        TreeNode lca = tree.FindLCA(tree.Root, 3, 7);
        Console.WriteLine("Lowest Common Ancestor of 3 and 7: " + (lca != null ? lca.Value.ToString() : "Not found"));
    }
}
```

# Explanation 

To solve the problem of performing different tree traversals on a binary tree, we first need to understand the structure of the binary tree and its nodes. A binary tree is composed of nodes, each containing a value and pointers to its left and right children. The root node is the starting point, and all other nodes descend from it. We implement this structure in C# using classes for the tree and its nodes, where each node contains its value and references to its left and right children. This foundational setup allows us to build and manipulate the binary tree effectively.

In the insertion process, we ensure that the binary search tree properties are maintained. This means that for any given node, the left child must have a smaller value, and the right child must have a larger value. We achieve this by recursively comparing the value to be inserted with the current node's value, deciding whether to move left or right until we find the appropriate position. This method guarantees that the tree remains ordered, facilitating efficient searches and other operations.

Tree traversal methods are crucial for accessing and processing the data stored in the tree nodes. The in-order traversal visits nodes in ascending order by exploring the left subtree, visiting the root, and then the right subtree. This traversal is particularly useful for binary search trees as it produces a sorted sequence of values. Pre-order traversal, on the other hand, starts with the root, then the left subtree, and finally the right subtree, which is beneficial for creating a copy of the tree or for prefix notation evaluations. Post-order traversal visits the left subtree, then the right subtree, and finally the root, making it suitable for tasks like deleting the tree or evaluating postfix expressions.

The solution to the problem involves implementing these traversal methods and applying them to a given binary tree. By inserting nodes in a specific order and performing in-order, pre-order, and post-order traversals, we can observe the different sequences in which the nodes are visited. For example, given the input binary tree with elements [10, 5, 15, 3, 7, 12, 17], the in-order traversal would output the values in ascending order, the pre-order traversal would start with the root and proceed through the left and right subtrees, and the post-order traversal would visit all children before the root. This approach demonstrates the utility and versatility of different tree traversal methods in various computational tasks.