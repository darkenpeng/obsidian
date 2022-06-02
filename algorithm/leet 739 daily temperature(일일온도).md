```js
const dailyTemperatures = function(temperatures) {
	// target, targetIndex
	// input[73,74,75,71,69,72,76,73]
	// slicedArr[74,75,71,69,72,76,73]
	// expected [1,1,4,2,1,1,0,0]
	
	return temperatures.map((target,index) => { // e,i
		return temperatures.slice(index+1) // 그 인덱스부터 끝까지 잘라줌
						   .findIndex(e => target < e)+1 //+1 안해주면 [0,0,3,1,0,0,-1,-1]
				// 왜냐하면 findIndex안의 index가 자른 배열의 인덱스이므로 0부터 시작함  
	})
};

```

시간초과 뜸...(눈물)

# 탐토님 풀이(그냥삼켜버림)

```js
var dailyTemperatures = function(temperatures) { //[73,74,75,71,69,72,76,73]
	const n = temperatures.length // 8
	const answer = Array(n).fill(0) // [1,1,0,0,0,0,0,0] => [1,1,4,2,1,1,0,0]
	const stack = [] // 아직 더 따뜻한 날을 찾지 못한 추운 day들

	// [2]
	// [73,74,75,71,69,72,76,73]
	temperatures.forEach((nowTemp, nowDay) => {
	// stack은 index의 요소값을 반환 temperatures[stack[stack.length - 1]]
	// 아직 답을 못 찾은 추운 날이 있으면... 오늘의 온도보다 추운 날일 때
	while (stack.length > 0 && temperatures[stack.at(-1)] < nowTemp) {
		const prevDay = stack.pop() // 그 추운 날을 꺼내서
		// 따뜻한 오늘까지 그 추운 날부터 며칠 걸렸는지를 넣어줌
			answer[prevDay] = nowDay - prevDay //index-stack의 맨마지막꺼
		}
		stack.push(nowDay) //[2,3,4]
		})
	return answer

};

// dailyTemperatures([73,74,75,71,69,72,76,73])
// O(N)
```