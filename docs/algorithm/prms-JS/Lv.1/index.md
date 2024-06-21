---
sidebar_label: "정수 내림차순으로 배치하기"
sidebar_position: 1

title: Lv1. 정수 내림차순으로 배치하기
authors: sungminstar
tags: [javascript, codingtest]
---

## 1. 문제

[[Lv.1] 정수 내림차순으로 배치하기](https://school.programmers.co.kr/learn/courses/30/lessons/12933)

---

## 2. 풀이

### 2-1. 내 풀이

```javascript
function solution(n) {
  let numTostr = (n + "")
    .split("")
    .map((x) => parseInt(x))
    .sort()
    .reverse();
  let sum = 0;
  for (let i = 0; i < numTostr.length; i++) {
    sum *= 10;
    sum += numTostr[i];
  }
  return sum;
}
```

- TIL 작성 후, 추구미를 반영한 간결한 풀이

```javascript
function solution(n) {
  return Number(
    (n + "")
      .split("")
      .map((x) => parseInt(x))
      .sort((a, b) => b - a)
      .join("")
  );
}
```

### 2-2. 추구미

- 주어진 수를 => 문자로 바꾸어 => 다시 정수로 배열 안에 넣은 수를 가지고
- 오름차순 정렬 후 => 다시 역으로 정렬(내림차순 정렬 완)
- 정수 배열을 반복문으로 돌려가면서 sum에 더하고 곱하기 10을 하면서
- 정수 내림차순으로 배치 완료

> 주어진 수를 다시 문자로 바꾸어 다시 정수로 배열 안에 집어 넣기란,,, 아이디어가 떠오르지 않으면 무리일 듯
> 그리고 한 번에 내림차순 정렬은 어려운 걸까?
> 그리고 이를 정수 배열을 문자 배열로 바꾸어 문자열로 합쳐버리면 안되는건가,,?

### 2-3. 다른 풀이

```javascript
function solution(n) {
  const newN = n + "";
  const newArr = newN.split("").sort().reverse().join("");
  return +newArr;
}
```

- 내가 원하는 바를,,, 명쾌하다
  ㅋㅋㅋ
- 만약, split까지의 과정이 이해가지 않는다면 아래 내용 참고할 것!
  [프로그래머스 Lv.1 "자연수 뒤집어 배열로 만들기"](https://velog.io/@sungmin8453/CodingTest-프로그래머스-Lv.1-자연수-뒤집어-배열로-만들기)
- 숫자 변환 (단항 플러스 연산자 사용)
  최종적으로 생성된 문자열을 +newArr를 통해 숫자로 변환하여 반환합니다.

  ```javascript
  return +newArr;
  ```

---

## 3. TIL

### 3-1. Array.prototype.sort()

- sort() 메서드는 배열의 요소를 적절한 위치에 정렬한 후 그 배열을 반환합니다. 정렬은 stable sort가 아닐 수 있습니다. 기본 정렬 순서는 **문자열의 유니코드 코드 포인트**를 따릅니다. (오름차순, 내림차순 아님 주의!)

```javascript
arr.sort([compareFunction]);
```

- 매개변수
  - **compareFunction Optional**
    - 정렬 순서를 정의하는 함수. 생략하면 배열은 각 요소의 문자열 변환에 따라 각 문자의 유니 코드 코드 포인트 값에 따라 정렬됩니다.
- 반환값
  - 정렬한 배열. 원 배열이 정렬되는 것에 유의하세요. 복사본이 만들어지는 것이 아닙니다.
    > [MDN_sort](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

#### 3-1-1. sort의 기본 정렬 순서는 문자열의 유니코드 코드 포인트를 따른다?

`sort()` 메서드에 대한 설명은 JavaScript에서 배열의 정렬 방법과 그 기본 동작 방식을 이해하는 데 중요합니다. 다음은 해당 설명을 자세히 해석한 내용입니다:

### 기본 정렬 순서: 유니코드 코드 포인트

JavaScript의 `sort()` 메서드는 기본적으로 배열의 요소를 문자열로 변환한 후 유니코드 코드 포인트의 순서에 따라 정렬합니다. 이를 이해하기 위해 몇 가지 개념을 알아야 합니다:

#### 유니코드 코드 포인트

유니코드 코드 포인트는 각 문자가 유니코드 표준에서 가지는 고유한 숫자 값을 의미합니다. 예를 들어, 'A'는 U+0041, 'a'는 U+0061의 유니코드 코드 포인트 값을 가집니다.

#### 문자열 비교

기본적으로 `sort()` 메서드는 배열 요소를 문자열로 변환한 후 각 문자의 유니코드 코드 포인트 값을 비교하여 정렬합니다.

### 예시

기본 `sort()` 메서드의 동작을 예시로 보겠습니다:

```javascript
let arr = ["apple", "Orange", "banana"];
arr.sort();
console.log(arr);
```

이 코드는 다음과 같이 출력됩니다:

```
["Orange", "apple", "banana"]
```

여기서 알파벳 대문자와 소문자가 유니코드 코드 포인트 순서에 따라 정렬된 것을 알 수 있습니다. 대문자가 소문자보다 먼저 오기 때문에 'Orange'가 가장 먼저 오게 됩니다.

#### 숫자 정렬

숫자 배열을 정렬할 때도 기본 `sort()` 메서드는 각 숫자를 문자열로 변환하여 유니코드 코드 포인트 순서대로 정렬합니다. 따라서 숫자를 크기 순서로 정렬하기 위해서는 정렬 기준(compare function)을 제공해야 합니다.

```javascript
let numbers = [10, 2, 30, 4];
numbers.sort();
console.log(numbers);
```

이 코드는 다음과 같이 출력됩니다:

```javascript
[10, 2, 30, 4];
```

이는 숫자를 문자열로 변환하여 정렬했기 때문입니다. 이를 해결하기 위해 정렬 기준 함수를 제공합니다:

```javascript
numbers.sort((a, b) => a - b);
console.log(numbers);
```

이 코드는 다음과 같이 출력됩니다:

```javascript
[2, 4, 10, 30];
```

### 정렬 기준 함수

`sort()` 메서드는 정렬 기준 함수를 인수로 받을 수 있습니다. 이 함수는 두 요소 `a`와 `b`를 비교하여 다음 값 중 하나를 반환해야 합니다:

- `a`가 `b`보다 작으면 음수
- `a`가 `b`보다 크면 양수
- 같으면 0

예를 들어, 숫자를 오름차순으로 정렬하려면 다음과 같이 합니다:

```javascript
let numbers = [10, 2, 30, 4];
numbers.sort((a, b) => a - b);
console.log(numbers);
```

### 요약

- 기본 `sort()` 메서드는 배열의 요소를 문자열로 변환하고 유니코드 코드 포인트 순서에 따라 정렬합니다.
- 기본 정렬은 숫자에 대해서는 예상치 못한 결과를 낳을 수 있으므로, 숫자 배열을 정렬할 때는 정렬 기준 함수를 제공해야 합니다.
- `sort()` 메서드는 stable sort가 아닐 수 있습니다.

이제 `sort()` 메서드와 유니코드 코드 포인트에 따른 정렬 방식에 대해 이해가 되셨을 겁니다.

### 3-2. 오름차순, 내림차순 정렬 방법

### 비교 함수 형식

```javascript
arr.sort((a, b) => {
  // 비교 로직
});
```

- 비교 함수는 다음을 반환합니다:

  - 음수: a가 b보다 앞에 와야 한다.
  - 양수: a가 b보다 뒤에 와야 한다.
  - 0: 순서를 바꾸지 않는다.

#### 3-2-1. 오름차순 정렬 방법

```javascript
numbers.sort((a, b) => a - b);
```

#### 3-2-2. 내림차순 정렬 방법

```javascript
numbers.sort((a, b) => b - a);
```

### 3-3. Array.prototype.join()

- Array 인스턴스의 Join() 메서드는 배열의 모든 요소를 쉼표나 지정된 구분 문자열로 구분하여 연결한 새 문자열을 만들어 반환합니다. 배열에 항목이 하나만 있는 경우, 해당 항목은 구분 기호를 사용하지 않고 반환됩니다.

```javascript
join();
join(separator);
```

- 매개변수
  - separator Optional
    - 배열의 인접한 요소의 각 쌍을 구분하는 문자열입니다. 생략되면 배열 요소는 쉼표(",")로 구분됩니다.
- 반환 값
  - 배열의 모든 요소들을 연결한 하나의 문자열을 반환합니다. 만약 arr.length 가 0이라면, 빈 문자열을 반환합니다. [MDN_join](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

### 3-4. 단항 플러스 연산자

- 단항 더하기 (+)
- 단항 더하기 연산자(+)는 피연산자 앞에 위치하며 피연산자를 평가하지만, 만약 피연산자가 숫자가 아니라면 숫자로 변환을 시도합니다.
  [MDX\_+x](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Unary_plus)
