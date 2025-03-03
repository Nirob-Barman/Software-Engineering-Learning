# গল্প: "পলিমরফিজমের জাদু" ✨

নীরব একদা ক্যালকুলেটরে যোগ করতে গিয়ে লক্ষ্য করল, এটি **নানা ধরনের সংখ্যার যোগফল সঠিকভাবে বের করতে পারছে**। এমনকি যখন **বিভিন্ন ধরনের সংখ্যা একসাথে যোগ করা হতো**, তখনও এটি **সঠিক ফলাফল প্রদান করত**।

সে দুটি **পূর্ণসংখ্যা** `৫` এবং `১০` যোগ করতে চেয়েছিল, তাই সে ক্যালকুলেটরটিতে সেই দুটি সংখ্যা দিয়ে যোগফল বের করল। ক্যালকুলেটরটি **সঠিকভাবে `১৫` বলে দিল**।  

এরপর নীরব কিছু **দশমিক সংখ্যা** নিয়ে পরীক্ষা করল—যেমন `৫.৫` এবং `১০.৫` যোগ করতে। ক্যালকুলেটর আবার **সঠিকভাবে `১৬.০` বলল**। নীরব ভাবল, "অদ্ভুত! কিভাবে এটি একই ক্যালকুলেটর দিয়ে দুটি ভিন্ন ধরনের সংখ্যা যোগ করতে পারছে?"

অবশেষে, নীরব বুঝতে পারল এটি আসলে **পলিমরফিজম**—এটি একটি **জাদু**, যা **কম্পিউটার প্রোগ্রামিংয়ের একটি গুরুত্বপূর্ণ ধারণা**। পলিমরফিজমের মাধ্যমে একাধিক ফাংশন একই নাম ব্যবহার করলেও তাদের মধ্যে বিভিন্ন ধরনের কাজ হতে পারে, এবং সেই অনুযায়ী বিভিন্ন ধরনের ইনপুট গ্রহণ করতে পারে।

নীরব বুঝল যে, তার ক্যালকুলেটরটি একে একে **তিনটি আলাদা পদ্ধতিতে কাজ করেছিল**:

1. **পূর্ণসংখ্যার যোগ**: যখন দুটি পূর্ণসংখ্যা(integer number) যোগ করা হয়, তখন `add(int a, int b)` ফাংশন কাজ করত।
2. **দশমিক সংখ্যার যোগ**: যখন দুটি দশমিক সংখ্যা(floating point number) যোগ করা হয়, তখন `add(float a, float b)` ফাংশন কাজ করত।
3. **মিক্সড সংখ্যার যোগ**: যখন একটি পূর্ণসংখ্যা(integer) এবং একটি দশমিক সংখ্যা(floating point number) যোগ করা হয়, তখন `add(int a, float b)` ফাংশন কাজ করত।

এই পলিমরফিজমের কারণে, একটাই `add()` নামের ফাংশন দিয়ে তিনটি ভিন্ন ধরণের যোগফল বের করা সম্ভব হয়েছিল।

### C++ কোড উদাহরণ:

```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    // Method for adding integers
    int add(int a, int b) {
        return a + b;
    }
    
    // Method for adding floating point numbers
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
    cout << "Decimal sum: " << calc.add(5.5, 10.5) << endl;  // Floating point number addition
    cout << "Mixed sum (integer + decimal): " << calc.add(5, 10.5) << endl; // Mixed addition

    return 0;
}
```
### আউটপুট:

```
Integer sum: 15
Decimal sum: 16
Mixed sum (integer + decimal): 15.5
```