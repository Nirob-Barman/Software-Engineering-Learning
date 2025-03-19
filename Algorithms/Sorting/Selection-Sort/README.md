# From Unsorted to Sorted: A Beginner's Journey with Selection Sort

একদিন নীরব তার শিক্ষককে আবার প্রশ্ন করলো, "স্যার, যদি আমাকে একটি বড় লিস্ট দেওয়া হয় এবং আমি চাই যে, সেই লিস্টটি সঠিক ক্রমে অন্য উপায়ে সাজাতে, তাহলে আমি কীভাবে অন্য উপায়ে সাজাতে পারব? আর কি কোনো নতুন পদ্ধতি আছে?"

শিক্ষক হাসি দিয়ে বললেন, "অবশ্যই! তুমি এখন যে পদ্ধতির কথা শুনবে, তার নাম Selection Sort। এই পদ্ধতিতে, আমরা লিস্টের মধ্যে সবচেয়ে ছোট (অথবা সবচেয়ে বড়) উপাদান খুঁজে সিলেক্ট করি এবং সেটিকে প্রথমে নিয়ে আসি। এরপর বাকি এলিমেন্টগুলির জন্য একই কাজ করি, এবং এভাবে পুরো লিস্টটি সাজানো হয়ে যায়।"

নীরব আরও জানতে চাইলো, "তাহলে আমি কীভাবে Selection Sort এর প্রোগ্রাম C তে লিখব?"
শিক্ষক তাকে C কোড দেখালেন, যা Selection Sort অ্যালগরিদম ব্যবহার করে:

### C Code (Selection Sort):
```cpp
#include <stdio.h>

// Selection Sort function to sort the array
void selectionSort(int arr[], int size) {
    for (int i = 0; i < size - 1; i++) {
        int minIndex = i;  // Assume the current element is the smallest

        // Find the smallest element in the remaining unsorted array
        for (int j = i + 1; j < size; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;  // Update the index of the smallest element
            }
        }

        // Swap the found smallest element with its proper position
        if (minIndex != i) {
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
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

    selectionSort(arr, size);

    printf("\nSorted array: \n");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```
### Output:
```
Original array: 
64 34 25 12 22 11 90 
Sorted array: 
11 12 22 25 34 64 90
```

### Explanation:
নীরব কোডটি পড়লো এবং বুঝলো কীভাবে Selection Sort কাজ করে। এই কোডের মধ্যে, **selectionSort** ফাংশনটি একটি লিস্ট (অ্যারে) নেয় এবং প্রতিটি এলিমেন্টের জন্য অনুসন্ধান করে সবচেয়ে ছোট উপাদানটি খুঁজে বের করে। তারপরে, সেই ছোট উপাদানটি প্রথম স্থানে নিয়ে আসা হয়। এই প্রক্রিয়া প্রতিটি এলিমেন্টের জন্য করা হয়, এবং এক এক করে লিস্টটি সাজানো হয়ে যায়।

এখন, সঠিকভাবে Selection Sort এর কাজ বুঝতে হলে, **sorted** এবং **unsorted** অংশের মধ্যে পার্থক্য পরিষ্কার করা যাক:
1. **Unsorted Portion:** প্রথমে পুরো অ্যারে আনসর্টেড লিস্ট হিসেবে বিবেচনা করা হয়। অর্থাৎ, কোনো সঠিক ক্রমে সাজানো থাকে না। এই পুরো অ্যারের মধ্যে আমরা লুকিয়ে থাকা সবচেয়ে ছোট উপাদানটি খুঁজে বের করব। শুরুতে পুরো অ্যারেটিই **unsorted**।
2. **Sorted Portion:** প্রতিটি পাসে, আমরা এক একটি উপাদানকে সঠিক স্থানে নিয়ে আসি। এইভাবে, যতবার পাস হয়, ততবার একে একে ছোট ছোট উপাদানগুলি তাদের সঠিক স্থানে চলে আসে। প্রতিটি নতুন পাসে, সেই "sorted portion" বাড়তে থাকে। এর মানে, যতটুকু অংশ আমরা সঠিকভাবে সাজিয়ে ফেলেছি, তা "sorted portion" হয়ে যায়। বাকি অংশটি তখনও **unsorted** থাকে।

প্রথম পাসে, সবচেয়ে ছোট উপাদানটি প্রথম স্থানে চলে আসে, দ্বিতীয় পাসে পরবর্তী ছোট উপাদানটি দ্বিতীয় স্থানে চলে আসে, এবং এইভাবে পুরো লিস্টটি সঠিকভাবে সাজানো হয়।

### Example:
ধরা যাক, আমরা একটি অ্যারে নিচ্ছি: **{64, 34, 25, 12, 22, 11, 90}**। প্রথম পাসের শেষে সবচেয়ে ছোট উপাদান 11 প্রথম স্থানে চলে আসে, এবং বাকি অংশটি এখন **unsorted** থাকে। পরবর্তী পাসে, 12 সঠিক স্থানে চলে আসে, এবং এটি sorted portion হয়ে যায়। এভাবে ধাপে ধাপে অ্যারে পুরোপুরি **Sorted** হয়ে যায়। চলুন বিস্তারিত দেখি।

ধরা যাক, আমাদের কাছে একটি অ্যারে আছে: {64, 34, 25, 12, 22, 11, 90}। এখন, আসুন প্রথম পাসটি দেখি: