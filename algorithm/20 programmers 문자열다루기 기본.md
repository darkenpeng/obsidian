```jsx
// expression evaluation or연산자작동방식
function solution(s) {
  const numArr = s.split('').map(i => Number(i))
  // numArr.length가 4 또는 6이 아니면 false를 리턴 ->여기서 막힘
  if([4, 6].includes(s.length) && !numArr.includes(NaN)){
    return true;
	}
	return false;
}
```