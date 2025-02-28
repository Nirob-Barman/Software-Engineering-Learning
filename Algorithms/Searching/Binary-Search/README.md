# Exploring Binary Search: A New Adventure in C Programming

নীরব এখন Linear Search শিখে ফেলেছে এবং সে বুঝতে পেরেছে যে, সব উপাদান চেক করার মাধ্যমে কিছু খুঁজে পাওয়া সহজ হলেও, এটি কিছুটা ধীর। তার শিক্ষক তখন নীরবকে আরেকটি উন্নত সার্চ পদ্ধতি শিখানোর কথা বললেন, যেটি আরও দ্রুত। শিক্ষক বললেন, "আজ আমরা শিখব Binary Search পদ্ধতি।"

নীরব খুবই কৌতূহলী হয়ে শিক্ষককে প্রশ্ন করল, "Binary Search কীভাবে কাজ করে?"

শিক্ষক বললেন, "ধরো তোমার কাছে একটা সাজানো (sorted) লিস্ট আছে। Binary Search পদ্ধতিতে, তুমি প্রথমে লিস্টের মাঝখানে থাকা উপাদানটি চেক করবে। যদি সেটা তোমার কাঙ্খিত উপাদান না হয়, তাহলে তুমি জানবে যে উপাদানটি নিশ্চয়ই লিস্টের যেকোনো একপাশে থাকতে পারে। তুমি লিস্টটিকে দুটি ভাগে ভাগ করে, প্রতিটি ভাগের মধ্যে শুধু একটি ভাগকে চেক করবে। এইভাবে পদ্ধতিটি দ্রুত কাজ করে।"

নীরব খুব আগ্রহী হয়ে বলল, "তাহলে আমি এই পদ্ধতি C কোডে কীভাবে লিখব?"

শিক্ষক হেসে বললেন, "তুমি Binary Search পদ্ধতিটি এমনভাবে কোডে লিখবে, যেন তুমি লিস্টের মাঝখানের উপাদান চেক করতে পারো এবং উপাদানটি বড় না ছোট তার উপর ভিত্তি করে উপযুক্ত ভাগে যেতে পারো। নিচে কোডটি দেখো:"

## C Code (Binary Search):

```cpp
#include <stdio.h>

int binarySearch(int arr[], int size, int key) {
    int left = 0, right = size - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;  // Find the middle index
        
        // Check if key is present at mid
        if (arr[mid] == key) {
            return mid;  // Element found at index mid
        }
        
        // If key is smaller, ignore the right half
        if (arr[mid] > key) {
            right = mid - 1;
        }
        // If key is larger, ignore the left half
        else {
            left = mid + 1;
        }
    }
    
    return -1;  // Element not found
}

int main() {
    int arr[] = {12, 23, 34, 45, 56, 78, 90};
    int size = sizeof(arr) / sizeof(arr[0]);
    int key = 56;
    
    int result = binarySearch(arr, size, key);
    
    if (result != -1) {
        printf("Element found at index: %d\n", result);
    } else {
        printf("Element not found in the array.\n");
    }
    
    return 0;
}
```
