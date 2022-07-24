```jsx
// 핑수딱 귀여움

// [시간초과!]
// 스스로 생각해 본 이유 : 문법을 찾는 데 시간이 너무 오래 걸렸어요!
// number 타입으로 접근해보려다가 시간이 지체됐어요!

// # psudo
    // n을 number 타입으로 (결국 실패!) 한자리수씩 쪼개서 [1,2,3]
    // 각 자리수끼리 크기를 비교하고 1,2,3 3>2>1
    // 큰 수부터 정렬해서 3,2,1
    // 하나의 값으로 합쳐서 321
    // answer로 리턴 321

// # actual
function solution(n) {
    const str = String(n);
    const strArr = str.split('');
    const numArr = strArr.map(item => Number(item)) // [3,2,1]
    // <https://ko.javascript.info/array-methods#ref-320>
    const minToMax = numArr.sort();
    const maxToMin = minToMax.reverse(); // 한 번에 숫자 비교와 정렬 동시에 하는 함수는 없을까? 
    // # 검색 내림차순
    // items.sort((a, b) => b - a); // [30, 20, 10, 2]
    // join은 배열의 요소를 "하나의 문자열"로 리턴하는데, 숫자로 바로 리턴해주는 함수는 없을까?
    const strAnswer = maxToMin.join('');
    const numAnswer = Number(strAnswer);
    return numAnswer;
}

// # 개선점
// 인생을 이렇게 살아야 하나? 싶었음 굳이 쪼개주고 다시 합치고
// 문자열로 변환했다가 넘버로 타입 바꿔주고
// 스스로 피곤해지는 풀이밖에 없었을까? number로 타입을 유지한 채로 하는 방법은 없었을지.. 아쉽

// # 검색한 문법 토대로 개선
function solution(n) {
const str = String(n);
    const strArr = str.split('');
    const numArr = strArr.map(item => Number(item));
    const maxToMin = numArr.sort((a,b) => b - a);
    const strAnswer = maxToMin.join('');
    const numAnswer = Number(strAnswer);
    return numAnswer;
}

// # 메서드 체이닝 이용해서 수정해보기

```
```jsx
function solution(n) {  // 12345678
	return +(n.toString() // 여기서 문자열 
						.split('')  // 하나 하나 숫자들이 문자로 
						.sort()     // [1,2,3,4,5,6,7,8]
						.reverse()  // [8,7,6,5,4,3,2,1]
						.join('')   // 87654321
					); // +('87654321') ==> 87654321
// 한줄로 return +(n.toString().split('').sort().reverse().join(''));
}


```