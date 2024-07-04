# Sets

Imagine you have a box of crayons. Each crayon has a unique color. Now, this box of crayons is like a `set` in C#. In a `set`, just like in our box of crayons, each item is unique. If you try to put another crayon of the same color into the box, it won’t work because that color is already there.  

We can solve a lot of problems that we might come across in our daily lives with `sets`. Let’s say you are making a list of people that you want to invite to a party. After you are finished with your list you ask your friend if they have people that they want to invite to the party. You add the people that your friend says to the list. What happens if your friend says the name of someone that you already had on our list. You’re not going to add them twice to the list but just keep the name on from the first time that you added it.
 
This is exactly how `sets` can be helpful in this situation. When you add your friend's suggestions to your initial guest list, the `set` will automatically prevent duplicate entries. It checks if the name your friend suggests already exists in the `set` (like checking if the color crayon is already in the box). If it is, the set simply ignores the duplicate and moves on to the next suggestion. This ensures you have a final guest list with unique invitees, avoiding accidental double invites and saving you the hassle of keeping track of who's already on the list. 


# Set Operations

There are a lot of ways that we can interact with a `sets` in C#. Some will interact with the set and change it while other operations will just look at the set and report its findings.
Here are some of the common operations that we can use to interact with `sets`.

### Add
The `Add` operation will add an element to a set if that element is not already in the `set`.
``` csharp
set.Add(1);
```
This code added 1 to our `set`.

### Remove
The `Remove` operation will simply remove an element from our `set`.
``` csharp
set.Remove(1);
```
This code removed the number 1 from our `set`.

### Contains
The `Contains` operations job is to check to see if a `set` contains a specified element.
``` csharp
bool contains = set.Contains(1);
```
This code checked to see if our `set` contained the number 1.

### Count
The `Count` operation counts the number of elements that are in our `set`.
``` csharp
int count = set.Count;
```
This code counted the elements that were in our `set`.

### UnionWith
the `UnionWith` modifies the current set to contain all elements that are present in itself, the specified collection, or both.
``` csharp 
HashSet<int> otherSet = new HashSet<int> { 2, 3, 4 };
set.UnionWith(otherSet);
```
This code added 2, 3, and 4 to our current `set`.

### IntersectWith
The `IntersectWith` modifies the current set to contain only elements that are present in both the current set and the specified collection.
``` csharp
set.IntersectWith(otherSet);
```
This code adds only elements that are in both `sets` into our current `set`.

### ExpectWith
The `ExcepthWith` Modifies the current set to contain only elements that are present in the current set but not in the specified collection.
```csharp
set.ExceptWith(otherSet);
```
This code made it so that only elements in the the current and not in the specified `set` were added.

### Clear
The `Clear` operation removes all elements from the set.
``` csharp
set.Clear();
```
This code cleared our set.

# Implementations of Sets

In C#, a set is a collection of unique elements. The HashSet<T> class in the System.Collections.Generic namespace provides high-performance set operations. This class implements the ISet<T> interface, which provides methods for set operations like union, intersection, and difference.

### Creating a Set
To create a set, you simply instantiate a HashSet<T> object. Here, T represents the type of elements in the set.

### Basic Operations
* Add: Adds an element to the set.
* Remove: Removes an element from the set.
* Contains: Checks if an element is in the set.
* UnionWith: Modifies the set to contain all elements that are in either the current set or the specified collection.
* IntersectWith: Modifies the set to contain only elements that are present in both the current set and the specified collection.
* ExceptWith: Removes all elements in the specified collection from the current set.
### Example
Below is a simple example demonstrating the creation and basic operations of a set in C#:

``` csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Create a new set
        HashSet<int> numbers = new HashSet<int>();

        // Add elements to the set
        numbers.Add(1);
        numbers.Add(2);
        numbers.Add(3);

        // Attempt to add a duplicate element
        bool added = numbers.Add(3); // returns false, 3 is already in the set

        // Remove an element
        numbers.Remove(2);

        // Check if an element is in the set
        bool contains = numbers.Contains(1); // returns true

        // Display the elements in the set
        Console.WriteLine("Elements in the set:");
        foreach (int number in numbers)
        {
            Console.WriteLine(number);
        }

        // Create another set
        HashSet<int> otherNumbers = new HashSet<int> { 3, 4, 5 };

        // Union the sets
        numbers.UnionWith(otherNumbers);

        // Display the elements after union
        Console.WriteLine("Elements after union:");
        foreach (int number in numbers)
        {
            Console.WriteLine(number);
        }

        // Intersect the sets
        numbers.IntersectWith(otherNumbers);

        // Display the elements after intersection
        Console.WriteLine("Elements after intersection:");
        foreach (int number in numbers)
        {
            Console.WriteLine(number);
        }

        // Except the sets
        numbers.ExceptWith(new HashSet<int> { 3 });

        // Display the elements after except
        Console.WriteLine("Elements after except:");
        foreach (int number in numbers)
        {
            Console.WriteLine(number);
        }
    }
}
```