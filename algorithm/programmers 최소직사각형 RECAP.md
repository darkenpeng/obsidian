```js

function solution(cards) {

	const maxWidth = cards.map(([width, height])=> Math.max(width, height))
	const maxHeight = cards.map(([width, height])=> Math.min(width, height))

		return Math.max(...maxHeight) * Math.max(...maxWidth)
}
```

`혼잣말`
성능이 어떠할지... 반복문으로 구현한 것과 비교했을 때 성능 VS 가독성 어떤 게 더 나을지 고민해보기!
다른 사람들이 익숙하지 않아서 이해하기 어렵다면 반복문으로 구현하는 것도 생각해보기!