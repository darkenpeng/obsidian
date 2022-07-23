```jsx
function solution(people, limit) {
  let count = 0;
  people.sort((a, b) => b - a); // [80,70,50,50]
  while (people.length) {
    const max = people[0]
    const min = people[people.length -1]
    if (min + max <= limit) {
      count += 1
      people.shift()
      people.pop()
      
	} else {
      count += 1
      people.shift()
    }
  }
  return count;
}
```

```jsx
테스트 1 〉	통과 (2.50ms, 31.9MB)
테스트 2 〉	통과 (1.41ms, 30.1MB)
테스트 3 〉	통과 (1.46ms, 30.2MB)
테스트 4 〉	통과 (1.27ms, 30.2MB)
테스트 5 〉	통과 (0.81ms, 29.9MB)
테스트 6 〉	통과 (0.46ms, 29.9MB)
테스트 7 〉	통과 (0.76ms, 30.1MB)
테스트 8 〉	통과 (0.12ms, 30MB)
테스트 9 〉	통과 (0.18ms, 30.3MB)
테스트 10 〉	통과 (1.30ms, 30MB)
테스트 11 〉	통과 (1.13ms, 30.1MB)
테스트 12 〉	통과 (1.07ms, 30.1MB)
테스트 13 〉	통과 (1.31ms, 30MB)
테스트 14 〉	통과 (1.60ms, 30.1MB)
테스트 15 〉	통과 (0.24ms, 29.9MB)
효율성  테스트
테스트 1 〉	실패 (시간 초과)
테스트 2 〉	실패 (시간 초과)
테스트 3 〉	실패 (시간 초과)
테스트 4 〉	실패 (시간 초과)
테스트 5 〉	실패 (시간 초과)
```
