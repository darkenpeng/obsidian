```jsx
function solution(nums) {
   // # 문제 해석
    // 배열 안에 있는 무작위 숫자 3개를 더했을 때 소수가 나오는 경우의 수를 구하는 함수
    //https://medium.com/@hongkevin/js-4-array-%EB%A9%94%EC%84%9C%EB%93%9C%EB%93%A4-concat-join-indexof-slice-sort-push-4eec70d564e7
    console.log(nums.join())
    
    // 배열 안에 있는 숫자 3개를 모두 더했을 때 소수인 경우를 찾기
    // [1,2,3,4] => [x+y+z = 소수]
    // ### 소수인지 판별하기? X
    // 1 item 3개를 고르기
    // [1,2,3], [1,2,4] [2,3,4]
    // 2) 고른 값을 더하기.
    // [1+2+3, 1+2+4, 2+3+4]
    // 리턴해서 새 배열에 담기?
    // 담은 배열에서 item을 한 개씩 꺼내서 소수인지 판별하기
    // [6, 7, 9]
    // 3) 7만 소수다! 소수는 뭐지 ? 약수를 1과 스스로만 가지는 수
    // 4) 리턴된 값 중에서 소수인지 판별한다.
    // answer += 1
   
    return answer;
}
```