
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