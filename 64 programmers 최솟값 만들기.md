```jsx
function solution(A,B){
	// 여기서 sum해주려고 했는데 실패해서 걍 for문 돌림 ㄱ- reduce와 index를 요리조리 하면 될거같은데 아놩
	const answer= A.sort((a,b)=> a-b).map((a,i)=> B.sort((a,b)=> b-a).map((b,j)=> a*b))
	
	let sum = 0

	for(let i = 0; i<answer.length;i++){
     sum += answer[i][i]
	}
	return sum
}
```

```jsx
정확성  테스트
테스트 1 〉	통과 (0.07ms, 30.1MB)
테스트 2 〉	통과 (0.78ms, 30.1MB)
테스트 3 〉	통과 (0.77ms, 30.2MB)
테스트 4 〉	통과 (0.78ms, 30.1MB)
테스트 5 〉	통과 (0.77ms, 30.1MB)
테스트 6 〉	통과 (0.78ms, 30MB)
테스트 7 〉	통과 (0.77ms, 30.1MB)
테스트 8 〉	통과 (0.77ms, 30.1MB)
테스트 9 〉	통과 (0.76ms, 30.2MB)
테스트 10 〉	통과 (0.77ms, 29.9MB)
테스트 11 〉	통과 (0.31ms, 30.1MB)
테스트 12 〉	통과 (0.28ms, 30.1MB)
테스트 13 〉	통과 (0.30ms, 30.1MB)
테스트 14 〉	통과 (0.45ms, 30MB)
테스트 15 〉	통과 (0.32ms, 30MB)
테스트 16 〉	통과 (0.31ms, 29.9MB)
효율성  테스트
테스트 1 〉	실패 (시간 초과)
테스트 2 〉	실패 (시간 초과)
테스트 3 〉	실패 (시간 초과)
테스트 4 〉	실패 (시간 초과)
// 실패 ! ㅋㅋ
```

# 수정함

```jsx
function solution(A,B){
    A.sort((a,b)=> a-b)
    B.sort((a,b)=> b-a)
	  let sum = 0;

    for(let i = 0; i < A.length ; i++){
       sum += A[i]*B[i]
    }
		return sum
}
```