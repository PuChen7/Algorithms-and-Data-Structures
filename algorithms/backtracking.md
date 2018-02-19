# Backtracking

## Definition
Backtracking is a general algorithm for finding all (or some) solutions to some computational problem, that incrementally builds candidates to the solutions, and abandons each partial candidate c ("backtracks") as soon as it determines that c cannot possibly be completed to a valid solution.

In each step, check if it satisfies all constraints. If it does, then continue. If it doesn't, then step backward to check another path. (The difference between Brute-Force and Backtracking)

## Core Pattern
The standard Backtracking code has the following pattern:

```Java
void backtracking(int[] arr, int boundary, int current, int[] result)
{
    if(current>=boundary) // terminate point
    {
        // check if result is the final answer
        // if yes -> terminate
        
        return;
    } 

    for(int i=0; i<arr.length;i++)
    {
        STEP 1： // extract the ith element in the array
        STEP 2： // add the ith element into the result
        STEP 3： backtracking(arr, boundary, current+1, result); // go deeper
        STEP 4： // take out the ith element from result
        STEP 5： // put back the ith element to array
    }     
}    
```

## When to use backtracking

* Find a path to success

* Find all paths to success

* Find the best path to success

This procedure is repeated over and over until you reach a final state. If you made a good sequence of choices, your final state is a goal state; if you didn't, it isn't.

## Related Problems

* [Combination Sum](combination-sum.md)

* [Combination Sum II](combination-sum2.md)

* [Subsets](subsets.md)

* [Subsets II](subsets2.md)

* [Permutations](permutations.md)

* [Permutations II](permutations2.md)

* [Palindrome Partitioning](palindrome-partitioning.md)


