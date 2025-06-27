
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