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
