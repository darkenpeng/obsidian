```jsx
// 접근이 훈늉한 핑구님! 거의 다 풀었음! 

//시간 초과!
function solution(n)
{
    // 자릿수 구하기 : '' 기준으로 쪼개서
    const str = String(n); // 123
    const num = str.split(''); // ['1','2','3']

		//number map parseInt
    // 더하기 : 배열의 index를 활용하는 방법 reduce?
    // <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce>
		const sum = num.reduce((a, b) => a + b);
    console.log(sum) // 987

		/*
    왜 덧셈이 안될까? 왜냐면 지금 num이라는 배열의 item들은 string 형태로 들어가 있기 때문에 
		더하기 연산이 되는 것이 아니라 숫자를 나열하는 형태로 출력되는 것!
    그렇다면 num안의 item들을 number로 바꾸어야 하는데 그걸 모르겠다!
		split으로 쪼갠 다음 각 item들의 type을 number로 바꾸고 reduce를 쓰면 덧셈이 되지 않을까?
		그러면 string으로 변환하지 않고 type을 number로 유지하고 푸는 방법은 없을까?
		*/
}
```