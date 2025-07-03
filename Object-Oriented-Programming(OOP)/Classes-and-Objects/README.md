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

## কনস্ট্রাক্টর ব্যবহার করে অবজেক্ট ইনিশিয়ালাইজেশন

আগের উদাহরণে আমরা ম্যানুয়ালি অবজেক্টের অ্যাট্রিবিউট সেট করেছি। তবে, **কনস্ট্রাক্টর ব্যবহার করে এই অ্যাট্রিবিউটগুলি ইনিশিয়ালাইজ করা আরও সহজ এবং কার্যকরী হতে পারে।** কনস্ট্রাক্টর অবজেক্ট তৈরির সময় অটোমেটিকভাবে অ্যাট্রিবিউটের মান সেট করে দেয়। পরবর্তীতে কখনো কনস্ট্রাক্টর নিয়ে বিস্তারিত আলোচনা করার চেষ্টা করবো।

```cpp
#include <iostream>
using namespace std;

class Car {
public:
    string name;
    string model;

    // Constructor to initialize the car's name and model
    Car(string n, string m) {
        name = n;
        model = m;
    }

    // Method to start the car
    void start() {
        cout << name << " " << model << " car is starting." << endl;
    }

    // Method to display car details
    void display() {
        cout << "Car Name: " << name << ", Model: " << model << endl;
    }
};

int main() {
    // Creating objects of the Car class using the constructor
    Car car1("Toyota", "Corolla");
    Car car2("Honda", "Civic");

    // Calling methods of car1
    car1.start();
    car1.display();

    // Calling methods of car2
    car2.start();
    car2.display();

    return 0;
}
```

### আউটপুট:
```plaintext
Toyota Corolla car is starting.
Car Name: Toyota, Model: Corolla
Honda Civic car is starting.
Car Name: Honda, Model: Civic
```

## ক্লাস ও অবজেক্ট বিষয়ক প্রোগ্রামের উদাহরণসমূহ

1. [A C++ program to introduce class of objects](https://github.com/Nirob-Barman/Object-Oriented-Programming/blob/main/Chapter-5-Classes-and-Objects/001-a-c%2B%2B-program-to-introduce-class-of-objects.cpp)

2. [Another C++ program to introduce class of objects](https://github.com/Nirob-Barman/Object-Oriented-Programming/blob/main/Chapter-5-Classes-and-Objects/002-a-c%2B%2B-program-to-introduce-class-of-objects.cpp)

3. [A C++ program to introduce nesting of member function](https://github.com/Nirob-Barman/Object-Oriented-Programming/blob/main/Chapter-5-Classes-and-Objects/003-a-c%2B%2B-program-to-introduce-nesting-of-member-function.cpp)

4. A C++ program to introduce arrays within a class

5. A C++ program to introduce static data member

6. A C++ program to introduce static data member and member function

7. A sample C++ program to introduce arrays of objects

8. A sample C++ program to introduce objects as function arguments

9. A sample C++ program to introduce returning objects

10. A sample C++ program to introduce friend function

11. A sample C++ program to demonstrate how friend functions work as bridge between the classes

12. A sample C++ program that shows how to use common friend function to exchange the private values of two classes

## উপসংহার

**ক্লাস এবং অবজেক্টের ধারণা OOP-এর মূল ভিত্তি।** ক্লাস আমাদের একটি **টেমপ্লেট** দেয়, যার মাধ্যমে আমরা **একাধিক অবজেক্ট তৈরি** করতে পারি। এর ফলে **কোড পুনরায় ব্যবহারযোগ্য হয়** এবং **প্রোগ্রামিং আরও সংগঠিত ও সহজ** হয়ে ওঠে।  

যখন আপনি **OOP-এর মাধ্যমে কোড লিখবেন**, তখন বুঝতে পারবেন **কিভাবে এই কনসেপ্টগুলো সফটওয়্যার ডেভেলপমেন্টে সাহায্য করে**, এবং **OOP আপনার কোডিং দক্ষতা বাড়াতে সহায়ক হবে।** 🚀
