---
sidebar_label: "두 정수 사이의 합"
sidebar_position: 1

title: Lv1. 두 정수 사이의 합
authors: sungminstar
tags: [javascript, codingtest]
---

# **Lv1. 두 정수 사이의 합**

## 1. 문제

[[Lv.1] 두 정수 사이의 합](https://school.programmers.co.kr/learn/courses/30/lessons/87389)

---

## 2. 풀이

### 2-1. 내 풀이

```jsx
function solution(a, b) {
  let sum = 0;
  for (let i = a >= b ? b : a; i <= (a >= b ? a : b); i++) {
    sum += i;
  }
  return sum;
}
```

### 2-2. 추구미

```jsx
function solution(a, b) {
    let sum = 0;
    let start, end;
    a >= b ? (start = b end = a) : (start = a end = b);
    for (let i = start ; i <= end ; i++){
        sum += i;
    }
    return sum;
}
```

- 삼항연산자 내에서 변수 초기화를 두 개 동시에는 불가능인 건가?

### 2-3. 다른 풀이

```jsx
function solution(a, b) {
  if (a === b) return a;
  let small = a < b ? a : b;
  let big = a > b ? a : b;
  for (let i = small + 1; i < big + 1; i++) small += i;
  return small;
}
```

- 추구미 이렇게 실현할 수 있을 듯ㅋㅋ

```javascript
function adder(a, b, s = 0) {
  for (var i = Math.min(a, b); i <= Math.max(a, b); i++) s += i;
  return s;
}
```

- Math라이브러리 활용 이것도 좋아보여서

```jsx
function adder(a, b) {
  var result = 0;
  return ((a + b) * (Math.abs(a - b) + 1)) / 2;
}
```

- 호호,,,,,
- 가우스 덧셈 공식(Gaussian Summation Formula),,,
- 수학 공부를 해야겠다라는 생각이 드는 풀이라,,,ㅎㅎㅎ

---

## 3. TIL

### 3-1. Math 라이브러리

- `Math`는 수학적인 연산을 도와주는 유용한 도구들을 제공하는 라이브러리

> 예를 들어, `Math` 객체에는 다음과 같은 메서드가 포함되어 있습니다.

- `Math.min()`: 주어진 숫자 중에서 가장 작은 숫자를 반환합니다.
- `Math.max()`: 주어진 숫자 중에서 가장 큰 숫자를 반환합니다.
- `Math.random()`: 0과 1 사이의 난수를 반환합니다.
- `Math.floor()`: 주어진 숫자 이하의 가장 큰 정수를 반환합니다.
- `Math.ceil()`: 주어진 숫자 이상의 가장 작은 정수를 반환합니다.
- `Math.sqrt()`: 주어진 숫자의 제곱근을 반환합니다.

### 3-2. 가우스 덧셈 공식

- 연속된 정수의 합을 구하는 효율적인 방법
- 공식의 기본 형태

  ```md
  S = n(n + 1) / 2
  ```

  - S : 1 부터 n 까지의 정수의 합 | n은 마지막 정수

- 일반화된 공식
  - 연속된 임의의 두 정수 a와 b 사이의 합을 구하는 데도 사용 가능
    ```
    S = (a + b)(|a - b| + 1) / 2
    ```
