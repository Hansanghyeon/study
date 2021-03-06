# 문자 열거형

문자 열거형은 비슷한 개념이지만 아래에 설명된 것과 같이 약간의 미묘한 실행시 차이가 있습니다.<br/>
문자 열거형에서 각 멤버는 문자 리터럴 또는 다른 문자 열거형 멤버로 상수초기화되어야 합니다.

```ts
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT",
}
```

문자 열거형은 자동 증가 동작을 하지 않지만 문자 열거형은 "직렬화(serialize)"하는 이점이 있습니다.

즉, 디버깅 중이며 숫자 열거형의 런타임 값을 읽어야하는 경우 이 값은 종종 불투명합니다. - 즉, 자체적으로 유용한 의미를 전달하지는 않습니다. (역 매핑이 도움이 될 것입니다)<br/>
문자 열거형을 사용하면 열거형 멤버 자체의 이름과 독립적으로 코드가 실행될 떄 의미가 있고 읽기 쉬운 값을 제공합니다.