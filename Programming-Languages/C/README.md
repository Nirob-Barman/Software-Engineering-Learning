
## Array

Declare and initialize with size:
```
int numbers[5];
```

Declare and initialize with values:
```
int numbers[5] = {1, 2, 3, 4, 5};
```


## Linear Search
```
int linearSearch(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i;  // Return the index where target is found
        }
    }
    return -1;  // Return -1 if target is not found
}

int main() {
    int numbers[] = {4, 2, 7, 1, 9, 3};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    int target = 7;

    int result = linearSearch(numbers, size, target);

    if (result != -1) {
        printf("Element %d found at index %d.\n", target, result);
    } else {
        printf("Element %d not found in the array.\n", target);
    }
    return 0;
}
```

## Binary Search
```
int binarySearch(int arr[], int size, int target) {
    int left = 0;
    int right = size - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;  // Prevent overflow

        if (arr[mid] == target) {
            return mid;  // Target found
        } else if (arr[mid] < target) {
            left = mid + 1;  // Search right half
        } else {
            right = mid - 1; // Search left half
        }
    }

    return -1;  // Target not found
}

int main() {
    int numbers[] = {1, 3, 5, 7, 9, 11};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    int target = 7;

    int result = binarySearch(numbers, size, target);

    if (result != -1) {
        printf("Element %d found at index %d.\n", target, result);
    } else {
        printf("Element %d not found in the array.\n", target);
    }

    return 0;
}
```

## Bubble Sort
```
void bubbleSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        // Last i elements are already sorted
        for (int j = 0; j < size - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap arr[j] and arr[j + 1]
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int main() {
    int numbers[] = {64, 34, 25, 12, 22, 11, 90};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    bubbleSort(numbers, size);

    printf("Sorted array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    return 0;
}
```

## Selection Sort
```
void selectionSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        int minIndex = i;

        // Find the minimum element in the unsorted part
        for (int j = i + 1; j < size; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }

        // Swap the found minimum with the first unsorted element
        if (minIndex != i) {
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
}

int main() {
    int numbers[] = {29, 10, 14, 37, 13};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    selectionSort(numbers, size);

    printf("Sorted array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    return 0;
}
```


## Insertion Sort
```
void insertionSort(int arr[], int size) {
    for (int i = 1; i < size; i++) {
        int key = arr[i];
        int j = i - 1;

        // Move elements of arr[0..i-1], that are greater than key,
        // to one position ahead of their current position
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }

        arr[j + 1] = key;
    }
}

int main() {
    int numbers[] = {12, 11, 13, 5, 6};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    insertionSort(numbers, size);

    printf("Sorted array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");

    return 0;
}
```

## Merge Sort
```
// Function to merge two halves of the array
void merge(int arr[], int left, int mid, int right) {
    int i, j, k;
    int n1 = mid - left + 1;
    int n2 = right - mid;

    // Create temp arrays
    int L[n1], R[n2];

    // Copy data to temp arrays
    for (i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for (j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];

    // Merge the temp arrays back into arr[left..right]
    i = 0;
    j = 0;
    k = left;

    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k++] = L[i++];
        } else {
            arr[k++] = R[j++];
        }
    }

    // Copy remaining elements of L[], if any
    while (i < n1) {
        arr[k++] = L[i++];
    }

    // Copy remaining elements of R[], if any
    while (j < n2) {
        arr[k++] = R[j++];
    }
}

// Merge Sort function
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        // Sort first and second halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        merge(arr, left, mid, right);
    }
}

// Helper function to print the array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

// Main function to test the Merge Sort
int main() {
    int numbers[] = {38, 27, 43, 3, 9, 82, 10};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    printf("Original array: ");
    printArray(numbers, size);

    mergeSort(numbers, 0, size - 1);

    printf("Sorted array: ");
    printArray(numbers, size);

    return 0;
}
```

## Quick Sort
```
#include <stdio.h>

// Function to swap two elements
void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

// Partition function to place pivot element at correct position
int partition(int arr[], int low, int high) {
    int pivot = arr[high];  // Choose the last element as pivot
    int i = low - 1;        // Index of smaller element

    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(&arr[i], &arr[j]);
        }
    }

    swap(&arr[i + 1], &arr[high]);
    return i + 1;
}

// Quick Sort function
void quickSort(int arr[], int low, int high) {
    if (low < high) {
        // Partitioning index
        int pi = partition(arr, low, high);

        // Recursively sort elements before and after partition
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

// Helper function to print the array
void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

// Main function to test Quick Sort
int main() {
    int numbers[] = {10, 7, 8, 9, 1, 5};
    int size = sizeof(numbers) / sizeof(numbers[0]);

    printf("Original array: ");
    printArray(numbers, size);

    quickSort(numbers, 0, size - 1);

    printf("Sorted array: ");
    printArray(numbers, size);

    return 0;
}
```