```javascript

function solution(jobs) {


	let pointer = 0
	const N = jobs.length
	let sortedArr = jobs.sort((a,b)=> a[1]- b[1]) //[[0,3],[2,6],[1,9]] 일단 더 적게 걸리는 시간대로 정렬함
	let accumulated = 0;

  

	while (sortedArr.length) {

		const index = sortedArr.findIndex((job,i)=> job[0] <= pointer)

		if(index == -1) {

			pointer += 1 
		}

		else {

			const task = sortedArr.splice(index, 1)[0] // sortedArr = [[2,6],[1,9]] task [[0,3]]

			pointer += task[1]
			accumulated += (pointer - task[0])

		}

	}

	return Math.floor( accumulated / N)

}

```

