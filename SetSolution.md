# Code Solution
We'll use the HashSet<T> class to solve this problem efficiently. The approach involves:

Adding all elements from the first array to a set.
Iterating through the second array and checking if each element is in the set created from the first array.
Using another set to store and ensure the uniqueness of common elements.
Here is the C# code that implements this solution:

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static HashSet<int> FindCommonElements(int[] array1, int[] array2)
    {
        HashSet<int> set1 = new HashSet<int>(array1);
        HashSet<int> commonElements = new HashSet<int>();

        foreach (int element in array2)
        {
            if (set1.Contains(element))
            {
                commonElements.Add(element);
            }
        }

        return commonElements;
    }

    static void Main()
    {
        int[] array1 = { 4, 5, 2, 10 };
        int[] array2 = { 5, 10, 10, -1 };

        HashSet<int> commonElements = FindCommonElements(array1, array2);

        Console.WriteLine("Common elements between the two arrays:");
        if (commonElements.Count > 0)
        {
            foreach (int element in commonElements)
            {
                Console.WriteLine(element);
            }
        }
        else
        {
            Console.WriteLine("(No common elements)");
        }
    }
}
```
### Explanation
Creating the First Set: We initialize a HashSet<int> with the elements of array1. This ensures that all elements from array1 are stored uniquely.

Finding Common Elements: We then iterate through array2. For each element in array2, we check if it exists in the set created from array1. If it does, we add it to the commonElements set.

Printing Common Elements: Finally, we print the elements in the commonElements set, which contains all unique elements found in both arrays.

This solution is efficient because the average time complexity for Add and Contains operations in a HashSet is O(1). Thus, the overall time complexity of this solution is O(n + m), where n is the number of elements in array1 and m is the number of elements in array2.