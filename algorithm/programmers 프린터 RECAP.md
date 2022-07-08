```js
function solution(priorities, location) {

	let printedID = null;
	let count = 0;
	const queue = priorities.map((v,i)=>({priority : v, id : i}))

  

	while(printedID !== location){
		let maxPriority = Math.max(...queue.map((item)=>item.priority))
		let J = queue.shift()

  

		while(maxPriority !== J.priority){
			queue.push(J)
			J = queue.shift()
		}

	count += 1
	printedID = J.id

	}

return count

}
```

`생각해볼 것!`
heap을 깎아서 푸는 것과 파이썬의 heapq를 이용하는 것 둘 중 뭐가 더 현재 내 풀이보다 나은 풀이일까?