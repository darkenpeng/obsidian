```jsx
function solution(s) {
    // 내림차순의 의미 = ASCCI 큰 것부터 작은 순으로 정렬해라?
    // sort의 기준 = ASCII임을 확인함
    return s.split('').sort().reverse().join('');
}
```