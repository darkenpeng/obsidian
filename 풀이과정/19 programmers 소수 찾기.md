```jsx
// # psudo
    // n = 10
    // 1,2,3,4,5,6,7,8,9,10 (2,3,5,7)
    // [추가!] 1을 제외하고 배열에 넣어야 함 (range가 2부터 시작)    
    // python의 range 함수? n까지 배열에 넣는다.
    // 1부터 10까지 각 숫자들을 소수 판별식에 넣고 소수면 리턴해서 새로운 배열을 filter로 만든 다음, length를 반환
    // 소수 판별식 isPrime 구체화 - 소수란 ? 1과 자기 자신만 나누어 떨어지는 수
    // 각 array의 item을 소수 판별식에 넣는다(그런데 1은 제외)
    // n / array안의 숫자 = 0
    // 10 / 1 = 0
    // 10 / 2 = 0 2를 배열에 넣는다(filter)
    // 10 / 3 != 0 3을 버림
    // ...
    // 10/10 = 0

// # actual
function solution(n) {
 	//소수 판별식
	function isPrime(num){
	  if(num === 2) return true;
	  for(let i = 2; i <= Math.floor(Math.sqrt(num)); i++){
	    if(num % i === 0) return false;
	  }
  return true;
	}
	const range = Array.from({length: n-1}, (v, i) => i+2);
  const result = range.filter(isPrime);
  return result.length
}

// # ref
// Array.filter()
// <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter>
// Array.from
// <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/from>
```

```jsx
테스트 1 〉	통과 (0.27ms, 29.9MB)
테스트 2 〉	통과 (0.33ms, 29.9MB)
테스트 3 〉	통과 (0.30ms, 30MB)
테스트 4 〉	통과 (1.19ms, 32.5MB)
테스트 5 〉	통과 (0.39ms, 30MB)
테스트 6 〉	통과 (4.59ms, 31.8MB)
테스트 7 〉	통과 (2.20ms, 32MB)
테스트 8 〉	통과 (3.19ms, 31.7MB)
테스트 9 〉	통과 (3.65ms, 32MB)
테스트 10 〉	통과 (79.90ms, 34.7MB)
테스트 11 〉	통과 (317.61ms, 40.1MB)
테스트 12 〉	통과 (134.89ms, 34.8MB)
```

```jsx
테스트 1 〉	실패 (시간 초과)
테스트 2 〉	실패 (시간 초과)
테스트 3 〉	실패 (시간 초과)
테스트 4 〉	실패 (시간 초과)
```