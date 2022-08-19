# 삽질(실패)

```jsx
const cache = [];

function find(index, land){
      for (let i = 0; i< land.length; i++){
        const loc = Math.max(...land[i])
        if(cache[i] === undefined) {
            cache[i] = land[i].indexOf(loc)
        }
        //console.log(cache)          

          return find(index+1, land[i+1])
      }
}
    
function solution(land) {
    
    for (let i = 0; i< land.length; i++){
         find(index, land)
    }
    return find(land)
 
    

}
```
지난번에 피보나치 풀이 비슷하게 풀려고 했는데 장렬히 실패함 ㅎㅎ

```jsx
function solution(land) {
  let answer = [0,0,0,0]

	// 단계를 올라가면서
  for (let level = 0; level < land.length; level++){
    answer = land[level].map((v, i) => v + Math.max(...answer.slice(0, i).concat(answer.slice(i+1))))
  }

  return Math.max(...answer)
}
```