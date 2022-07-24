```jsx
function solution(num) {
    let answer = '';
    const div = num%2;
    
    //짝수이면 "Even";
    //홀수이면 "Odd";
    
    if(div==0){
        answer="Even";
    }else {
        answer="Odd";
    }
    return answer;
}

// if문을 사용하시려면
// const div = num%2;
// if(div===0) return "Even"
// return "Odd"
// 요렇게 쓰시면 깔끔합니다.
// 요점은 else가 필요가 없다는 점!

// 핑구님 코드를 살리려면
// let answer = "Odd"
// if(div===0) answer = "Even"
// return answer
// 이렇게도 가능해요.

// early return 조기 반환
```