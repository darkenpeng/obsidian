```jsx
function solution(n) {
const binary = n.toString(2)
const count = binary.split('').filter((c,i)=> c == 1).length
let i = 1
while(i < n) {
    if(count == (n+i).toString(2).split('').filter((c,_)=> c ==1).length){
        return (n+i) 
    }
    else i++
    }
}
```