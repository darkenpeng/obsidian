```jsx
function solution(number, k) {
    const limit = number-k
    const stack = [];

    for(const num of number){
        while(stack.length && k > 0 && num > stack[stack.length -1]){
            stack.pop()
            k -= 1
        }
        if(stack.length < limit){
            stack.push(num)
        }
    }
    return stack.join('')
}
```