---
sidebar_label: "없는 숫자 더하기"
sidebar_position: 1

title: Lv1. 없는 숫자 더하기
authors: sungminstar
tags: [javascript, codingtest]
---

# **Lv1. 없는 숫자 더하기**

## 1. 문제

[[Lv.1] 없는 숫자 더하기](https://school.programmers.co.kr/learn/courses/30/lessons/86051)

---

## 2. 풀이

### 2-1. 내 풀이

```jsx
function solution(numbers) {
  let sum = 0;
  for (let i = 0; i < 10; i++) {
    numbers.includes(i) ? sum : (sum += i);
  }
  return sum;
}
```

### 2-2. 추구미

- String.prototype.substring과 비슷한 메소드를 찾으려고 하였음. MDN 문서 참고.

### 2-3. 다른 풀이

```jsx
function solution(numbers) {
  var answer = 0;
  for (let i = 0; i < 10; i++) {
    if (numbers.indexOf(i) === -1) answer += i;
  }
  return answer;
}
```

- i가 numbers에 있다면 해당 인덱스를 반환하지만, 없다면 -1을 반환함
- -1인 경우는 i가 numbers에 없다는 것이기에 해당 숫자 i를 answer에 더하고 반환

---

## 3. TIL

### 3-1. **Array.prototype.includes()**

- The **`includes()`** method of [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) instances determines whether an array includes a certain value among its entries, returning `true` or `false` as appropriate.

---

- `includes(searchElement)
includes(searchElement, fromIndex)`
- **Parameters**
  - `searchElement`
    The value to search for.
  - `fromIndex`
    OptionalZero-based index at which to start searching, converted to an integer.
- [**Return value**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes#return_value)
  A boolean value which is `true` if the value `searchElement` is found within the array (or the part of the array indicated by the index `fromIndex`, if specified).
  ``

### 3-2. **Array.prototype.indexOf()**

- `Array` 인스턴스의 **`indexOf()`** 메서드는 배열에서 주어진 요소를 찾을 수 있는 첫 번째 인덱스를 반환하고, 찾을 수 없는 경우 -1을 반환합니다.
- `indexOf(searchElement)
indexOf(searchElement, fromIndex)`
- 매개변수
  - `searchElement`
    배열에서 위치를 찾을 요소입니다.
  - `fromIndex` Optional
    검색을 시작할 0 기반 인덱스로, [정수로 변환됩니다](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Number#%EC%A0%95%EC%88%98_%EB%B3%80%ED%99%98).
    • 음수 인덱스는 배열의 끝부터 거꾸로 셉니다. 즉, `fromIndex < 0`이면, `fromIndex + array.length`가 사용됩니다. 그러나, 이 경우에도 배열은 여전히 앞에서 뒤로 검색됩니다.
    • `fromIndex < -array.length`이거나 `fromIndex`가 생략되면, `0`이 사용되어 전체 배열이 검색됩니다.
    • `fromIndex >= array.length` 이면, 배열은 검색되지 않고 `-1`이 반환됩니다.
- 반환 값
  - 배열에서 `searchElement`의 첫 번째 인덱스이고, 찾을 수 없으면 `-1`입니다.
