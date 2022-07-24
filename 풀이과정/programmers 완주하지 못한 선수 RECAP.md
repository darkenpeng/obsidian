```javascript
function solution(participant, completion) {

// 배열돌면서 키로 배열의 요소를 넣음
// 숫자셈(participant)
	
	const participantCounter = new Map();
	for (const name of participant) {
	//undefined는 falsy 하고, OR연산자는 falsy하면 무조건 오른쪽걸 반환
		participantCounter.set(name, (participantCounter.get(name) || 0) + 1);

	}

	const completionCounter = new Map();
	for (const name of completion) {
		completionCounter.set(name, (completionCounter.get(name) || 0) + 1);
	}

//participantCounter를 돌면서 key가 존재하면 completeionCounter에 있는 키도 있는지 비교함
//둘이 value다르면 리턴함
	for (const name of participantCounter.keys()) {
		if(participantCounter.get(name) !== completionCounter.get(name)){
			return name
		}
	}

}
```