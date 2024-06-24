---
sidebar_label: "정수 제곱근 판별"
sidebar_position: 1

title: Lv1. 정수 제곱근 판별
authors: sungminstar
tags: [javascript, codingtest]
---

# **Lv1. 정수 제곱근 판별**

## 1. 문제

[[Lv.1] 정수 제곱근 판별](https://school.programmers.co.kr/learn/courses/30/lessons/12934)

---

## 2. 풀이

### 2-1. 내 풀이

```jsx
function solution(n) {
  return Math.sqrt(n, 2) % 1 == 0 ? Math.pow(Math.sqrt(n, 2) + 1, 2) : -1;
}
```

⇒ 통과된 풀이

n의 제곱근의 제곱이 n과 같은 지 확인하는 부분을 ⇒ n의 제곱근이 정수임을 확인하는 부분으로

수정하니 통과됨,,,

⇒ 뭔 차이일까 왜 통과가 된걸까

1. 아! 내 풀이 오류!
   1. n의 제곱근이 정수가 아님에도 불구하고, 바로 제곱을 해 버리면 정수가 될 때가 있다는 것을 놓쳤다!

### 2-2. 추구미

```jsx
function solution(n) {
  return Math.pow(Math.sqrt(n, 2), 2) == n
    ? Math.pow(Math.sqrt(n, 2) + 1, 2)
    : -1;
}
```

- 삼항연산자 활용
  - n의 제곱근의 제곱을 한 수가 n과 같으면
    - n+1의 제곱을 한 값을 반환
    - 그게 아니라면 -1 반환
- 결과: 실패?!?!?

### 2-3. 다른 풀이

```jsx
function nextSqaure(n) {
  var result = 0;

  if (Number.isInteger(Math.sqrt(n))) {
    return Math.pow(Math.sqrt(n) + 1, 2);
  } else {
    return -1;
  }
}
```

- isInteger() 함수를 쓸 수도 있겠구나!

---

## 3. TIL

### 3-1. Number.isInteger()

**`Number.isInteger()`** 메서드는 주어진 값이 정수인지 판별합니다.

```jsx
Number.isInteger(value);
```

- 매개변수
  [`value`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number/isInteger#value)정수인지 확인하려는 값.
- 반환값
  주어진 값의 정수 여부를 나타내는 [`Boolean`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Boolean).
