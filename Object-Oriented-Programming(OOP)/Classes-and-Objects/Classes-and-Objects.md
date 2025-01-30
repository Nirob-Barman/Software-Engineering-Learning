# Introduction to Classes and Objects in Object-Oriented Programming (OOP)

**Object-Oriented Programming (OOP)** হচ্ছে পপুলার প্রোগ্রামিং প্যারাডাইম(paradigms) যা সফটওয়্যার ডেভেলপমেন্টে ব্যাপকভাবে ব্যবহৃত হয়। OOP-তে **ক্লাস** এবং **অবজেক্ট** দুটি মূল ফিচার যা প্রোগ্রামের কাঠামো তৈরি করতে সাহায্য করে। এই পোস্টে, আমরা **ক্লাস** এবং **অবজেক্ট** কী এবং কীভাবে এগুলো কাজ করে, তা একটি উদাহরণের মাধ্যমে বুঝার চেষ্টা করবো।

## ক্লাস কী?
ক্লাস মূলত ব্লুপ্রিন্ট বা টেমপ্লেট হিসেবে কাজ করে, যা অবজেক্ট (Object) তৈরির জন্য স্ট্রাকচার প্রদান করে। ক্লাসে ডেটা (**attribute**) এবং ফাংশন (**method**) একত্রিত থাকে, যা ক্লাসের অবজেক্টের মাধ্যমে ব্যবহৃত হয়।

## অবজেক্ট কী?
অবজেক্ট হলো ক্লাসের একটি নির্দিষ্ট **ইনস্ট্যান্স (instance)**। একাধিক অবজেক্ট একই ক্লাস থেকে তৈরি হতে পারে, তবে তাদের ডেটা আলাদা থাকতে পারে।

---

### উদাহরণ: `Car` ক্লাস
ধরা যাক, আমরা একটি `Car` ক্লাস তৈরি করেছি, যেখানে দুটি অ্যাট্রিবিউট থাকবে:  
- `name` (গাড়ির নাম)  
- `model` (গাড়ির মডেল)  

এছাড়া, দুটি মেথড থাকবে:  
1. `start()` (গাড়ি স্টার্ট করা)  
2. `display()` (গাড়ির বিস্তারিত তথ্য প্রদর্শন করা)  

#### Code Example:
```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string name;
    string model;

    // Method to start the car
    void start() {
        cout << name << " " << model << " car is starting." << endl;
    }

    // Method to display car details
    void display() {
        cout << "Car Name: " << name << ", Model: " << model << endl;
    }
};
```

এখানে **Car** ক্লাসটি তৈরি হয়েছে। এখন এই ক্লাস থেকে একাধিক অবজেক্ট তৈরি করা যাবে, এবং প্রতিটি অবজেক্টের ডেটা আলাদা হবে।

```cpp
int main() {
    // Creating two objects of the Car class
    Car car1, car2;

    // Setting attributes for car1
    car1.name = "Toyota";
    car1.model = "Corolla";

    // Setting attributes for car2
    car2.name = "Honda";
    car2.model = "Civic";

    // Calling methods of car1
    car1.start();
    car1.display();

    // Calling methods of car2
    car2.start();
    car2.display();

    return 0;
}

```
## ব্যাখ্যা:
`Car` ক্লাসের মাধ্যমে আমরা দুটি অবজেক্ট (`car1` এবং `car2`) তৈরি করেছি। আমরা সরাসরি `main()` ফাংশনে এই অবজেক্টগুলোর অ্যাট্রিবিউটের মান সেট করেছি।


`car1.name = "Toyota";`  
`car1.model = "Corolla";`  

এইভাবে, আমরা `car1` অবজেক্টের নাম এবং মডেল অ্যাট্রিবিউটের মান নির্ধারণ করেছি।  

একইভাবে, `car2` অবজেক্টের অ্যাট্রিবিউট সেট করা হয়েছে:  
`car2.name = "Honda";`  
`car2.model = "Civic";`  

এখানে `start()` এবং `display()` মেথডগুলো প্রত্যেকটি অবজেক্টের অ্যাট্রিবিউট ব্যবহার করে কাজ করছে।

### আউটপুট:
```plaintext
Toyota Corolla car is starting.
Car Name: Toyota, Model: Corolla
Honda Civic car is starting.
Car Name: Honda, Model: Civic
```
