# 재귀로 풀기
```js
function fibo(n) {
	
	if (n === 1) return 1;
	if (n === 2) return 1;
	return (fibo(n - 2) + fibo(n - 1)) % 1234567;

}

  

function solution(n) {
	return fibo(n);
}
```



# memoization으로 풀기
```js
const cache = [];

function fibo(n) {

	if (n === 1) return 1;
	if (n === 2) return 1;
	if (cache[n] === undefined) {
		cache[n] = (fibo(n - 2) + fibo(n - 1)) % 1234567;
	}
	return cache[n];
}

  

function solution(n) {

	for (let i = 3; i < n; i++) {
		fibo(i);
	}
	return fibo(n);
}
```


# %1234567해주는 이유
number의 범위를 초과하면 안되기 때문!
