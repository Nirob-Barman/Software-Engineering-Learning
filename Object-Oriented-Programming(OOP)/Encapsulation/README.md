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

## C++ কোড উদাহরণ:

```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    // Method for adding integers
    int add(int a, int b) {
        return a + b;
    }
    
    // Method for adding doubles
    float add(float a, float b) {
        return a + b;
    }

    // Method for adding mixed types (integer and float)
    float add(int a, float b) {
        return a + b;
    }
};

int main() {
    Calculator calc;

    // Demonstrating the three different types of addition
    cout << "Integer sum: " << calc.add(5, 10) << endl;       // Integer addition
    cout << "Decimal sum: " << calc.add(5.5, 10.5) << endl;  Floating point number addition
    cout << "Mixed sum (integer + decimal): " << calc.add(5, 10.5) << endl; // Mixed addition

    return 0;
}
```
## আউটপুট:
```
Integer sum: 15
Decimal sum: 16
Mixed sum (integer + decimal): 15.5
```