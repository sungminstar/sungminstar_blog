---
sidebar_label: "음양 더하기"
sidebar_position: 1

title: Lv1. 음양 더하기
authors: sungminstar
tags: [javascript, codingtest]
---

# **Lv1. 음양 더하기**

## 1. 문제

[[Lv.1] 음양 더하기](https://school.programmers.co.kr/learn/courses/30/lessons/76501)

---

## 2. 풀이

### 2-1. 내 풀이

```jsx
function solution(absolutes, signs) {
  let sign,
    sum = 0;
  for (let i = 0; i < absolutes.length; i++) {
    sign = signs[i] ? 1 : -1;
    sum += sign * absolutes[i];
  }
  return sum;
}
```

### 2-2. 추구미

```jsx
function solution(absolutes, signs) {
  let sum = 0;
  for (let i = 0; i < absolutes.length; i++) {
    sum += absolutes[i] * (signs[i] ? 1 : -1);
  }
  return sum;
}
```

- 하지만,, 너무 직관적이지 않다고 느껴서 sign 변수를 만들어 제출함

### 2-3. 다른 풀이

```jsx
function solution(absolutes, signs) {
  let answer = 0;
  for (let i = 0; i < absolutes.length; i++) {
    signs[i] ? (answer += absolutes[i]) : (answer -= absolutes[i]);
  }
  return answer;
}
```

- 호호,, 부호를 곱하지 않고 그냥 sum에 더하기 빼기를 하면 되는거잖아!

---

## 3. TIL

### 3-1. **Array.length**

- `Array` 인스턴스의 **`length`** 속성은 배열의 길이를 반환합니다. 반환값은 부호 없는 32비트 정수형이며, 배열의 최대 인덱스보다 항상 큽니다. **`length`** 속성에 값을 설정할 경우 배열의 길이를 변경합니다.

### 3-2. **Math.abs()**

- `Math.abs()` 함수는 주어진 숫자의 절대값을 반환합니다. `x`가 양수이거나 0이라면 `x`를 리턴하고, `x`가 음수라면 `x`의 반대값, 즉 양수를 반환합니다.
- 이건 그냥 궁금해서 절대값 메소드도 있을까 해서? 봣더니 있어소
