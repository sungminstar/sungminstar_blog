---
sidebar_label: "나머지가 1이 되는 수 찾기"
sidebar_position: 1

title: Lv1. 나머지가 1이 되는 수 찾기
authors: sungminstar
tags: [javascript, codingtest]
---

# **Lv1. 나머지가 1이 되는 수 찾기**

## 1. 문제

[[Lv.1] 나머지가 1이 되는 수 찾기](https://school.programmers.co.kr/learn/courses/30/lessons/87389)

---

## 2. 풀이

### 2-1. 내 풀이

```jsx
function solution(n) {
  for (let i = 1; i <= n; i++) {
    if (Math.floor(n % i) === 1) return i;
  }
}
```

### 2-2. 추구미

- 1부터 n까지 반복문 돌리면서 나머지 구하기 ⇒ 나머지가 1인 경우 바로 리턴!

### 2-3. 다른 풀이

```jsx
function solution(n) {
  var answer = 1;
  while (n % answer != 1) answer++;
  return answer;
}
```

- 나랑 비슷한 느낌이지만,, 좀 다른 부분은,,,
  - 나머지가 1이 아닌 경우 while문 돌기
  - 계속 돌다가 while문의 조건문과 어긋나는 상황 바로 반복문 중단 후 해당 값 리턴

---
