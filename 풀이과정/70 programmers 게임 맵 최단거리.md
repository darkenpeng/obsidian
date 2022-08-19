```jsx
function solution(maps) {
    const dx = [0,1,0,-1];
    const dy = [1,0,-1,0];
    const row = maps.length;
    const col = maps[0].length;
    
    const visited = maps.map((m) => m.map((c)=> 1));
    const queue = [[0,0]];
    
    while(queue.length){
        const [y,x] = queue.shift();
        const now = visited[y][x];
        
        
        for(let i = 0; i< 4; i++){
            const ny = y + dy[i];
            const nx = x + dx[i];
        if(0<= ny&&ny < row &&0 <= nx &&nx<col){
            if(maps[ny][nx] === 1 && visited[ny][nx]=== 1){
                visited[ny][nx] = now + 1;
                queue.push([ny,nx])
            }
        }
        }
    }
    
    const goal = visited[row-1][col-1];
    return goal == 1 ? -1 : goal;
}
```