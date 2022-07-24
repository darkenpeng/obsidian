```jsx
//# psudo
    // n = 121 = 11^2
    // return n+1 = 144 = (11+1)^2
    // n = 3
    // return -1

    // 루트 씌웠을 때 정수이면
    // 루트 씌운 숫자에 1을 더해서 (제곱근+1)^2로 리턴 
    // 루트 씌웠을 때 실수이면 -1을 리턴

//# real
function solution(n) {
    if (Number.isInteger(Math.sqrt(n))){
    const target = Math.sqrt(n)
    return Math.pow((target+1), 2);
		} else return -1
}

// # refactor
function solution(n) {
		let answer;    
    const target = Math.sqrt(n)
    if (!Number.isInteger(target)){ //true
			return -1 // 실행
    }
		return Math.pow((target+1), 2);	
}

// # 개선점(이라고 쓰고 마음에 안드는 점)
// if문 -> 삼항연산자로 개선하고 싶다 읽는 사람 입장에서는 가독성이 구릴 수도~
// -> 어떤 경우에는 삼항연산자 ? 모자딥 어떤경우에는 If문이 좋다~ ref 모자딥
// 제곱을 하는 연산자는 없을까? 분명 있을 것 같은데...Math.pow()가 장황함
// -> 이것은 그냥 스타일이다~ 속도가 무엇이 더 빠른지는 (?)

// # 생각해본 것
// answer라는 변수를 선언하고 리턴을 마지막에 해주는 것(처음에 그렇게 구현함)과
// 나의 풀이는 어떤 장단점이 있을까?

// if/else 값을 나눠서 리턴하는 경우에는 굳이 굳이 early return을 굳이 해줄필요가? 왜냐면 가독성이 구려짐~

// 이분탐색이 있다~
```

```jsx
function solution(n) {   
    const target = Math.sqrt(n)
    if (Number.isInteger(target)){
			return Math.pow((target+1), 2);
    }
		return -1
}
```