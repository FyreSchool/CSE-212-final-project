# Code Solution
This is the code solution for the problem to solve in the stacks
```csharp
using System;
using System.Collections.Generic;

public class Solution {
    public int[] NextGreaterElements(int[] nums) {
        int[] result = new int[nums.Length];
        Stack<int> stack = new Stack<int>();

        for (int i = nums.Length - 1; i >= 0; i--) {
            while (stack.Count > 0 && stack.Peek() <= nums[i]) {
                stack.Pop();
            }
            result[i] = stack.Count == 0 ? -1 : stack.Peek();
            stack.Push(nums[i]);
        }

        return result;
    }
}

class Program
{
    static void Main()
    {
        Solution solution = new Solution();

        // Test cases
        int[][] testCases = {
            new int[] {4, 5, 2, 10},
            new int[] {3, 2, 1},
            new int[] {1, 3, 2, 4}
        };

        foreach (var testCase in testCases) {
            int[] result = solution.NextGreaterElements(testCase);
            Console.WriteLine($"Next greater elements for [{string.Join(", ", testCase)}]: [{string.Join(", ", result)}]");
        }
    }
}

```
### Explanation
The problem takes advantage of the stack's LIFO nature. Iterate through the array from right to left. For each element, pop elements from the stack until you find an element greater than the current element or the stack is empty. The next greater element is the element on the top of the stack after the popping. If the stack is empty, it means there is no greater element on the right side, and the result is -1.
