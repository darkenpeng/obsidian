```jsx
function solution(n, times) {
//모든 입국심사관들이 최소시간만큼 걸린다고 가정(시작점)
  let min = Math.min(...times) * Math.floor( n / times.length);
//모든 입국심사관들이 최대시간만큼 걸린다고 가정(끝점)  
  let max = Math.max(...times) * Math.floor(n / times.length);
//최대와 최소 사이의 값(=answer)을 찾을거임
  let answer = 0;
  
  while (min <= max) {
  //중간에 있는 값을 찾아서
    const middle = Math.floor((min + max) / 2);
    //각 입국 심사관마다 몇 명을 심사할 수 있는지 구하고 총합을 더함
    const count = times.map((time)=> Math.floor(middle / time)).reduce((a,b)=> a+b, 0)
    //n명보다 더 많이 심사할 수 있다면(또는 n명만큼 심사할 수 있다면)
    if(count >= n){
	    // 중간값보다 1 작은 값이 추측하고 있는 answer의 최대값이 된다
        max = middle - 1
		//answer는 중간값이 될 수도 있음 하지만 while을 돌면서 min > max가 되는 순간의 answer가 리턴됨
        answer = middle
    }
    else {
    //최솟값은 중간값보다 1 큰 값으로 설정해서 최솟값과 최댓값의 범위를 줄임
        min = middle + 1
    }
  }
  //루프가 끝나면 이분탐색으로 찾은 answer를 리턴
  return answer
}
```

## 3일만에다시풂
```js
function solution(n, times) {
    let min = Math.min(...times) * Math.floor(n / times.length)
    let max = Math.max(...times) * Math.floor(n / times.length)
    let answer = 0;

    while(min <= max){
      let mid = Math.floor((min + max) / 2)
      let count = times.map((time)=> Math.floor(mid / time)).reduce((a,b)=>a+b)
        if(n <= count){
            max = mid - 1
            answer=mid
        }else{
            min = mid + 1
        }
        
    }return answer
}


```
