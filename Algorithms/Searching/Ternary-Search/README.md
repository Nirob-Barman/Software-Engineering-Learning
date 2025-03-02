# Exploring Ternary Search: Another Adventure in C Programming

নীরব এখন Binary Search পদ্ধতিও শিখে ফেলেছে এবং সে জানত যে, Binary Search খুবই দ্রুত কাজ করে। তবে তার শিক্ষক তাকে নতুন কিছু শিখানোর সিদ্ধান্ত নিলেন, যেটি আরও একটি সার্চ পদ্ধতি—Ternary Search। শিক্ষক বললেন, "আজ আমরা শিখব Ternary Search পদ্ধতি।"

নীরব কৌতূহলী হয়ে শিক্ষককে প্রশ্ন করল, "Ternary Search কীভাবে কাজ করে?"

শিক্ষক বললেন, "ধরো তোমার কাছে একটি সাজানো (sorted) লিস্ট আছে। Ternary Search পদ্ধতিতে, আমরা লিস্টটিকে তিনটি ভাগে ভাগ করি। প্রথমে, আমরা দুটি মধ্যবর্তী উপাদান নির্বাচন করি, এবং দেখি, আমাদের কাঙ্খিত উপাদানটি কোন ভাগে আছে। তারপর, আমরা সেই ভাগে চলে যাই এবং আবার একইভাবে খোঁজ করতে থাকি।"

নীরব আরও জানতে চাইল, "তাহলে এটা কীভাবে কোডে লিখবো?"

শিক্ষক হেসে বললেন, "তুমি Ternary Search-এ তিনটি ভাগের মধ্যে খোঁজ করবে এবং সেটি কোডে এমনভাবে লিখবে যেন তুমি লিস্টের মধ্যবর্তী দুইটি উপাদান চেক করতে পারো। নিচে কোডটি দেখো:"

### C Code (Ternary Search):

```cpp
#include <stdio.h>

int ternarySearch(int arr[], int left, int right, int key) {
    while (right >= left) {
        // Divide the array into three parts
        int mid1 = left + (right - left) / 3;
        int mid2 = right - (right - left) / 3;

        // Check if key is present at mid1 or mid2
        if (arr[mid1] == key) {
            return mid1;
        }
        if (arr[mid2] == key) {
            return mid2;
        }

        // If key is smaller, search in the left third
        if (key < arr[mid1]) {
            right = mid1 - 1;
        }
        // If key is greater, search in the right third
        else if (key > arr[mid2]) {
            left = mid2 + 1;
        }
        // Otherwise, search in the middle third
        else {
            left = mid1 + 1;
            right = mid2 - 1;
        }
    }
    return -1;  // Element not found
}

int main() {
    int arr[] = {10, 20, 30, 40, 50, 60, 70, 80, 90};
    int size = sizeof(arr) / sizeof(arr[0]);
    int key = 50;
    
    int result = ternarySearch(arr, 0, size - 1, key);
    
    if (result != -1) {
        printf("Element found at index: %d\n", result);
    } else {
        printf("Element not found in the array.\n");
    }
    
    return 0;
}
```