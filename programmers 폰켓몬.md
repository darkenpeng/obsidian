```jsx
function solution(nums) {
    const limit = Math.floor(nums.length / 2) //2
    const unique = new Set(nums).size; //3
    return limit >= unique ? unique : limit    
}
```

```jsx
function solution(nums) {
    const limit = nums.length / 2 //2
    const unique = new Set(nums).size; //3    
    return Math.min(limit, unique)
}
```

```jsx
function solution(nums) {
   return Math.min(nums.length / 2, new Set(nums).size)
}
```