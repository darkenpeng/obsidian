```jsx
function solution(n, lost, reserve) {
  const candidate = getCandidate(lost);
  const rent = reserve.filter((student) => candidate.includes(student));
  return rent.length >= lost.length ? n : n - lost.length + rent.length;
}

function getCandidate(students) {
  const candidate = [];
  const plus = students.map((student) => student + 1);
  const minus = students.map((student) => student - 1);
  candidate.push(...plus, ...minus);
  return [...new Set(candidate)];
}
```

```jsx
테스트 1 〉	통과 (0.13ms, 30.2MB)
테스트 2 〉	통과 (0.10ms, 29.8MB)
테스트 3 〉	실패 (0.10ms, 30.2MB)
테스트 4 〉	통과 (0.12ms, 30.2MB)
테스트 5 〉	실패 (0.14ms, 30.2MB)
테스트 6 〉	통과 (0.09ms, 30.1MB)
테스트 7 〉	통과 (0.11ms, 30.2MB)
테스트 8 〉	통과 (0.13ms, 30.2MB)
테스트 9 〉	통과 (0.12ms, 30.2MB)
테스트 10 〉	통과 (0.12ms, 30.1MB)
테스트 11 〉	통과 (0.17ms, 30MB)
테스트 12 〉	실패 (0.10ms, 30.2MB)
테스트 13 〉	통과 (0.13ms, 30.1MB)
테스트 14 〉	통과 (0.12ms, 30.1MB)
테스트 15 〉	통과 (0.12ms, 30MB)
테스트 16 〉	통과 (0.12ms, 30.2MB)
테스트 17 〉	통과 (0.12ms, 30.1MB)
테스트 18 〉	통과 (0.12ms, 30MB)
테스트 19 〉	통과 (0.12ms, 30.1MB)
테스트 20 〉	통과 (0.10ms, 30.1MB)
```

# 2트
```jsx
function solution(n, lost, reserve) {
  const realLost = lost.filter((student)=> !reserve.includes(student)) //[2,4]
  const candidate = getCandidate(realLost);//[1,3,5]
  const realReserve = reserve.filter((student)=> !lost.includes(student)) //[3]
  const rent = realReserve.filter((student) => candidate.includes(student)); //[1,3,5]
  if (rent.length >= realLost.length) {
    return n;
  } else {
    return n - realLost.length + rent.length;
  }
}

function getCandidate(students) {
    const arr = [];
    for (let i = 0; i<students.length; i++){
        arr.push(students[i]+1, students[i]-1)
    }
    return [...new Set(arr)];
}

const n = 5;
const lost = [2, 4, 5]; [1,3,5, 4,6]
const reserve = [3, 5];
```