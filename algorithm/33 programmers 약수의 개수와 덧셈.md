```jsx
		// range로 left~right 배열로 만들어서
    // 약수의 개수를 filter해서 약수의 개수가 짝수면 배열에 넣고// 양수 +
    // 홀수면 "그 수"는 원래 range 배열에서 빼서 //음수 -
    // 총합 구하기
```

```jsx
function getDivisor(num){
    const divisors = [];
    for(let i = 1 ; i <= Math.sqrt(num) ; i++) {
        if(num % i === 0) {
            divisors.push(i);
            if(num / i != i) 
                divisors.push(num / i);
        }
        divisors.sort((a,b)=> a-b) //나중에 무슨문제생길지 몰라서 귀찮아서 sort해줌
   }
   return divisors;
}

function range(size, start = 0) {
  return Array.from({length: size}, (_, index) => index + start);
}

function solution(left, right) {
    return range(right-left+1, left) // [10,11,12,13,14,15]
					 .map(e => getDivisor(e).length %2 == 0 ? +e : -e) //[[1,2,5,10],[1,11]....]
					 .reduce((a,b)=> a+b) //[10, 11, 12,]
}
```