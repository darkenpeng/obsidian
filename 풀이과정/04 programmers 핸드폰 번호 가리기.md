```jsx
function solution(phone_number) {
	//#제한시간:20분+풀이과정 정리 10분
	//#접근
	//배열의 11자리 숫자를 뒤에서부터 4개를 제외하고 앞의 숫자를 모두 *로 바꾼다

		//#1st 먼저 숫자를 배열에서 꺼낸 뒤,값을 문자열로 바꿔볼까?
		~~//개떡같은 변수명...~~
		//const [...num] =phone_number
		// 결과 ['0','1','0',..'8']
		//     console.log(num)
		// 뒤에서부터 4번째 숫자는 (배열의 item길이-4)번째 숫자
		//     let startNum = phone_number.length-4;
		//루프 돌려서 item 값 찍어보기
		//     for(startNum;startNum<phone_number.length;startNum++){
		//         console.log(num[startNum])
		//     }
    
    //#2nd item을 앞에서부터 8번째까지 지우고
		//"*"8개를 배열의 item으로 추가할까?
    // [원본] arr.splice(1, 1);
    // const countOfItem = phone_number.length;
    // phone_number.splice()
		//문서 읽다가 갑자기 #3rd생각이 나서 안쓰고 넘어감

    //#3rd 배열의 item을 ''을 기준으로 쪼개볼까?
		//변수명 거지같음
		//실행 시 ['0','1','0'...'8'] 왜냐면 문자열의 배열이지 하나의 문자열이 아니기 때문에!
		//''기준으로 나눌 수가 없음
		//[?]숫자는 하나의 값인가?
    // const a = phone_number.split(',',phone_number.length);
    // console.log(a)
    **
    //#4th array의 item을 "*"으로 바꾸어볼까?
    //문법 몰라서 찾아본 map의 예제
		//# 시간초과
		// let result = arr.map(function(item, index, array) {
    // 요소 대신 새로운 값을 반환합니다.
    const countOfItem = phone_number.length;
    const asteric = "*"
    let startNum= countOfItem-3;
    for (startNum; startNum<countOfItem; startNum++){
        console.log(result)
    }
    
    let result = phone_number.map(phone_number[startNum]=>asteric)
});
    
    var answer = '';
    // return answer;
}

```