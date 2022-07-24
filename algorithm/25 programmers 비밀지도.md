## 1트

```jsx
// # psudo
//    지도 1 array item을 이진수로 치환하는 방법?-> 0은 공백, 1은 #으로 치환.
//    지도 2 array item을 이진수로 치환?-> 0은 공백, 1은 #으로 치환
//    합집합처럼 지도 1과 지도 2를 더한다 ~ 배열을 합치는 메서드? 배열 두개를 더해야? 
//	  근데 문제가 자릿수가 다르잖아 이게되나?

function solution(n, arr1, arr2) {
   const convertToBinary = (arrName)=> {
        return arrName.map(i=>i.toString(2).padStart(n,'0'))
    }
   
const binaryArr1 = convertToBinary(arr1)
const binaryArr2 = convertToBinary(arr2)

//문자열이어서 비트연산이 안되는 줄 알았는데 자릿수때문에 안되는거였다! (<<이게틀린듯...?)
//그럼 앞에다가 0을 추가해줘서 자릿수를 맞춰주면 될텐데...
//자바스크립트 자릿수 맞추기 검색 => .padStart
//실험~

console.log(binaryArr1) // [ '01001', '10100', '11100', '10010', '01011' ]
console.log(binaryArr2) // [ '11110', '00001', '10101', '10001', '11100' ]

    //여기서 for문으로 구현해봤는데 안되는것임..그래서 다 찍어봄
    console.log(binaryArr1[0] | binaryArr2[0]) // 11247 ?????
    console.log(binaryArr1[1] | binaryArr2[1]) // 10101
    console.log(binaryArr1[2] | binaryArr2[2]) // 12157 ?????
    console.log(binaryArr1[3] | binaryArr2[3]) // 10011
    console.log(binaryArr1[4] | binaryArr2[4]) // 11263 ?????

 // # 질문 ?????한 부분은 이진수 OR 연산이 왜 안되나요...?
    //-> 순서가 틀렸음다 저 toString으로 이진수로 변환한 이상 item의 타입은 number가 아니라 string이기 때문에 
// OR 연산자가 안먹는다 ~
// 그렇다면 or 연산자의 피연산자는 반드시 number 타입 이어야하는지? no~ boolean SSAP가넝~
    
// (됐다고 가정하면 arr1과 2의 합집합스러운 (...) 하나의 배열이 만들어짐)
// 그 배열의 이름을 unionArr라고 가정
// 검색 문자열을 특정 문자열로 변환 -> <https://powerku.tistory.com/130>
// map으로 replace를 해주면되지않을까?
// string.replace(0, "")
// string.replace(1,"#")

// return unionArr.map(i=>i.replace('0',"").replace('1',"#")
}
```

## 2트

```jsx
function solution(n, arr1, arr2) {
const unionArr = Array.from(arr1, (v,i)=> v | arr2[i])
//(자아비판) 이거 여기서 바로 return하는거랑 머선차이가있나요? 별로없을듯..걍 간지인가
// 걍 answer라고 붙여주고 싶었슴다
// 스타일이다~(이불교수님)
// lint?(디스캣 교수님)가 경고를 해준다~
// IDE가 걸러줄수도있다~
// 구현할 때는 콘솔로 찍고~ 그다음 한줄리턴으로 리팩토링하자~
    const answer = unionArr.map(i=>i.toString(2)
													 .padStart(n,'0')
													 .replace(/1/g,"#")
													 .replace(/0/g, " "))
    return answer
```