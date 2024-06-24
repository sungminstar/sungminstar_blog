---
sidebar_label: "x만큼 간격이 있는 n개의 숫자"
sidebar_position: 1

title: Lv1. x만큼 간격이 있는 n개의 숫자
authors: sungminstar
tags: [javascript, codingtest]
---

# **Lv1. x만큼 간격이 있는 n개의 숫자**

## 1. 문제

[[Lv.1] x만큼 간격이 있는 n개의 숫자](https://school.programmers.co.kr/learn/courses/30/lessons/12954)

---

## 2. 풀이

### 2-1. 내 풀이

```jsx
function solution(x, n) {
  let answer = [];
  for (let i = 1; i <= n; i++) {
    answer.push(x * i);
  }
  return answer;
}
```

### 2-2. 추구미

- 정수 배열에 조건에 따라 push 하기

### 2-3. 다른 풀이

```jsx
function solution(x, n) {
  return Array(n)
    .fill(x)
    .map((v, i) => (i + 1) * v);
}
```

- 배열 리스트를 x로 채워 넣은 뒤 ⇒ 곱하기!
- `Array(n)`: 길이가 `n`인 배열을 생성합니다. 이 배열은 초기에는 빈 슬롯을 가지고 있습니다.
- `.fill(x)`: 생성된 배열의 모든 요소를 `x`로 채웁니다. 이제 배열의 모든 요소는 `x` 값을 가지게 됩니다.
- `.map((v, i) => (i + 1) * v)`: 배열의 각 요소에 대해 매핑 함수를 실행합니다. 이 함수는 각 요소와 그 인덱스를 받아서 새로운 값을 반환합니다. 여기서 `v`는 현재 요소의 값이고, `i`는 현재 요소의 인덱스입니다. `(i + 1) * v`는 인덱스에 1을 더한 값과 현재 요소의 값을 곱한 값을 반환합니다.

---

## 3. TIL

### 3-1. **Array() 생성자**

- **`Array()`** 생성자는 새로운 [`Array`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array) 객체를 생성할 때 사용합니다.

### 3-2. **Array.prototype.fill()**

- [`Array`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array) 인스턴스의 **`fill()`** 메서드는 배열의 인덱스 범위 내에 있는 모든 요소를 정적 값으로 변경합니다. 그리고 수정된 배열을 반환합니다.

```jsx
fill(value);
fill(value, start);
fill(value, start, end);
```

- [매개변수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/fill#%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98)
  - [`value`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/fill#value)
    - 배열을 채울 값입니다. 배열의 모든 요소는 정확히 이 값이 될 것입니다. `value`가 객체인 경우, 배열의 각 슬롯은 해당 객체를 참조합니다.
  - [`start`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/fill#start) Optional
    - 채우기를 시작할 0 기반 인덱스로, [정수로 변환](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number#%EC%A0%95%EC%88%98_%EB%B3%80%ED%99%98)됩니다.
      • 음수 인덱스는 배열의 끝부터 거꾸로 셉니다. `start < 0`인 경우, `start + array.length`가 사용됩니다.
      • `start < -array.length` 또는 `start`가 생략된 경우, `0`이 사용됩니다.
      • `start >= array.length`이면, 아무 인덱스도 채워지지 않습니다.
  - [`end`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/fill#end) Optional
    - 채우기를 끝낼 0 기반 인덱스로, [정수로 변환](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number#%EC%A0%95%EC%88%98_%EB%B3%80%ED%99%98)됩니다. `fill()`은 `end`까지 채우며, `end`는 포함하지 않습니다.
      • 음수 인덱스는 배열의 끝부터 거꾸로 셉니다. `end < 0`인 경우, `end + array.length`가 사용됩니다.
      • `end < -array.length` 이면, `0`이 사용됩니다.
      • `end >= array.length` 이거나 `end`가 생략된 경우, `array.length`가 사용되어 끝까지 모든 인덱스가 채워집니다.
      • `end`가 정수로 변환된 후, `after`보다 앞에 위치하면, 아무 인덱스도 채워지지 않습니다.
- [반환 값](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/fill#%EB%B0%98%ED%99%98_%EA%B0%92)
  - `value`로 채워진 변경된 배열입니다.

### 3-3. **Array.prototype.map()**

- **`map()`** 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환합니다.

```jsx
    arr.map(callback(currentValue[, index[, array]])[, thisArg])
```

- [매개변수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map#%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98)
  - [`callback`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map#callback)
    - 새로운 배열 요소를 생성하는 함수. 다음 세 가지 인수를 가집니다.
    - [`currentValue`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map#currentvalue)
      - 처리할 현재 요소.
    - [`index`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map#index) Optional
      - 처리할 현재 요소의 인덱스.
    - [`array`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map#array) Optional
      - `map()`을 호출한 배열.
  - [`thisArg`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map#thisarg) Optional
    - `callback`을 실행할 때 `this`로 사용되는 값.
- [반환 값](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map#%EB%B0%98%ED%99%98_%EA%B0%92)

  - 배열의 각 요소에 대해 실행한 `callback`의 결과를 모은 새로운 배열.
