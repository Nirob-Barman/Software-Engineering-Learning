# ইনহেরিটেন্সের মাধ্যমে বেস এবং ডিরাইভড ক্লাসের সম্পর্ক

**ইনহেরিটেন্স** (Inheritance) হল একটি অবজেক্ট-ওরিয়েন্টেড প্রোগ্রামিং (OOP) কনসেপ্ট, যা এক ক্লাসের(parent class) অ্যাট্রিবিউট / ফিল্ড / ডাটা মেম্বার এবং ফাংশন / মেথড অন্য ক্লাসে(Child Class) পুনরায় ব্যবহার করতে সাহায্য করে।

সহজ কথায়, ইনহেরিটেন্সের মাধ্যমে একটি নতুন ক্লাস (চাইল্ড / ডিরাইভড ক্লাস) বেজ বা প্যারেন্ট ক্লাসের অ্যাট্রিবিউট ও মেথড অ্যাক্সেস বা ব্যবহার করে।এতে কোডের পুনঃব্যবহারযোগ্যতা বৃদ্ধি পায়, এবং সিস্টেম ডিজাইন আরও সহজ হয়।

ইনহেরিটেন্সের মাধ্যমে, বেজ বা প্যারেন্ট ক্লাসের সব প্রাইভেট অ্যাট্রিবিউট এবং মেথড ছাড়া অন্য সব অ্যাট্রিবিউট এবং মেথড ডিরাইভড ক্লাসের দ্বারা অ্যাক্সেস করা যায়।

এখানে একটি সহজ উদাহরণ শেয়ার করছি যেখানে বেজ ক্লাসে একটি মেম্বার ভেরিয়েবল এবং একটি মেথড আছে, এবং ডিরাইভড ক্লাস সেই অ্যাট্রিবিউট ও মেথড ব্যবহার করে। getName() মেথডটি বেজ ক্লাসে ডিফাইন করা হয়েছে এবং ডিরাইভড ক্লাসে এটি ব্যবহার করা হয়েছে।

```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    string name;  // Member variable in the base class

    // Method to get the name of the animal
    string getName() {
        return name;
    }
};

// Derived class
class Dog : public Animal {
public:
    // Constructor to set the name
    Dog(string n) {
        name = n;
    }

    void speak() {
        cout << getName() << " barks." << endl;  // Using the base class method
    }
};

int main() {
    Dog dog("Buddy");  // Creating a Dog object with a name
    dog.speak();  // Calls the derived class function

    return 0;
}
```