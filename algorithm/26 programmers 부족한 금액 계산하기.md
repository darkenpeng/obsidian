```jsx
function solution(price, money, count) {
//n*(n+1)/2 
//변수명...
    const totalCost = (price+price*count)*count/2
    const calculatedValue = money-totalCost
    return  calculatedValue > 0 ? 0 : Math.abs(calculatedValue) 
}
```