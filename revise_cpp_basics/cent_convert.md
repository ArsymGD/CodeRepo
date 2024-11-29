```cpp

#include <iostream>

int main()
{
    int cent {};
    const int dollars_value {100}, quarters_value {25}, dimes_value {10}, nickels_value {5};
    
    std::cout << "請輸入美分金額" << "\n";
    std::cin >> cent;

    int balance{}, dollars{}, quarters {}, dimes{}, nickels{}, pennies{};

    dollars = cent / dollars_value;
    balance = cent % dollars_value;

    quarters = balance / quarters_value;
    balance %= quarters_value;

    dimes = balance / dimes_value;
    balance %= dimes_value;

    nickels = balance / nickels_value;
    balance %= nickels_value;

    pennies = balance;


    std::cout << "dollars:" << dollars << "\n";
    std::cout << "quarters:" << quarters << "\n";
    std::cout << "dimes:" << dimes << "\n";
    std::cout << "nickels:" << nickels << "\n";
    std::cout << "pennies:" << pennies << "\n";

    return 0;
}

```