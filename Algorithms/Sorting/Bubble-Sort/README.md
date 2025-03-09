# The Bubble Sort Algorithm: A Simple Approach to Sorting Algorithms

একদিন নীরব তার শিক্ষককে জিজ্ঞেস করলো, "স্যার, যদি আমাকে একটি বড় লিস্ট দেওয়া হয় এবং আমি চাই যে, সেই লিস্টটিকে সঠিক ক্রমে সাজাতে, তাহলে আমি কীভাবে সাজাতে পারব?"

শিক্ষক হাসি দিয়ে বললেন, "তুমি যে প্রশ্ন করছো, তার উত্তর হলো **Bubble Sort**। এই পদ্ধতিতে আমরা লিস্টের পাশের দুইটি উপাদান তুলনা করি এবং যদি তাদের ক্রম সঠিক না হয়, তবে সেগুলো একে অপরের সাথে স্থান বিনিময় করি। আমরা এটি ততক্ষণ পর্যন্ত পুনরাবৃত্তি করি যতক্ষণ না পুরো লিস্ট সঠিকভাবে সাজানো হয়।"

নীরব অবাক হয়ে বললো, "তাহলে আমি কীভাবে এই প্রোগ্রামটি C কোডে লিখব?"

শিক্ষক তখন তাকে একটি কোড দেখালেন যা Bubble Sort পদ্ধতি ব্যবহার করে:

### C Code (Bubble Sort):

```cpp
#include <stdio.h>
#include <stdbool.h>  // Include for using bool

// An optimized version of Bubble Sort
void bubbleSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        bool swapped = false;  // To track if a swap happened

        // Loop through the array and (size-i-1) is for ignoring comparisons of elements which have already been compared in earlier iterations
        for (int j = 0; j < size - i - 1; j++) {
            // Compare adjacent elements
            if (arr[j] > arr[j + 1]) {
                // Swap if the current element is greater than the next element
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                swapped = true;  // Mark that a swap occurred
            }
        }

        // If no two elements were swapped in the inner loop, then the array is already sorted
        if (!swapped) {
            break;
        }
    }
}

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int size = sizeof(arr) / sizeof(arr[0]);

    printf("Original array: \n");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }

    bubbleSort(arr, size);

    printf("Sorted array: \n");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```

আউটপুট:
```
Original array: 
64 34 25 12 22 11 90 
Sorted array: 
11 12 22 25 34 64 90 
```