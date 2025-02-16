# Abstraction কিভাবে কাজ করে?

**Abstraction** (অ্যাবস্ট্রাকশন) হল একটি **অবজেক্ট-ওরিয়েন্টেড প্রোগ্রামিং** (OOP) ধারণা, যার মাধ্যমে অবজেক্টের **কমপ্লেক্স ইমপ্লিমেন্টেশন** হাইড রেখে শুধুমাত্র তার **প্রয়োজনীয়** এবং **গুরুত্বপূর্ণ ফিচারগুলো** প্রকাশ করা হয়। এটি আমাদের কেবলমাত্র সেই তথ্য এবং কার্যাবলী দেখাতে সাহায্য করে, যা ব্যবহারকারীর জন্য প্রয়োজনীয়, এবং বাকী সব কিছু হাইড রাখে।


# Abstraction কী?

**Abstraction** হচ্ছে OOP (Object-Oriented Programming) এর মোস্ট **essential** এবং **ইম্পোর্টেন্ট** ফিচার, যার মাধ্যমে আমরা কেবলমাত্র একটি অবজেক্টের **essential** ইনফরমেশন শো করি। এটি আমাদের কোডকে **পরিষ্কার** এবং **সহজবোধ্য** রাখে।

প্রোগ্রামিং এ **অ্যাবস্ট্রাকশন** বলতে বোঝায়, সফটওয়্যারের **কমপ্লেক্সিটি** হাইড করে ব্যবহারকারীর সামনে কেবলমাত্র **প্রয়োজনীয়** এবং **সহজবোধ্য ফিচারগুলি** উপস্থাপন করা। ব্যবহারকারীকে সিস্টেমের ভিতরের কমপ্লেক্সিটি বুঝতে হবে না, তাদের জন্য সিস্টেমটি আরোও সহজ ও কার্যকরী করে তোলা হয়। 

উদাহরণস্বরূপ, গাড়ির চালকের জন্য **গতি** এবং **স্টিয়ারিং** গুরুত্বপূর্ণ, কিন্তু **ইঞ্জিনের ভিতরের অংশগুলি** কিভাবে কাজ করে তা না জানলেও চলবে।


# উদাহরণ
এখন চলুন C++ কোডের মাধ্যমে দেখি Abstraction কিভাবে কাজ করে:

```cpp
#include <iostream>
using namespace std;

// Abstract class
class Animal {
public:
    // Pure virtual function
    virtual void sound() = 0; // Abstract method

    // Regular method
    void sleep() {
        cout << "Animal is sleeping" << endl;
    }

    // Destructor
    virtual ~Animal() {}
};

// Derived class
class Dog : public Animal {
public:
    // Implementation of the abstract method
    void sound() override {
        cout << "Dog says Woof!" << endl;
    }
};

// Another derived class
class Cat : public Animal {
public:
    // Implementation of the abstract method
    void sound() override {
        cout << "Cat says Meow!" << endl;
    }
};

int main() {
    // Pointers to abstract base class
    Animal* dog = new Dog();
    Animal* cat = new Cat();

    dog->sound(); // Dog says Woof!
    dog->sleep(); // Animal is sleeping

    cat->sound(); // Cat says Meow!
    cat->sleep(); // Animal is sleeping

    // Clean up memory
    delete dog;
    delete cat;

    return 0;
}
```
