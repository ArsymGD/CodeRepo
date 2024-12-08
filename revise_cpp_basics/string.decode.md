```CPP
#include <windows.h>

#include <iostream>
#include <string>

int main() {
  const std::string alphabet =
      "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789 !\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~";
  const std::string key =
      "ZYXWVUTSRQPONMLKJIHGFEDCBAzyxwvutsrqponmlkjihgfedcba9876543210~}|[]\\^_`{>?!:;/,.()+&%'$#\" \" ";

  std::string message;
  std::cout << "輸入你的訊息: ";
  std::getline(std::cin, message);

  std::string enc_msg;
  for (char ch : message) {
    size_t pos = alphabet.find(ch);
    if (pos != std::string::npos) {
      enc_msg += key[pos];
    } else {
      enc_msg += ch;
    }
  }
  std::cout << "加密後的訊息: " << enc_msg << "\n";

  std::string dec_msg;
  for (char ch : enc_msg) {
    size_t pos = key.find(ch);
    if (pos != std::string::npos) {
      dec_msg += alphabet[pos]; 
    } else {
      dec_msg += ch;
    }
  }
  std::cout << "解密後的訊息: " << dec_msg << "\n";

  return 0;
}
```