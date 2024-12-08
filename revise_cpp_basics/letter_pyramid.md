```CPP
#include <iostream>
#include <string>

int main() {
  std::string input;
  std::cout << "請輸入字串: ";
  std::getline(std::cin, input);

  int len = input.length();

  for (int row = 0; row < len; row++) {
    int spaces = len - row - 1;
    std::cout << std::string(spaces, ' ');
    for (int letter = 0;letter <= row; letter++) {
      std::cout << input[letter];
    }

    for (int rev_letter = row - 1; rev_letter >= 0; rev_letter--) {
      std::cout << input[rev_letter];
    }
    std::cout << "\n";
  }

  return 0;
}
```