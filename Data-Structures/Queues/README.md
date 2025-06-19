# কিউ (Queue) নিয়ে বিস্তারিত — ডেফিনেশন, অপারেশনস এবং উদাহরণ (C ল্যাংগুয়েজ)

Queue একটি লিনিয়ার ডেটা স্ট্রাকচার যা লাইনের মতো কাজ করে — উপাদান একদিকে প্রবেশ করে (enqueue) এবং অপরদিকে থেকে বের হয় (dequeue), First In First Out (FIFO) নীতিতে।

আজকে আমরা জানব:

-  ✔️ কিউ কী
-  ✔️ কীভাবে এটি কাজ করে
-  ✔️ কী কী অপারেশন করা যায়
-  ✔️ বাস্তব উদাহরণ সহ ব্যাখ্যা

আমরা উদাহরণ হিসেবে C ল্যাংগুয়েজ ব্যবহার করব।

## 1. Queue Definition (কিউ ডেফিনেশন)
Queue হলো এমন একটি ডেটা স্ট্রাকচার যেখানে উপাদান সামনের দিক থেকে রিমুভ এবং পিছনের দিক থেকে ইনসার্ট করা হয়। এটি FIFO – First In, First Out নিয়মে চলে।

বাস্তব উদাহরণ:

বাস স্টপে লাইনের কল্পনা করো — যে যাত্রী সবার আগে লাইনে এসেছে, সে-ই সবার আগে বাসে উঠবে। এটি কিউ-এর বাস্তব উদাহরণ।

কল সেন্টারে কাস্টমার কল হ্যান্ডলিং-এর সময়, প্রথম যিনি কল করেন, তার কলটাই প্রথম এজেন্ট গ্রহণ করে। এটিও কিউ ব্যবহারের একটি ভালো উদাহরণ।


## 2. Queue Operations (কিউ অপারেশনস)
- একটি কিউতে সাধারণত নিচের অপারেশনগুলো থাকে:
- enqueue(x) → নতুন উপাদান কিউ-এর শেষে যোগ করা
- dequeue() → কিউ-এর সামনে থেকে উপাদান সরানো
- frontElement() → সামনে থাকা উপাদান দেখা
- isEmpty() → কিউ খালি কিনা চেক করা
- size() → কিউ-এর বর্তমান সাইজ নির্ণয় করা।

### (a) Enqueue Operation

```
void enqueue(int queue[], int x, int n) {
    if (rear == n - 1) {
        printf("Queue is full. Overflow!\n");
    } else {
        if (front == -1) front = 0;
        rear++;
        queue[rear] = x;
    }
}
```

### (b) Dequeue Operation

```
void dequeue() {
    if (front == -1 || front > rear) {
        printf("Queue is empty. Underflow!\n");
    } else {
        front++;
    }
}
```


### (c) Front Element
```
int frontElement(int queue[]) {
    return queue[front];
}
```

### (d) isEmpty
```
int isEmpty() {
    return front == -1 || front > rear;
}
```

### (e) size
```
int size() {
    if (isEmpty()) return 0;
    return rear - front + 1;
}
```

## 3. Queue Implementation in C

```
#include <stdio.h>

#define SIZE 5
int queue[SIZE];
int front = -1, rear = -1;

void enqueue(int queue[], int x, int n) {
    if (rear == n - 1) {
        printf("Queue is full. Overflow!\n");
    } else {
        if (front == -1) front = 0;
        rear++;
        queue[rear] = x;
    }
}

void dequeue() {
    if (front == -1 || front > rear) {
        printf("Queue is empty. Underflow!\n");
    } else {
        front++;
    }
}

int isEmpty() {
    return front == -1 || front > rear;
}

int frontElement(int queue[]) {
    return queue[front];
}

int size() {
    if (isEmpty()) return 0;
    return rear - front + 1;
}

int main() {
    enqueue(queue, 10, SIZE);
    enqueue(queue, 20, SIZE);
    enqueue(queue, 30, SIZE);
    printf("Front element: %d\n", frontElement(queue));
    printf("Queue size: %d\n", size());

    dequeue();
    printf("After one dequeue, front element: %d\n", frontElement(queue));
    printf("Queue size: %d\n", size());

    dequeue();
    dequeue();
    dequeue(); // Underflow

    return 0;
}
```


## 4. Output
```
Front element: 10  
Queue size: 3  
After one dequeue, front element: 20  
Queue size: 2  
Queue is empty. Underflow!
```

## 5. কিউ-এর অ্যাপ্লিকেশন — অর্ডার প্রসেসিং
ধরা যাক, একটি রেস্টুরেন্টে কাস্টমাররা অর্ডার দেয় এবং সেগুলো কিচেনে একটি কিউ হিসেবে জমা হয়। যেই অর্ডারটি আগে এসেছে, সেটিই আগে রান্না করা হয়।
