220331
```jsx

// # input 1을 통과하지 못함
function solution(arr, divisor) {
    // 에러 처리시 -1 리턴하기로 조건에 적혀 있음
    const exceptionArr = [-1]
    const divArr= arr.filter(num => num % divisor == 0)
    return divArr.length !== 0 ? divArr.sort() : exceptionArr
}
//sort()의 매개변수로 compareFunction을 넣어주지 않아서 10이 5보다 앞에 온다!
// <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort>
```

```jsx
// 수정 후
function solution(arr, divisor) {
    // 에러 처리시 -1 리턴하기로 조건에 적혀 있음
    const exceptionArr = [-1]
    const divArr= arr.filter(num => num % divisor == 0)
    return divArr.length !== 0 ? divArr.sort((a, b)=> a - b) : exceptionArr
}

```
