```js
function solution(progresses, speeds) {


	let cursor = 0;

	const answer = [];

		while(cursor < progresses.length) {

		let advanced = 0

			for(let i = 0; i < progresses.length; i++){

			progresses[i] += speeds[i]

			}

  
		//short circuit
		while(cursor < progresses.length && progresses[cursor] >= 100 ){

		cursor += 1
		//index cursor 가리키는 값이 100이상이면 전진(advanced)
		advanced += 1

		}

  

		if(advanced >= 1){

		answer.push(advanced)

		}

	}

return answer;

}

const progresses = [95, 90, 99, 99, 80, 99]

const speeds = [1, 1, 1, 1, 1, 1]

console.log(solution(progresses, speeds))

```