TypeScript의 고유한 개념중 일부는 타입 레벨에서 JavaScript 객체의 형태를 설명합니다.<br/>
특히 TypeScript에서의 고유한 예로는 '선언 병합'이라는 개념이 있습니다.<br/>
이 개념을 이해하는 것은 기존 JavaScript를 사용할 때 이점을 제공할 것입니다.<br/>
또한 고급 추상화 개념에 대한 문을 열어줍니다.

이 아티클의 목적인 "선언 병합"은 컴파일러가 동일한 이름으로 선언된 두 개의 독립된 선언을 하나의 정의로 병합하는 것을 의미합니다.<br/>
이 병합된 정의에는 원래 선언의 두 가지 기능이 있습니다.<br/>
어떠한 수의 선언이든 병합할 수 있습니다. 단지 두 가지 선언에 제한되지 않습니다.

# 개본 개념

TypeScript에서 선언은 다음 세 가지 중 하나 이상의 엔티티를 생성합니다.네임스페이스, 타입 또는 값 네임스페이스-생성 선언은 점 표기법을 사용하여 접근하는 이름이 포함된 네임스페이스를 생성합니다.<br/>
타입-생성 선언은 다음과 같습니다: 선언된 형태로 표시되고 주어진 이름에 바인딩 되는 타입을 작성합니다.<br/>
마지막으로, 값-생성 선언은 출력된 JavaScript에서 볼 수 있는 값을 만듭니다.

선언 타입 | 네임스페이스 | 타입 | 값
--------- | ------------ | ---- | --
네임스페이스 | X | | X
클래스 | | X | X
열거형 | | X | X
인터페이스 | | X |
타입 별칭 | | X | 
함수 | | | X
변수 | | | X

각 선언으로 생성된 내용을 이해하면 선언 병합을 수행할 때 병합되는 내용을 이해하는 데 도움이 됩니다.