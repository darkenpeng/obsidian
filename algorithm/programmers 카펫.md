```js
function getYellow (height, width) {
	return (height-2) * (width-2)
}

function getHeight(brown, yellow) {
	const square = Math.floor(Math.sqrt(brown + yellow));
	const widthHeight = brown + yellow;
	for (let i = 3; i < square; i++) {
		if (widthHeight % i == 0 && getYellow(i, widthHeight/i) === yellow) {
			return i;
		}
	}
}

function solution(brown, yellow) {
	const height = getHeight(brown, yellow);
	const width = (brown + yellow) / height;
	return [width, height];
}
```