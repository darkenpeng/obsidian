```jsx
function solution(s) {
//odd, even이라는 변수명 index로 수정하면 명시적이다~
const odd = (s.length-1)/2
const even = (s.length-2)/2
const isEven = s.length%2
return isEven === 0 ? s.slice(even, even+2) : s.slice(odd,odd+1)
}

// [홀수]
// a b c 1 1 1 length(3) (3-1)/2
// ab c de 2 1 2 length(5) 5-1/2
// abc d efg 3 1 3 length(7) 7-1/2
// abcd e fghj 4 1 4 length(9) 9-1/2

// [짝수]
// q we r 1 2 1 4-2/2
// qw er ty 2 2 2 6-2/2
// qwe rt yui 3 2 3 8-2/2

// [홀수]
// a b c 1 1 1 length(3) (3-1)/2
// ab c de 2 1 2 length(5) 5-1/2
// abc d efg 3 1 3 length(7) 7-1/2
// abcd e fghj 4 1 4 length(9) 9-1/2

// [짝수]
// q we r 1 2 1 4-2/2
// qw er ty 2 2 2 6-2/2
// qwe rt yui 3 2 3 8-2/2
```