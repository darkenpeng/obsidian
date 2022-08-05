```jsx
function solution(s) {
    const regex = /^[a-zA-Z]*$/; 
    const word = s.split(' ').map((word)=> word.slice(1).toLowerCase())
    const capital = s.split(' ').map((c,i)=> c[0].replace(regex, c[0].toUpperCase()))
        
    return capital.map((c,i)=> c + word[i]).join(' ')
}
```

```jsx
테스트 1 〉	통과 (0.29ms, 30.1MB)
테스트 2 〉	실패 (런타임 에러)
테스트 3 〉	통과 (0.55ms, 30.2MB)
테스트 4 〉	실패 (런타임 에러)
테스트 5 〉	실패 (런타임 에러)
테스트 6 〉	통과 (0.21ms, 30.1MB)
테스트 7 〉	통과 (0.20ms, 30.2MB)
테스트 8 〉	실패 (런타임 에러)
테스트 9 〉	실패 (런타임 에러)
테스트 10 〉	통과 (0.34ms, 30.2MB)
테스트 11 〉	실패 (런타임 에러)
테스트 12 〉	실패 (런타임 에러)
테스트 13 〉	실패 (런타임 에러)
테스트 14 〉	실패 (런타임 에러)
테스트 15 〉	통과 (0.32ms, 30.2MB)
테스트 16 〉	통과 (0.28ms, 30.1MB)
테스트 17 〉	실패 (런타임 에러)
테스트 18 〉	통과 (0.31ms, 30.2MB)
```

# 2

```jsx
function solution(s) {
    const ASCII = 65;
    const sent = s.split(' ')

    const stack = [];
    for(const word of sent){
        if(ASCII > word.charCodeAt(0)){
            word.toLowerCase()
        }
        stack.push(word[0].toUpperCase()+word.slice(1).toLowerCase())

    }
    return stack.join(' ')

}
```

```jsx
테스트 1 〉	통과 (0.07ms, 29.9MB)
테스트 2 〉	실패 (런타임 에러)
테스트 3 〉	통과 (0.08ms, 30.2MB)
테스트 4 〉	실패 (런타임 에러)
테스트 5 〉	실패 (런타임 에러)
테스트 6 〉	통과 (0.08ms, 30.2MB)
테스트 7 〉	통과 (0.13ms, 29.9MB)
테스트 8 〉	실패 (런타임 에러)
테스트 9 〉	실패 (런타임 에러)
테스트 10 〉	통과 (0.07ms, 30.3MB)
테스트 11 〉	실패 (런타임 에러)
테스트 12 〉	실패 (런타임 에러)
테스트 13 〉	실패 (런타임 에러)
테스트 14 〉	실패 (런타임 에러)
테스트 15 〉	통과 (0.16ms, 30.1MB)
테스트 16 〉	통과 (0.09ms, 30.3MB)
테스트 17 〉	실패 (런타임 에러)
테스트 18 〉	통과 (0.14ms, 30.1MB)
```

# 3
런타임 에러 왜나는지 찾다가 정답을 발견함
[](https://school.programmers.co.kr/questions/27700)[https://school.programmers.co.kr/questions/27700](https://school.programmers.co.kr/questions/27700)
```jsx
function solution(s) {
//word[0]은 빈 문자열을 만나면 undefined를,  word.charAt(0)은 빈 문자열을 만나면 빈 문자열을 반환한다.
    return s.split(' ').map((c)=> c.charAt(0).toUpperCase()+c.substring(1).toLowerCase()).join(' ')
}
```

# 4(너무느림!)

```jsx
function solution(s) {
    const regex = /^[a-zA-Z]*$/; 
    const word = s.split(' ').map((word)=> word.slice(1).toLowerCase())
    const capital = s.split(' ').map((c,i)=> c.charAt(0).replace(regex, c.charAt(0).toUpperCase()))
        
    return capital.map((c,i)=> c + word[i]).join(' ')
}
```