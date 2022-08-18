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
number의 범위를 초과하면 안되기 때문!'
RangeError: Maximum call stack size exceeded'

```jsx
const cache = []; //[1,1,2,3,5...]
//2^n
function fibo(n) {
	if (n === 1) return 1;
	if (n === 2) return 1;
// cache 배열에 존재하지 않으면
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

```jsx
function solution(n) {
  let a = 1; // 1
  let b = 1; // 2

  for (let i = 2; i < n; i++) {
    const temp = b;
    b = (a + b) % 1234567;
    a = temp;
  }

  return b;
}
```

재귀와 관련된 글

[](https://ko.javascript.info/recursion)[https://ko.javascript.info/recursion](https://ko.javascript.info/recursion)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a09333fc-1f35-4be1-a4a5-3f807a84686a/Untitled.png)