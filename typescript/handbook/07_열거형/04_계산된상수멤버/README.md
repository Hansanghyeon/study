# 계산된 상수 멤버

각 열거형 멤버에는 constant 또는 computed 중 하나일 수 있는 값이 있습니다.<br/>
열거형 멤버는 다음과 같은 경우 상수로 간주됩니다.

- 열거형의 첫 번째 멤버이며 초기화가 없으면 값이 `0`으로 지정됩니다.
  ```ts
  // E.X는 상수입니다.
  enum E { X }
  ```
- 초기화가 없고 앞의 열거형 멤버가 숫자인 상수입니다.<br/>
  이 경우 이후 나오는 열거형 멤버의 값은 이전 열거형 멤버의 값에 1을 더한 값이 됩니다.
  ```ts
  // E1 및 E2의 모든 열거형 멤버는 상수입니다.
  enum E1 { X, Y, Z}
  enum E2 {
    A = 1, B, C
  }
  ```
- 열거형 멤버는 상수 열거형 표현식으로 초기화됩니다.<br/>
  상수 열거형 표현식은 시간에 완전히 평가될 수 있는 TypeScript의 하위 집합입니다.<br/>
  표현식은 다음과 같은 경우 상수 열거 표현식입니다.
  1. 리터럴 열거 표현식(기본적으로 문자 리털러 또는 숫자 리터럴)
  2. 이전에 정의된 상수 열거형 멤버(다른 열거형에서 올 수 있음)에 대한 참조
  3. 괄호로 묶인 상수 열거형 표현식
  4. 상수, 열거형, 표현식에 적용된 +, -, ~ 단항 연산자 중 하나
  5. +, -, *, /, %, <<, >>, >>>, &, |, ^ 바이너리 연산자에 사용된 열거형 표현식 상수 열거형 표현식이 NaN또는 Infinity로 평가되는 것은 컴파일 타임 에러입니다.

다음 모든 경우에는 열거형 멤버가 계산된(computed)것으로 간주됩니다.

```ts
enum FileAccess {
  // 상수 멤버
  None,
  Read = 1 << 1,
  Write = 1 << 2,
  ReadWrite = Read | Write,
  // 계산된 멤버
  G = '123'.length
}
```