```jsx
const regex = /^[A-Z]+$/;

function parse(str){
    const input = str.toUpperCase()
    const stack = []

    for(let i = 0; i<input.length;i++){
        const output = input.slice(i,i+2)
        if(output.length == 2 && regex.test(output)){
            stack.push(output)
        }
    }
    return stack
}

function solution(str1, str2) {
    
    const parsed1 = parse(str1)
    const parsed2 = parse(str2)
    if(parsed1.length ===0 && parsed2.length ===0){
        return 65536
    }
    let answer = J(parsed1,parsed2)
    return Math.floor(answer*65536)
}
// 두 글자씩 끊어서 다중집합을 만들 수 있다. 
// {FR, RA, AN, NC, CE}, {FR, RE, EN, NC, CH}
// 교집합은 {FR, NC}, 합집합은 {FR, RA, AN, NC, CE, RE, EN, CH}
// 영문자로 된 글자 쌍만 유효하고, 기타 공백이나 숫자,
// 특수 문자가 들어있는 경우는 그 글자 쌍을 버린다.
// 대문자와 소문자의 차이는 무시
function inter(A,B){ //a,b는 배열
    return A.filter((a)=> B.includes(a))
}

function union(A,B){
    return A.filter(a=> !B.includes(a)).concat(B)
}
function J(a,b){
    return inter(a,b).length / union(a,b).length
}
```