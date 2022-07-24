```jsx
function solution(arr) {
    const n = arr.length;
		//문법 몰라서 찾아보았어요
		//https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce
    
		//변수명 거지같음
		const plus = (a,b) => a+b;
    const total = arr.reduce(plus);
    const average = total / n;

    return average;
}
```

```jsx
function solution(arr){
  let sum = 0;
  for (let i =0; i < arr.length; i++){
    sum += arr[i];
  }
  return sum / arr.length;
}
```