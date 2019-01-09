# Counting Sort
Counting sort is a sorting technique based on keys between a specific range. It works by counting the number of objects having 
distinct key values (kind of hashing). Then doing some arithmetic to calculate the position of each object in the output sequence.

```java
 public static void main(String[] args){
    // input array. for each value <= arr.length
    int[] input = {1,5,1,3,4,5,0};

    // modified array with length == arr.length
    int[] modified = new int[256];
    for (int i = 0; i < modified.length; i++) modified[i] = 0;

    // get count
    for (int i = 0; i < input.length; i++)
        modified[input[i]] += 1;

    // modify by adding the previous sum
    for (int i = 1; i < modified.length; i++)
        modified[i] += modified[i-1];
        
    // output array
    int[] res = new int[input.length];

    for (int i = 0; i < input.length; i++){
        int val = input[i];	// get the original value
        int modVal = modified[val];	// make val as index for modified array
        res[modVal-1] = val;	// put the val at index modVal
        modified[val] = modified[val] - 1;
    }
}
```

## Complexity
O(n)
