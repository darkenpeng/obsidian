## 삽질
```Javascript
//1hr

const topKFrequent = function(nums, k) {

// 빈도
// nums, k
// 1 : 3
// 2 : 2
// 3 : 1
// 상위 2(k)번째 요소까지 출력하기

const numMap = new Map();
// #counter
for(const num of nums) {
numMap.set(num, (numMap.get(num) || 0) + 1 )
}
const numArr = [...numMap.entries()] // //[ [ 1, 3 ], [ 2, 2 ], [ 3, 1 ] ]
// # 삽질
// => 아니 이거 map 돌려가지고 arr, index 매개변수로 받고 e[1]은 sort돌리고 e[0]를 k까지 슬라이스해서 리턴하게 하면 안됨?하지만 slice로 k까지 짜른 배열 ~
// 아근데 slice하려면 values랑 keys랑 나눠야 따로따로 가져와야하나 아무튼 불만족스럽
// 인생을 이렇게 살아야함? 이러려고 코딩했나 자괴감 들어...
// const sortedValueArr = numVal.sort((a,b)=> b-a)
// arr[1].sort를 내림차순으로 돌려서 e[0]을 k까지 리턴한다.
//numArr.map((i,e)=> e.sort((a,b)=> b-a)
//const ex = [...numMap.values()].slice(0,k)
//console.log(ex)
//e[0]

[...numMap.keys()].sort((a,b)=> b-a)
// e[1]
[...numMap.values()].slice(0,k)))
//이걸 배열에서 한번에 !하려면 map돌려서 numMap의 key를 e[0], e[1]으로 하는게 최선일까?
//고통...일단 맘에 안들지만 해보자
// numArr.map(e=> e[0].sort((a,b)=> b-a)).map(e=> e[1].slice(0,k))
//아놔 이렇게 하니까 e[0]이 배열이 아니어서 sort가 function이 아니라고 하네.. 어쩔수없이 keys() values를 가져와서 slice랑 sort해야겠다. 근데 이거 한꺼번에 어떻게하지???
//원본 Map이 sort()당하면 (변경되면, emmutable) keys로 가져와도 상관없을텐데 지금 얕복해서
//원본 Map안에 안바뀌어서 그런거같음. 그러면 원본 Map을 변경하면서 하는 방법과 변경안하고 한번에 keyvalue 연산을 돌리는 방법 이렇게 두개 생각해보자

};
```
## 풀이과정
```javascript
const topKFrequent = function(nums, k) {
	const numMap = new Map();
	// # counter
	for(const num of nums) {
	numMap.set(num,(numMap.get(num)|| 0) + 1 )
	}
	const numArr = [...numMap.entries()] // [ [ 1, 3 ], [ 2, 2 ], [ 3, 1 ] ]
	return numArr.sort((a,b)=> b[1]-a[1])
				 .map((x)=> x[0])
				 .slice(0,k)
};
```