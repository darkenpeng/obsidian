```jsx
const isPrime = (n) => {
  if(n === 0) return false;
  if(n === 1) return false;

  for (let i = 2; i < Math.sqrt(n); i++) {
    if (n % i === 0) {
      return false;
    }
  }

  return true;
}

function getCases(input){
  if(input.length === 1) return [input];

  if(input.length === 2){
    return [input[0], input[1], input[0]+input[1], input[1] + input[0]]
  }

  const cases = [...input].flatMap((n, i) => getCases(input.slice(0, i) + input.slice(i+1, input.length)).flatMap(m => [m+n, n+m]))
    .concat([...input]) // ['1','2','7']
  return unique(cases)
}

function unique(arr){
  return Array.from(new Set(arr))
}

function solution(numbers){
  return unique(getCases(numbers).map(s => parseInt(s))).filter(isPrime)
}
// expected.filter(isPrime)

console.log(getCases('011'))
console.log(getCases('7'))
const input = "011"

const expected = ['1','7', '17', '71']
```