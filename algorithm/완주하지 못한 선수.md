# 내 풀이
```javascript
function solution(participant, completion) {

	const runnerMap = new Map();
	    for (const runner of participant) {
	        runnerMap.set(runner, (runnerMap.get(runner)|| 0)+1 )
	    }

	const completedMap = new Map();
	    for(const completed of completion) {
			        completedMap.set(completed,(completedMap.get(completed)||0) +1)
	    }
    
	const runnerArr = [...runnerMap.entries()]
// [ [ 'leo', 1 ], [ 'kiki', 1 ], [ 'eden', 1 ] ]
return runnerArr.find((entry)=> entry[1] !== completedMap.get(entry[0]))[0]
}

```

## 삽질과정 (하루 종일 고민한 거 억울해서 씀)
처음에는 맵카운터(아래 코드)를 참가자 리스트와 완주한 인간 리스트를 합쳐서 만들었었다. 왜냐면 중복을 걸러야 한다는 걸 제대로 생각을 못했기 때문에...
```javascript
// Mapcounter
	const completedMap = new Map();
	    for(const completed of completion) {
	        completedMap.set(completed, (completedMap.get(completed)||0) +1)
	    }
```

```javascript
const runnerList = new Map();
	for (const runner of participant){
		for (const completedRunner of completion){
			if(runner == completedRunner){
				runnerList.set(runner, completedRunner)
			}		
		}
	}
	console.log(runnerList)	
```

> **input**
> ["leo", "kiki", "eden"], ["eden", "kiki"]
> **expected**
> "leo"
>**console**
>Map { 'kiki' => 'kiki', 'eden' => 'eden' }

이렇게 하면 **중복을 못거른다**
왜냐하면 참가한 인간들 리스트와 완주한 인간 리스트가 개별적으로 존재해야 중복값이 있는 지 비교할 수 있기 때문. 카운터를 애초에 잘못 구현한게 문제 
각각의 카운터를 구현한 다음 그 값을 비교해야...

```javascript
	const runnerMap = new Map();
	    for (const runner of participant) {
	        runnerMap.set(runner, (runnerMap.get(runner) || 0)+1 )
	    }

	const completedMap = new Map();
	    for(const completed of completion) {
	        completedMap.set(completed, (completedMap.get(completed) || 0) +1)
	    }

	console.log(runnerMap)
	console.log(completedMap)

```
카운터 두 개에 뭐가 들어있는 지 확인

> Map { 'leo' => 1, 'kiki' => 1, 'eden' => 1 } // runnerMap
> Map { 'eden' => 1, 'kiki' => 1 } // completedMap

### 논리연산자 || (OR)
>https://ko.javascript.info/logical-operators

```javascript
alert( true || true ); // true
alert( false || true ); // true
alert( true || false ); // true
alert( false || false ); // false

```
>피연산자가 모두 `false`인 경우를 제외하고 연산 결과는 항상 `true`입니다.
**피연산자가 불린형이 아니면, 평가를 위해 불린형으로 변환됩니다.**
예를 들어, 연산 과정에서 숫자 `1`은 `true`로, 숫자 `0`은 `false`로 바뀌죠.

1은 truthy, 0은 falsy하다.
![[Pasted image 20220504224045.png]]
이때, OR `||`연산자는 다음 순서에 따라 연산을 수행합니다.

-   가장 왼쪽 피연산자부터 시작해 오른쪽으로 나아가며 피연산자를 평가합니다.
-   각 피연산자를 불린형으로 변환합니다. 변환 후 그 값이 `true`이면 연산을 멈추고 해당 피연산자의 **변환 전** 원래 값을 반환합니다.
-   피연산자 모두를 평가한 경우(모든 피연산자가 `false`로 평가되는 경우)엔 마지막 피연산자를 반환합니다.

여기서 핵심은 반환 값이 형 변환을 하지 않은 원래 값이라는 것입니다.

정리해 보자면 이렇습니다. OR `"||"` 연산자를 여러 개 체이닝(chaining) 하면 첫 번째 truthy를 반환합니다. 피연산자에 truthy가 하나도 없다면 마지막 피연산자를 반환합니다.

---
```js
	const runnerArr = [...runnerMap.entries()]
```

여기서 배열로 만들어야겠다는 생각을 왜했냐면 Map의 기본메서드 중에서 key를 이용해 value를 얻어오는 메서드를 찾지 못했기 때문이다..그래서 정해진 요소값을 반환하는 Array.prototype.find()메서드를 써야겠다고 생각했다.
그리고 array안 array의 0번째 인덱스는 무조건 이름이고, 1번째 인덱스는 수 일것이므로 1번째 index를 비교해서 0번째 index를 반환해야겠다는 계획을 세움.

```js
// entry는 배열임
runnerArr.find((entry)=> entry[1] !== completedMap.get(entry[0]))[0]

```
총 달린 사람(참가자) 배열에서 배열을 찾을건데, 그 배열의 1번째 index가 같지 않은 배열을 찾아서 0번째 인덱스를 리턴한다고 한 것이다.