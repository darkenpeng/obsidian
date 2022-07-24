```jsx
//# 1 indexOf
function solution(seoul) {
    //파이썬의 index?
    const index =  seoul.indexOf("Kim")
    const answer = `김서방은 ${index}에 있다`;
    return answer;
}

// #refactor
function solution(seoul) {
return `김서방은 ${seoul.indexOf("Kim")}에 있다`
}
```

```jsx
//# 2 findIndex
function solution(seoul) {
    const index =  seoul.findIndex(e => e === "Kim")
    const answer = `김서방은 ${index}에 있다`;
    return answer;
}
```