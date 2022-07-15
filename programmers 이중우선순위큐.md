# psudo
```javascript
//psudo
// ["I -45", "I 653", "D 1", "I -642", "I 45", "I 97", "D 1", "D -1", "I 333"]
//     배열의 element가 I를 포함하고 있다면
//     꺼내서 숫자를 큐에 넣는다.
    
//     배열의 element가 D를 포함하고 있다면
//     e의 숫자를 꺼내서 0보다 크다면 최댓값을 삭제한다.
//                   0보다 작다면 최솟값을 삭제한다.
    
//     if(queue.length === 0)
//         return [0,0]
//     else {
//         return [max, min]
//     }
```
# 날것의 코드

```javascript
 function solution(operations) {
  const queue = [];
	// exp = expression
  for (const exp of operations) {
    if (exp.includes("I")) {
      queue.push(exp.split(" ")[1]);
    }

    if (exp.includes("D")) {
      if (Number(exp.split(" ")[1]) >= 0) {
        const min = queue.sort((a, b) => a - b)[0];
        queue.pop(min);
      } else {
        const max = queue.sort((a, b) => b - a)[0];
        queue.pop(max);
      }
    }
  }

  if (queue.length === 0) return [0, 0];
  else {
   queue.sort((a,b)=> b-a)
   return [queue[0], queue[queue.length -1]].map((num)=> Number());
  }
}
const operations = ["I -45", "I 653", "D 1", "I -642", "I 45", "I 97", "D 1", "D -1", "I 333"]	;
console.log(solution(operations))
```
# 나름 고친 것(리팩토링)
## 개선한 부분
- 구조분해 할당
- 필요없는 sort 제거
- pop과 shift의 쓸모없는 매개변수 제거


## 스스로 생각해본 개선사항
- if문의 depth로 인해 생기는 트레이드오프를 고려해보자
- type casting 2번 해주는 부분...구리다
- 느리더라도 Heap을 클래스를 깎아볼 생각?
- 인덱스로 접근하면 빠르긴 하지만 기존 array의 length가 길다면? 나중에 뭔지 모를것이다...주석이라도 열심히 써주는 건?
```javascript
function solution(operations) {

  const queue = [];

  //exp = expression
  for (const exp of operations) {
    const [command, number] = exp.split(" ");
    if (command === "I") {
      queue.push(number);
    }

    if (command === "D") {
      if (Number(number) >= 0) {
        queue.sort((a, b) => a - b);
        queue.pop();

      } else {
        queue.shift();
      }
    }
  }

  if (queue.length == 0) return [0, 0];
  else {
    queue.sort((a, b) => b - a);
    return [queue[0], queue[queue.length - 1]].map((num) => Number(num));
  }
}
```

