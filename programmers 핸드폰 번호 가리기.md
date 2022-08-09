```js
function solution(phone_number) {
    const hashed_num = phone_number.length - 4;
    const real_num = phone_number.slice(hashed_num)
    return "*".repeat(hashed_num)+real_num

}
```