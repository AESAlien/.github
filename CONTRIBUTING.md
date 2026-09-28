# 코딩 컨벤션

## 브랜치 규칙

작업 브랜치는 `<유형>/<이슈 번호>-<이슈 내용>` 형식으로 만듭니다.

| 유형 | 예시 |
| --- | --- |
| `feature` | `feature/123-search` |
| `fix` | `fix/124-empty-input` |
| `task` | `task/125-coding-conventions` |

- 작업에 해당하는 이슈를 생성하거나 기존 이슈를 확인한 뒤 브랜치를 만듭니다.
- 이슈 번호는 `#` 없이 숫자만 사용합니다.
- 이슈 내용은 핵심을 나타내는 짧은 명사형으로 작성합니다.
- 이슈 내용은 영문 소문자와 숫자로 작성하고, 단어 사이는 하이픈(`-`)으로 구분합니다(`kebab-case`).

## 명명 규칙

| 대상 | 규칙 |
| --- | --- |
| 클래스 | `PascalCase` |
| 구조체 | `PascalCase` |
| enum 타입 | `PascalCase` |
| enum 값 | `PascalCase` |
| 함수/메서드 | `camelCase` |
| 지역 변수 | `camelCase` |
| 매개변수 | `camelCase` |
| 상수 (`const`, `constexpr`) | `camelCase` |
| private 멤버 변수 | `camelCase_` |
| namespace | `snake_case` |
| 파일/디렉터리 | `snake_case` |

## 코드 서식 (Microsoft 스타일)

```cpp
#include <algorithm>
#include <iostream>
#include <string>
#include <vector>

class NumberPrinter
{
public:
    void print(
        const std::vector<int>& values,
        const std::string& title,
        int minimumValue) const
    {
        if (values.empty())
        {
            std::cout << "No numbers" << '\n';
            return;
        }

        std::cout << title << '\n';
        for (std::size_t index = 0; index < values.size(); ++index)
        {
            int value = std::max(values[index], minimumValue);
            int remainder = value % 2;

            switch (remainder)
            {
            case 0:
                std::cout << "Even: ";
                break;
            default:
                std::cout << "Odd: ";
                break;
            }

            std::cout << value << separator_;
        }
    }

private:
    char separator_ = '\n';
};

int main()
{
    const std::vector<int> values = {1, 2, 3};
    NumberPrinter printer;
    printer.print(
        values,
        "Example numbers",
        0);

    return 0;
}
```
