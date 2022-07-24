```jsx
// # psudo
    // p를 포함하는지 판단하는 판별식을 만족하는 배열 리턴
    // 배열의 length끼리 비교
    // 만약 p와 y의 length 모두 0이라면 트루 리턴
    
// # actual
function solution(s){
    
const pASCII = 80;
    const yASCII = 89;
    const strArr = s.toUpperCase().split('')
    const pASCIIArr = strArr.map(e => e.charCodeAt()).filter(e => e=== pASCII)
    const yASCIIArr = strArr.map(e => e.charCodeAt()).filter(e => e=== yASCII)

    return pASCIIArr.length === yASCIIArr.length
}

// # thinking
// 변수명이 구리다...
// 문자열을 char 형태로 비교하는 것과 문자열을 모두 아스키로 치환해서 값을 비교하는 것 둘 중에 뭐가 더 빠를까?
// includes를 사용하는 방법은 없을까?
```