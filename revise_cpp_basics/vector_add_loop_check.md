```CPP
#include <windows.h>
#include <iomanip>
#include <iostream>
#include <vector>

int main() {
  SetConsoleOutputCP(CP_UTF8);
  std::vector<int> list{};
  char select{};
  std::cout << std::fixed << std::setprecision(2);

  do {
    std::cout << "\nP：顯示所有元素\n"
              << "A：新增元素（不允許重複）\n"
              << "M：顯示所有元素的平均值\n"
              << "S：顯示最小元素\n"
              << "L：顯示最大元素\n"
              << "W：搜索某個元素是否存在\n"
              << "C：清空內容\n"
              << "Q：離開程式\n";

    std::cin >> select;

    switch (select) {
      case 'P':
      case 'p': {
        bool first{};
        if (!list.empty()) {
          std::cout << "[";
          for (auto index : list) {
            if (first) {
              std::cout << ",";
            }
            first = true;
            std::cout << index;
          }
          std::cout << "]";
        } else {
          std::cout << "[]：列表為空！";
        }
      } break;

      case 'A':
      case 'a': {
        unsigned int item{};
        int elem{};
        bool duplicate{};
        std::cout << "\n請輸入要新增的元素數量：";
        std::cin >> item;

        for (unsigned int count{}; count < item;) {
          std::cout << "\n請輸入要新增的元素：";
          std::cin >> elem;
          duplicate = false;

          for (auto value : list) {
            if (value == elem) {
              duplicate = true;
              break;
            }
          }
          if (duplicate) {
            std::cout << "\n元素 " << elem
                      << " 已經存在於列表中，無法重複新增，請重新輸入！\n";
          } else {
            std::cout << "元素：" << elem << "已新增\n";
            list.push_back(elem);
            ++count;
          }
        }
      } break;

      case 'M':
      case 'm': {
        double sum{};

        if (!list.empty()) {
          for (auto value : list) {
            sum += value;
          }
          std::cout << "平均值是： " << sum / list.size() << "\n";
        }

        else {
          std::cout << "內容為空，無法計算平均值\n";
        }
      } break;

      case 's':
      case 'S': {
        if (!list.empty()) {
          int min = list.at(0);  // 保证 list 不为空后再访问
          for (auto value : list) {
            if (min > value) {
              min = value;
            }
          }
          std::cout << "最小值是： " << min << "\n";
        } else {
          std::cout << "內容為空，無法查詢最小值\n";
        }
      } break;

      case 'l':
      case 'L': {
        if (!list.empty()) {
          int max = list.at(0);
          for (auto value : list) {
            if (max < value) {
              max = value;
            }
          }
          std::cout << "最大值是： " << max << "\n";
        } else {
          std::cout << "內容為空，無法查詢最大值\n";
        }

      } break;

      case 'w':
      case 'W': {
        int search{};
        std::cout << "請輸入要搜尋的元素：\n ";
        std::cin >> search;

        if (!list.empty()) {
          bool found = false;
          for (size_t i = 0; i < list.size(); ++i) {
            if (search == list[i]) {
              std::cout << search << " 確實存在於索引 " << i << "\n";
              found = true;
              break;
            }
          }
          if (!found) {
            std::cout << search << " 不存在於列表中\n";
          }
        } else {
          std::cout << "列表為空，無法進行搜尋\n";
        }
      } break;

      case 'c':
      case 'C': {
        list.clear();
        list.shrink_to_fit();
      } break;

      case 'Q':
      case 'q':
        std::cout << "GoodBye！\n";
        break;
      default: {
        std::cout << "未知選擇，請重新輸入！\n";
        break;
      }
    }
  } while (select != 'q' && select != 'Q');
  return 0;
}
```