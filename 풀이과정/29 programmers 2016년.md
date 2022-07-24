```jsx
function solution(a, b) {
//input 5,24
    // 31+29+31+30+ 24-1 / 7 = (나머지에 해당하는 element를 찾아서 리턴)
    // 하지만 배열의 index는 0부터 시작하지
	 const week = ["FRI","SAT","SUN","MON","TUE","WED","THU"]
	 const day = [31,29,31,30,31,30,31,31,30,31,30,31]
	 const targetDay= day.slice(0,a-1)       
   const monthDateSum = targetDay.reduce((a,b) => a + b,0);
   const idx = (monthDateSum+b-1)%7
   return week[idx]
}
```

```jsx
// # refactor
// 근데 그냥 줄 수만 줄이고 별로 좋지 않은 리팩토링..
// 이거 변수명 좀 제발...(monthDaySum...아오)
// 2017년 함수 계산하려면 29-> 28로 변경해야 해서 유틸성이 구리다
function solution(a, b) {
	 const DAY = ["FRI","SAT","SUN","MON","TUE","WED","THU"]
// 각 월의 일수?
	 const MONTH = [31,29,31,30,31,30,31,31,30,31,30,31]
	 const monthDaySum = MONTH.slice(0,a-1).reduce((a,b) => a + b,0);
   return week[monthDaySum+b-1)%7]
}
```

```jsx
테스트 1 〉	통과 (3.97ms, 30.3MB)
테스트 2 〉	통과 (4.09ms, 30.2MB)
테스트 3 〉	통과 (3.96ms, 30.2MB)
테스트 4 〉	통과 (4.68ms, 30.2MB)
테스트 5 〉	통과 (3.99ms, 30.1MB)
테스트 6 〉	통과 (3.99ms, 30.1MB)
테스트 7 〉	통과 (4.15ms, 30.4MB)
테스트 8 〉	통과 (3.95ms, 30.3MB)
테스트 9 〉	통과 (3.98ms, 30.2MB)
테스트 10 〉	통과 (3.99ms, 30.2MB)
테스트 11 〉	통과 (3.94ms, 30.1MB)
테스트 12 〉	통과 (4.06ms, 30.4MB)
테스트 13 〉	통과 (3.96ms, 30.2MB)
테스트 14 〉	통과 (3.95ms, 30.3MB)
```