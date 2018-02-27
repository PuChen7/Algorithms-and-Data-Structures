# Binary Search

## Synopsis
earch a sorted array by repeatedly dividing the search interval in half.
Begin with an interval covering the whole array. 
If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. 
Otherwise narrow it to the upper half. 
Repeatedly check until the value is found or the interval is empty.

## Code - Recursively solve
```java

public int binarySearch(int lo, int hi, int[] nums, int target){
    int mid = lo + (hi - lo)/2; // prevent overflow
}
```