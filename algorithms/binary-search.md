# Binary Search

## Synopsis
Search a sorted array by repeatedly dividing the search interval in half.
Begin with an interval covering the whole array. 
If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. 
Otherwise narrow it to the upper half. 
Repeatedly check until the value is found or the interval is empty.

## while loop version
```java
public int binarySearch(int lo, int hi, int[] nums, int target){
    while (lo <= hi){
        int mid = lo + (hi - lo)/2; // prevent overflow
        if (nums[mid] == target)
            return nums[mid];
        else if (nums[mid] < target)
            lo = mid + 1;
        else
            hi = mid - 1;
    }
    // target was not found
    return -1;
}
```

## recursion version
```java
public int binarySearch(int lo, int hi, int[] nums, int target){
    if (lo <= hi){
        int mid = lo + (hi-lo)/2;
        if (nums[mid] == target)
            return target;
        else if (nums[mid] < target)
            return binarySearch(mid+1, hi, nums, target);
        else
            return binarySearch(lo, mid-1, nums, target);
    }
    // target wad not found
    return -1;
}
```