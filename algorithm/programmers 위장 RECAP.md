```javascript
function solution(clothes) {

	const clothesMap = new Map();
	for(const [_, kind] of clothes) {
		clothesMap.set(kind, (clothesMap.get(kind) || 0 )+1)
	}

	let cases = 1

	for(const kind of clothesMap.keys()){
		cases *= clothesMap.get(kind)+1
	}

	return cases - 1

}
```