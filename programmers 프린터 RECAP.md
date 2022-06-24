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