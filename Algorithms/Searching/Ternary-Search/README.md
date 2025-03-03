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


**কোড বিশ্লেষণ:** Ternary Search পদ্ধতিতে, Binary Search-এর মতো লিস্টের উপাদানগুলিকে দ্রুত খোঁজা হয়, তবে এখানে তিনটি ভাগে ভাগ করা হয়। প্রতিবার তিনটি ভাগে ভাগ করা হলে এটি একটু ধীর হতে পারে। কারণ প্রতি পদক্ষেপে তিনটি অংশে বিভক্ত হতে গিয়ে আরো একাধিক তুলনা করতে হয়।

এখন, চলুন কোডের একটি গুরুত্বপূর্ণ দিক ব্যাখ্যা করি:

* যখন "If key is smaller, search in the left third" শর্তটি কাজ করে, তখন আমরা **right** পয়েন্টারটি আপডেট করি **mid1 - 1** পর্যন্ত, কারণ আমাদের খোঁজ করতে হবে লিস্টের প্রথম অংশে। এ ক্ষেত্রে লেফট পয়েন্টার আগের মতোই থাকে, কারণ আমরা শুধু ডান পাশের সীমা নিয়ে কাজ করছি।
* তবে, "If key is greater, search in the right third" শর্তে, আমরা **left** পয়েন্টারটি আপডেট করি **mid2 + 1** পর্যন্ত, কারণ আমাদের খোঁজ করতে হবে লিস্টের তৃতীয় অংশে। এ ক্ষেত্রে রাইট পয়েন্টার আগের মতোই থাকে, কারণ আমরা শুধু বাম পাশের সীমা নিয়ে কাজ করছি।
* অন্যথায়, মাঝখানের তৃতীয়াংশে খোঁজ করতে হবে"। এর মানে হলো, আমরা লেফট পয়েন্টারকে **mid1 + 1** এবং রাইট পয়েন্টারকে **mid2 - 1** পর্যন্ত আপডেট করি, কারণ আমরা এখন লিস্টের মধ্যবর্তী অংশে খোঁজ করছি।

এখন, যদিও Ternary Search কৌতূহলজনক এবং কিছু পরিস্থিতিতে ফাস্ট হতে পারে, তবে Binary Search সাধারণত বেশি ফাস্ট। কারণ Binary Search প্রতি পদক্ষেপে লিস্টের অর্ধেক অংশ বাদ দেয়, যা খুবই দ্রুত ফলাফল দেয়।

**শেষ কথা:** নীরব বুঝলো যে, Ternary Search একটি তৃতীয় পদ্ধতি হতে পারে তবে এটি Binary Search-এর তুলনায় একটু কম ফাস্ট। নীরব Binary Search-এর গতি এবং দক্ষতা নিয়ে আরও বেশি সন্তুষ্ট হয়ে গিয়েছিল এবং সে এখন জানে যে কোন পরিস্থিতিতে কোন পদ্ধতি ব্যবহার করা উচিত!