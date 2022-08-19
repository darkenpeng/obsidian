```jsx
const sum = (arr) => arr.reduce((acc, n) => acc + n, 0);

function solution(n, computers) {
  const visited = Array(n).fill(false); // [false, false, false]

[
	[1, 1, 0],
	[1, 1, 0],
  [0, 0, 1],
]
  function dfs(i) {
    if (visited[i] === true){
		return 0;
	}
	else{
		// 방문처리
		visited[i] = true;
		computers[i].forEach((isConnected, newI) => {
		if (isConnected && newI !== i) dfs(newI);
		});
		return 1;
	}
    
  }
  return sum(visited.map((_, i) => dfs(i)));
}

```

## 유형
DFS
## 아이디어
방문하지 않은 노드를 방문하고 방문처리 후 갯수를 세줌.
연결된 노드가 있으면 그 노드를 탐색! 하지만 갯수는 세주지 않음(연결되어 있는 노드여서)
