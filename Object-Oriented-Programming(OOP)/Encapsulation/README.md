# নীরবের শেখা: এনক্যাপসুলেশন এবং ডেটা সুরক্ষা

একদা, নীরব নামক একজন মেধাবী ছেলে একটি গ্রামে বাস করত। নীরব নতুন কিছু শেখা এবং কোডিং করতে খুব পছন্দ করত।  

একদিন, সে তার শিক্ষক থেকে একটি গুরুত্বপূর্ণ ধারণা শুনল – **এনক্যাপসুলেশন**। শিক্ষক বললেন, *"এনক্যাপসুলেশন একটি ধারণা, যেখানে আমরা ডেটা এবং ফাংশনগুলোকে একত্রিত করে সেই ডেটার সরাসরি অ্যাক্সেস সীমাবদ্ধ করি। এর ফলে ডেটার সুরক্ষা বৃদ্ধি পায়।"*

নীরব খুব আগ্রহী হয়ে এই ধারণা সম্পর্কে আরও জানতে চাইল। তখন শিক্ষক তাকে একটি উদাহরণ দিয়ে বুঝালেন:

## C++ কোড উদাহরণ:

```cpp
#include <iostream>
using namespace std;

// Creating a class
class Account {
private:
    // Keeping data members hidden
    double balance;

public:
    // Constructor
    Account(double initialBalance) {
        if (initialBalance >= 0) {
            balance = initialBalance;
        } else {
            balance = 0;
        }
    }

    // Deposit function
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        } else {
            cout << "Invalid amount!" << endl;
        }
    }

    // Withdraw function
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        } else {
            cout << "Insufficient balance or invalid amount!" << endl;
        }
    }

    // Function to view balance
    double getBalance() {
        return balance;
    }
};

int main() {
    // Creating an account
    Account myAccount(1000.0);
    
    // Viewing balance after account creation
    cout << "Account created. Your current balance is: " << myAccount.getBalance() << endl;

    // myAccount.balance = 0; // Cannot be accessed directly because it is private.

    // Deposit
    myAccount.deposit(500.0);
    
    // Viewing balance after deposit
    cout << "Your current balance is: " << myAccount.getBalance() << endl;

    // Withdraw
    myAccount.withdraw(300.0);
    
    // Viewing balance after withdrawal
    cout << "Your current balance is: " << myAccount.getBalance() << endl;

    return 0;
}
```

নীরব বুঝতে পারল, ক্লাসে `balance` নামক ভেরিয়েবলটি গোপন রাখা হয়েছে। সেই ভেরিয়েবলকে সরাসরি অ্যাক্সেস করা যায় না। তবে `deposit`, `withdraw`, এবং `getBalance` ফাংশনের মাধ্যমে আমরা এই ডেটার উপর নিয়ন্ত্রণ রাখতে পারি।

শিক্ষক বললেন, "এখন তুমি বুঝতে পারছো যে, এনক্যাপসুলেশন শুধুমাত্র ডেটাকে সুরক্ষিত রাখে না, বরং এটি ডেটার সাথে কাজ করা আরও সহজ করে তোলে। তুমি যদি ক্লাসের বাইরে সরাসরি `balance` পরিবর্তন করতে পারো, তাহলে সেটা হয়তো ভুল তথ্য বা অস্বাভাবিক পরিবর্তন ঘটাতে পারে। কিন্তু আমরা ফাংশনগুলোর মাধ্যমে কেবলমাত্র বৈধ পরিবর্তনগুলো করতে পারি।"

নীরব আনন্দিত হয়ে বলল, "ধন্যবাদ স্যার! এখন আমি এনক্যাপসুলেশন বুঝতে পারছি এবং এর গুরুত্বও বুঝতে পারছি।"

এইভাবে, নীরব এনক্যাপসুলেশনের মাধ্যমে প্রোগ্রামিংয়ের একটি গুরুত্বপূর্ণ ধারণা শিখল এবং তার কোডিং দক্ষতা আরও উন্নত হলো।


#### ডেটা সুরক্ষায় এনক্যাপসুলেশনের ভূমিকা
1. **Private Data Members:** ব্যালেন্স ভ্যারিয়েবলটি **private** হিসেবে ডিফাইন করা হয়েছে। এর মানে হলো, বাইরের কোনো কোড সরাসরি ব্যালেন্স অ্যাক্সেস করতে পারবে না। শুধুমাত্র ক্লাসের অভ্যন্তরীণ মেথডগুলি এটি পরিবর্তন বা অ্যাক্সেস করতে পারবে।
2. **Public Member Functions:** আমাদের কোডে **deposit, withdraw** এবং **getBalance** ফাংশনগুলি **public** হিসেবে ডিফাইন করা হয়েছে। এসব ফাংশন ব্যবহার করে আমরা গ্রাহকের ব্যালেন্স পরিবর্তন বা দেখতে পারি। এটি এনক্যাপসুলেশনের মূল ধারণা, যেখানে বাইরের কোড শুধুমাত্র নির্দিষ্ট মেথড ব্যবহার করতে পারে, কিন্তু ডেটার সরাসরি অ্যাক্সেস বন্ধ থাকে।

#### এনক্যাপসুলেশনের মূল লক্ষ্য:
এনক্যাপসুলেশনের মূল লক্ষ্য হলো ডেটা সুরক্ষা এবং প্রাইভেসি রক্ষা করা। সুতরাং, **কোনো ধরনের ডেটা সদস্যকে public করা উচিত নয়**, কারণ এতে ডেটা সরাসরি পরিবর্তন করা সম্ভব হয়ে পড়ে, যা সুরক্ষিত নয়। তবে, **public** মেথড রাখা যেতে পারে, যা শুধুমাত্র নির্দিষ্ট নিয়ম মেনে ডেটার সঙ্গে কাজ করে।