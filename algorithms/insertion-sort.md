# Insertion Sort


```java
public class InsertionSort {
    public static void main(String[] args) {
	int[] input = {5,3,7,9,12,1,0,4,25,99};
	
	for (int i = 1; i < input.length; i++){
	    int currVal = input[i];
	    int j = i - 1;
	    while (j >= 0 && input[j] > currVal){
		input[j+1] = input[j];
		j = j - 1; // go to previous
	    }
	    input[j+1] = currVal;	// update value at the right position
	}
    }
}
```

## Complexity
Time Complexity: `O(n*2)`

Space Complexity: `O(1)` --> in-place

Boundary Cases: Insertion sort takes maximum time to sort if elements are sorted in `reverse order`. 
And it takes minimum time (Order of n) when elements are `already sorted`.
