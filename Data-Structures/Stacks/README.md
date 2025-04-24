# 🎯 স্ট্যাক (Stack) নিয়ে বিস্তারিত — ডেফিনেশন, অপারেশনস এবং উদাহরণ (C ল্যাংগুয়েজ)

প্রোগ্রামিং জগতে **স্ট্যাক** একটি গুরুত্বপূর্ণ ডেটা স্ট্রাকচার, যা **Last In First Out (LIFO)** নীতিতে কাজ করে। আজকে আমরা জানব:

* স্ট্যাক কী
* কীভাবে এটি কাজ করে
* কী কী অপারেশন করা যায়
* বাস্তব উদাহরণ সহ ব্যাখ্যা

আমরা উদাহরণ হিসেবে C ল্যাংগুয়েজ ব্যবহার করব।

## 1. Stack Definition (স্ট্যাক ডেফিনেশন)
স্ট্যাক হলো এমন একটি ডেটা স্ট্রাকচার যেখানে সর্বশেষে ইনসার্ট করা উপাদানটি সবার আগে রিমুভ হয়। এই নীতিটিকে বলে LIFO – Last In, First Out।

একটা টেবিলে রাখা ট্রের স্তূপ কল্পনা করো। যেই ট্রেটা সবার উপরে আছে, সেটা সবার আগে উঠবে। এটিই স্ট্যাকের বাস্তব উদাহরণ।

## 2. Stack Operations (স্ট্যাক অপারেশনস)
স্ট্যাকে সাধারণত পাঁচটি মৌলিক অপারেশন থাকে:
* **push(x)** → উপরে একটি উপাদান যোগ করে
* **pop()** → উপরের উপাদানটি সরিয়ে ফেলে
* **topElement()** → বর্তমান টপ উপাদান রিটার্ন করে
* **isEmpty()** → স্ট্যাক খালি কিনা তা যাচাই করে
* **size()** → স্ট্যাকের বর্তমান সাইজ জানায়

### (a) Push Operation

স্ট্যাকে নতুন উপাদান যোগ করার জন্য Push অপারেশন ব্যবহার করা হয়। উপাদানটি সবসময় স্ট্যাকের উপরে যোগ হয়।
```
void push(int stack[], int x, int n) { 
    if (top == n - 1) { // Check if the stack is full
        cout << "Stack is full. Overflow condition!" << endl;
    } else {
        top = top + 1; // Increment the top position
        stack[top] = x; // Insert the element at the top
    }
}
```

### (b) Pop Operation

স্ট্যাকের উপরের উপাদানটি রিমুভ করার জন্য Pop অপারেশন ব্যবহার করা হয়।
```
void pop() {
    if (isEmpty()) {
        cout << "Stack is empty. Underflow condition!" << endl;
    } else {
        top = top - 1; // Decrement the top position
    }
}
```

### (c) Top Element
স্ট্যাকের উপরের উপাদানটি অ্যাক্সেস করার জন্য ব্যবহৃত হয়।
```
int topElement(int stack[]) {
    return stack[top];
}
```

### d) isEmpty
স্ট্যাকটি খালি কিনা তা চেক করার জন্য ব্যবহৃত হয়।
```
bool isEmpty() {
    return top == -1;
}
```

### (e) Size
স্ট্যাকের বর্তমান সাইজ নির্ণয় করার জন্য ব্যবহৃত হয়।
```
int size() {
    return top + 1;
}
```

## 3. Stack Implementation in C (C ল্যাংগুয়েজে স্ট্যাক ইমপ্লিমেন্টেশন)
```
#include <iostream>
using namespace std;

int top = -1; // শুরুতে স্ট্যাক খালি

void push(int stack[], int x, int n) {
    if (top == n - 1) {
        cout << "Stack is full. Overflow condition!" << endl;
    } else {
        top = top + 1;
        stack[top] = x;
    }
}

bool isEmpty() {
    return top == -1;
}

void pop() {
    if (isEmpty()) {
        cout << "Stack is empty. Underflow condition!" << endl;
    } else {
        top = top - 1;
    }
}

int size() {
    return top + 1;
}

int topElement(int stack[]) {
    return stack[top];
}

int main() {
    int stack[3];

    push(stack, 100, 3);
    cout << "Current size of stack is " << size() << endl;

    push(stack, 200, 3);
    push(stack, 300, 3);
    cout << "Current size of stack is " << size() << endl;

    push(stack, 400, 3); // Overflow

    cout << "Top element: " << topElement(stack) << endl;

    for (int i = 0; i < 3; i++) {
        pop();
    }
    cout << "Current size of stack is " << size() << endl;

    pop(); // Underflow

    return 0;
}
```

## 4. Output
```
Current size of stack is 1
Current size of stack is 3
Stack is full. Overflow condition!
Top element: 300
Current size of stack is 0
Stack is empty. Underflow condition!
```

## 5. স্ট্যাকের অ্যাপ্লিকেশন — ব্র্যাকেট ব্যালেন্স চেক
একটি স্ট্রিং-এর প্রথম এবং শেষ বন্ধনী সঠিকভাবে ব্যালেন্সড কিনা তা চেক করতে স্ট্যাক ব্যবহার করা যায়। 
