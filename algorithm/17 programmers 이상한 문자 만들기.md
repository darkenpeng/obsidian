```jsx
// [시간초과!]

// # 출력값
    // s = 'try hello world'
    // ['try', 'hello', 'world']
    // ['try'], ['hello'], ['world']
    // ['t','r','y'], ['h','e','l','l','o'], ['w','o','r','l','d']
    // 각각의 배열에서 인덱스가 짝수면 대문자로 치환해서 리턴
    // join()으로 합치기

function solution(s) {
		let strArr = [];
    let answer = [];

    const splitStr = s.split(' ')
    for (const word of splitStr) {
      const chars = word.split('');
			strArr = chars.map((v, i)=> i % 2 === 0 ? v.toUpperCase() : v.toLowerCase());
			answer.push(strArr.join('');
		}		
    return answer.join(' ');
}

function solution(s) {
  let map = [];
  let answer = [];

  const splitStr = s.split(" ");
  for (const word of splitStr) {
    const chars = word.split("");
    map = chars.map((v, i) =>
      i % 2 === 0 ? v.toUpperCase() : v.toLowerCase()
    );
    answer.push(map);
  }
  return answer.join(" ");
}
// T,r,Y H,e,L,l,O W,o,R,l,D

    // 만약 splitWord의 index가 짝수라면, upperCase로 치환하고
    // 홀수면 lowerCase()한 값을 리턴하고 join으로 합쳐주면 되겠군 ~
    // chars[index == 짝수]이 부분을 판별식으로 만들면 되겠군...
    
    // # [여기서 타임아웃!]
    
    // 각각의 배열에 대한 루프를 돌면서(각 배열의 length까지) 배열의 인덱스가 짝수일 때,
		// .toUpperCase() 리턴
    // 배열의 인덱스에 "짝수판별식"이 참이면 으로 삼항연산자에 던지면 되는 것 아닌가?
		// 아니 잠만 인덱스에 판별식을 던질 수 없잖아.. 숫자여야지!
	  //그러면 판별식을 만족하는(짝수) 인덱스를 찾아서 리턴하는 함수를 찾으면 되지 않을까?  

		// # 고민한 과정
        배열의 인덱스가 짝수이면 ? chars.toUpperCase() : chars.toLowerCase()   
        chars[idx] //0,2,4 ...
        idx % 2 == 0

}
```