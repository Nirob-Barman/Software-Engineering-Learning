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

### কোডের ব্যাখ্যা:

#### Abstract Class (Animal):
Animal একটি abstract ক্লাস, কারণ এতে একটি pure virtual function (sound()) রয়েছে। এর মানে হল যে, sound() ফাংশনটি Animal ক্লাসে ইমপ্লিমেন্ট করা হয়নি। বরং, যেকোনো derived ক্লাসে (যেমন Dog বা Cat) এই ফাংশনটি ইমপ্লিমেন্ট করতে হবে।
এই ক্লাসে একটি সাধারণ মেথড sleep() রয়েছে, যা কোনো derived ক্লাসে আবার ইমপ্লিমেন্ট করার প্রয়োজন নেই। অর্থাৎ, sleep() ফাংশনটি Animal ক্লাসের সকল derived ক্লাসের জন্য কমন।

#### Derived Classes (Dog এবং Cat):
Dog এবং Cat ক্লাস দুটি Animal ক্লাস থেকে ইনহেরিটেড এবং sound() ফাংশনটির নিজস্ব ইমপ্লিমেন্টেশন প্রদান করেছে।
উদাহরণস্বরূপ, Dog ক্লাসে sound() ফাংশনটি Woof! প্রদর্শন করে, আর Cat ক্লাসে sound() ফাংশনটি Meow! প্রদর্শন করে।
এইভাবে, Animal ক্লাসের sound() ফাংশনটি abstraction প্রদান করে, যার মাধ্যমে প্রতিটি প্রাণী নিজের শব্দ তৈরি করতে পারে, কিন্তু sound() ফাংশনের মূল স্ট্রাকচার পূর্বে নির্ধারিত থাকে।

#### Main Function:
এখানে Animal ক্লাসের পয়েন্টার ব্যবহার করে Dog এবং Cat ক্লাসের অবজেক্ট তৈরি করা হয়েছে। এর মাধ্যমে আমরা sound() ফাংশনটি কল করতে পারি যেটি বাস্তবে নির্ধারিত হয় যে প্রাণীটি কি ধরনের (কুকুর না বিড়াল)।

### Abstraction এর উপকারিতা:
**Implementation Details Hide করা**: Animal ক্লাস শুধুমাত্র একটি ইন্টারফেস প্রদান করে, যেখানে sound() একটি abstract ফাংশন। এটা নির্ধারণ করে যে, প্রত্যেকটি প্রাণীকে sound() ফাংশন থাকতে হবে, কিন্তু তারা কিভাবে শব্দ করবে তা তাদের উপর নির্ভর করে।

### উপসংহার:
C++ তে Abstraction এর মাধ্যমে আমরা কোডের কমপ্লেক্সিটি লুকিয়ে রেখে, একটি সাধারণ ইন্টারফেস ব্যবহার করে বিভিন্ন কাজ করতে পারি। এটি আমাদের কোডকে আরও পুনঃব্যবহারযোগ্য এবং মেইনটেনেবল করে তোলে। আশা করি আজকের উদাহরণটি আপনাদের সাহায্য করবে Abstraction ধারণা বোঝাতে।
