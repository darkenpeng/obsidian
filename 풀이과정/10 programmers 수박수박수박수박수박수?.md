```jsx
function solution(n) {
    //#psudo
    //n의 개수에 따라 글자 수가 정해진다
    //"수박"이라는 문자열을 반복한다.
    //글자 수만큼 return하는 배열
    const repeatText = '수박';
    const answer = repeatText.repeat(n) //수박수박수박, 수박수박수박수박
    //문자열을 잘라야겠다
		//str.slice(start [, end])
    return answer.slice(0,n);
}

```