```jsx
// #psudo (삽질 1)
[1,3,2,5,4] 9 3
[2,2,3,3] 10 4
[1,2,3,4,5]
		array.length C 1 sum() == budget return (새롭게 생성된) array.length
    array.length C 2 sum() == budget
    .
    .
    .
    array.length C array.length sum() == budget
//운동끝나고풀게요
```

```jsx
		
// 1~array.length를 뽑을 건데
    // sort를 시켰으니까 가장 작은 것 부터 뽑음.
    // 순서대로 sum(0,1) < budget
    // sum(0,1,2) < budget
    // sum(0,1,2,3) == budget 
    // 깊복해야 하네...
```

```jsx
//😍 다시 물어볼 것.(팽)
const sum = (array)=> array.reduce((a,b)=> a+b, 0)

function solution(d, budget) {
    const res = d.sort((a,b) => (a-b))
                 .findIndex((e,i) => sum(d.slice(0,i+1)) > budget)
    return res !== -1 ? res : d.length;
}
```