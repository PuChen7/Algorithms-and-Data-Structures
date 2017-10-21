# Merge Sort
Merge Sort is a Divide-and-Conquer algorithm. 
It divides the input array in two halves, calls itself 
for the two halves and then merges the two sorted halves.

## C version
```c
void merge(int arr[], int l, int m, int r) {
    int i, j, k;
    int n1 = m - l + 1;
    int n2 =  r - m;
 
    int L[n1], R[n2];
 
    for (i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (j = 0; j < n2; j++)
        R[j] = arr[m + 1+ j];
 
    i = 0; 
    j = 0; 
    k = l; 
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        }
        else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
    
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }
    
    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}

void mergeSort(int arr[], int l, int r) {
    if (l < r) {
        int m = l+(r-l)/2;
 
        mergeSort(arr, l, m);
        mergeSort(arr, m+1, r);
 
        merge(arr, l, m, r);
    }
}

/* main function */
int main(){
    int arr[] = {2, 3, 17, 1, 34, 28, 90};
    int arr_length = sizeof(arr)/sizeof(arr[0]);

    mergeSort(arr, 0, arr_length - 1);

    return 0;
}
```

# Complexity
The algorithm uses recursion.

Recurrence Relation: T(n) = 2T(n/2) + \Theta(n)

Big O: O(nlogn) for best/worst/average case

