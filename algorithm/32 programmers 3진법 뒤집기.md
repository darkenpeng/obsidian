```jsx
// const arr = [
//              3**0*strArr[reverseIdx],
//              3**1*strArr[reverseIdx-1],
//              3**2*strArr[reverseIdx-2],
//              3**3*strArr[reverseIdx-3],
//              3**4*strArr[reverseIdx-4]
//            ];

function sum(arr) {
    return arr.reduce((a,b)=>a+b,0)
}

function solution(n) {
    const digit3= n.toString(3).split('')
    const strArr = digit3.reverse().map(num => parseInt(num))
    const lastIdx = digit3.length-1 // index가 0이기 때문에
        return sum(strArr.map((e,i)=> 3**i*strArr[lastIdx-i]))
}
```

```jsx
// # [refactor]
// # 곱하기의 피연산자가 하나라도 숫자인 경우 자동 형변환 by 디교수님
function solution(n) { // 7
    return n.toString(3) // '21'
            .split('') // ['2', '1']
            .map((e,i)=> 3**i*e) // [3**0*2, 3**1]
            .reduce((a,b)=>a+b,0)
}
```