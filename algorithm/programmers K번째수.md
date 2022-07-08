```javascript
function solution(array, commands) {
	return commands.map(([i,j,k],index)=> array.slice(i-1,j).sort((a,b)=> a-b)[k-1])
}
```