```
# 접근

//배열에 다음 숫자를 넣는다
//x부터 x*n까지 n개의 숫자
//배열에 값을 넣는다.
//answer = [2*1, 2*2, 2*3, 2*4, 2*5];
//2를 배열에 넣고 4를 배열에 넣고 6를 배열에 넣고...
//=>loop 배열에 값을 넣는 과정을 반복문으로 돌리면 되겠군!

```

```js
function solution(x, n) { // 2 5

	let startNum = x; // 2
	let endNum = x*n; // 10
	let count = n+1; // 6
	var answer = [];


	// # 구현

	for(let i=1;i<count;i++){
		answer.push(i*x)
	}
	return answer;

}
```

``` js
# 검색
//https://ko.javascript.info/array-methods
//배열의 맨 끝에 값을 추가하는 메서드
//arr.push(...items) – 맨 끝에 요소 추가
//2*1, 2*2, 2*3, 2*4, 2*5
```