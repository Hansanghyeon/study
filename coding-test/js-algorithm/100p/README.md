두 개의 정렬된 배열이 동일한 크기일 때 해당 배열들의 중앙값 찾기

집합의 원소 개수가 짝수인 경우 두 개의 중간 숫자가 존재하게 되는데 중앙값은 해당 두 개의 중간 숫자의 평균이라는 점을 기억하자. 배열이 정렬돼 있다면 중앙값을 찾는 것은 간단한다.

`[1,2,3,4]`의 중앙값은 (2+3)/2 = 2.5이다.

```js
function medianOfArray(array) {
  var length = array.length;
  // 홀수
  if (length % 2 === 1) {
    return array[Math.floor(length / 2)];
  } else {
    // 짝수
    return (array[length / 2] + array[length/2 - 1]) / 2;
  }
}
```

이제 중앙값을 찾기 위해 아래 `medianOfTwoSortedArray(arr1, arr2, pos)`와 같이 두 개의 배열을 반복 접근하면서 어느 쪽이 더 큰지 비교할 수 있다. 두 배열이 동일한 크기라면 전체 크기는 짝수가 될 것이다.

두 개의 짝수를 더하든 두 개의 홀수를 더하든 모두 짝수가 되기 때문이다. 이와 관련된 크기라면 전체 크기는 짝수가 될 것이다.

두 개의 짝수를 더하든 두 개의 홀수를 더하든 모두 짝수가 되기 때문이다. 이와 관련된 자세한 사항은 8장을 참고하자.

두 배열이 모두 정렬됐기 때문에 위 함수는 재귀적으로 호출될 수 있다. 함수를 재귀적으로 호출할 때마다 어떤 중앙값이 더 큰지 확인한다.

두 번째 배열의 중앙 값이 더 큰 경우 첫 번째 배열을 반으로 나눈 다음 큰 쪽만 재귀적으로 전달한다.

첫 번째 배열의 중앙값이 더 큰 경우 두 번째 배열을 반으로 나눈 다음 큰 쪽만 재귀적으로 전달한다.

첫 번째 배열의 중앙값이 더 큰 경우 두 번째 배열을 반으로 나눈 다음 큰 쪽이 다음 번 함수 호출 시 첫 번째 매개변수 배열이 된다. 이 함수의 arr2 매개변수가 arr1 매개변수보다 항상 크기 때문이다. 마지막으로 배열의 크기가 짝수인지 홀수인지 확인하기 위해 배열의 크기(매개변수 pos)가 필요하다.

다음 예를 살펴보자.

`array1 = [1,2,3], array2 = [4,5,6]`

여기서 `array1`의 중앙값은 2이고 `array2`의 중앙값은 5이다. 따라서 중앙값은 `[2,3]`과 `[4,5]`내에 존재한다. 네 개의 항목만 남았기 때문에 중앙값은 다음과 같이 계산할 수 있다.

`max(arr1[0], arr2[0]) + min(arr[1], arr2[1]) / 2;`