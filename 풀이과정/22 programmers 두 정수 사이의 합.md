```python
def solution(a, b):
    # range, sum
    
    # (a-b) 음수면 a<b
    if(a < b) : return sum(list(range(a,b+1)))
    # (a-b) 양수면 a>b
    if(a > b) : return sum(list(range(b,a+1)))
    # (a-b) 0이면 a=b
    else : return a
		# return a가 별루...
```

**너무 느려요!!!!!!!!!!!!!!!!**

```python
테스트 1 〉	통과 (0.00ms, 10.2MB)
테스트 2 〉	통과 (0.01ms, 10.3MB)
테스트 3 〉	통과 (0.01ms, 10.2MB)
테스트 4 〉	통과 (951.51ms, 746MB)
테스트 5 〉	통과 (706.77ms, 521MB)
테스트 6 〉	통과 (504.53ms, 438MB)
테스트 7 〉	통과 (278.64ms, 215MB)
테스트 8 〉	통과 (445.11ms, 346MB)
테스트 9 〉	통과 (349.88ms, 263MB)
테스트 10 〉	통과 (67.81ms, 67.5MB)
테스트 11 〉	통과 (0.22ms, 10.3MB)
테스트 12 〉	통과 (0.65ms, 10.6MB)
테스트 13 〉	통과 (0.41ms, 10.3MB)
테스트 14 〉	통과 (0.00ms, 10.1MB)
테스트 15 〉	통과 (0.05ms, 10.3MB)
테스트 16 〉	통과 (0.12ms, 10.4MB)
```

```jsx
// # 전개
    // 3+4+5 = 12 (3+5)/2 * 3
    // range를 js로 구현? 

    // # psudo
    // 3,4,5를 배열에 뿌려서 reduce로 다 더한다
    
    // # actual
    function solution(a, b) {
        const max = Math.max(a,b)
        const min = Math.min(a,b)
	// +1 하는거 좀 맘에 안듦...
       const range = max-min+1
        const rangeArr = [...Array(range).keys()].map(key => key + min);
// initialValue 써줘야 마음이 편-안
        const initialValue = 0;
        const sumOfArray = rangeArr.reduce((a, b) => a + b, initialValue)
        return sumOfArray
    }
```

**더 느려요... 시그마를 구현하는 방법? // 디스코드 비스킷님이 워낙에 제가 하려고 한거구현하심(속도얼마나나와요????)**

```jsx
테스트 1 〉	통과 (0.10ms, 30.1MB)
테스트 2 〉	통과 (0.10ms, 30.1MB)
테스트 3 〉	통과 (0.11ms, 30.1MB)
테스트 4 〉	통과 (2231.97ms, 744MB)
테스트 5 〉	통과 (1548.65ms, 524MB)
테스트 6 〉	통과 (1378.36ms, 405MB)
테스트 7 〉	통과 (625.26ms, 245MB)
테스트 8 〉	통과 (1037.55ms, 362MB)
테스트 9 〉	통과 (876.21ms, 267MB)
테스트 10 〉	통과 (176.36ms, 94.3MB)
테스트 11 〉	통과 (0.55ms, 30.1MB)
테스트 12 〉	통과 (1.79ms, 31MB)
테스트 13 〉	통과 (0.68ms, 30.1MB)
테스트 14 〉	통과 (0.10ms, 30.2MB)
테스트 15 〉	통과 (0.25ms, 30.4MB)
테스트 16 〉	통과 (0.36ms, 30.2MB)
```