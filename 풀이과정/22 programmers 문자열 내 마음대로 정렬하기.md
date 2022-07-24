```jsx
// # pseudo
    // 인덱스가 n인 element를 sort로 정렬해서
		
    // 원본 배열의 element를 정렬?
    // loop {같은 문자를 가지면 다음 인덱스로 넘어가서 정렬} // 사전순
    // 2차원 배열의 정렬을 모르겠음!
// # actual
function solution(strings, n) {
    
    const chars = strings.map(e => e.split(''));
    console.log(chars[n].sort())
// # 구현 못한 이유
// 인덱스를 변경해주는 메서드 같은게 없음
// 정렬하려는 기준과 정렬하려는 대상이 2차원배열안의 element, 1차원배열안의 element라서 구현못하는것임

}

```