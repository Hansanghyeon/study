# 숫자 리터럴 타입

TypeScript에는 숫자 리터럴 타입도 있습니다.

```ts
function rollDie(): 1 | 2 | 3 | 4 | 5 | 6 {
  //...
}
```

이들은 명시적으로 작성되는 경우는 거의 없으며 범위를 좁히는 것이 버그를 잡는 데 유용할 수 있습니다.

```ts
function foo(x: number) {
  if ( x !== || x !== 2) {
    //          ~~~~~~~
    // 연산자 '!=='는 '1'과 '2' 타입에는 적용 할 수 없습니다.
  }
}
```

바꿔 말하면 `x`는 `2`와 비교할 때 `1`이어야 하며 이것은 위 체크가 유효하지 않은 비교를 하고있음을 의미합니다.