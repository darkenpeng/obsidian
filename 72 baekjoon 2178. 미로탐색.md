```jsx
const fs = require("fs")
const input = fs.readFileSync("/dev/stdin").toString()

const input = `4 6
101111
101010
101011
111011`

const [first, ...raw] = input.split('\\n');
const [row, col] = first.split(' ')
const maze = raw.map(row => row.split(''))
function solution(row, col, maze){
    const dx = [0,1,0,-1];
    const dy = [1,0,-1,0];
    const queue = [[0,0]];
    const visited = maze.map((e)=> e.map(()=> 1))
    while(queue.length){
      const [y,x] = queue.shift();
      const now = visited[y][x];

      if( y == row-1 && x == col-1){
        return now;
      }

      for(let i = 0; i< 4; i++){
        const nx = x + dx[i]
        const ny = y + dy[i]
        if(nx >= 0 && ny >= 0 && nx < col && ny < row){
          if(visited[ny][nx] == 1 && maze[ny][nx] == 1){
            queue.push([ny,nx])
            visited[ny][nx] = now + 1
          }
        }
      }
    }
}

console.log(solution(row, col, maze))
```


지난번 프로그래머스 문제랑 똑같은 문제! 그래서 복습하려고 일부러 똑같은 문제로 선정함!