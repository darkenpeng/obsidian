# Map이 뭔데요?
> 
> 객체 – 키가 있는 컬렉션을 저장함
> 배열 – 순서가 있는 컬렉션을 저장함
	하지만 현실 세계를 반영하기엔 이 두 자료구조 만으론 부족해서 `맵(Map)`과 `셋(Set)`이 등장하게 되었다.
> [맵(Map)](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Map)은 키가 있는 데이터를 저장한다는 점에서 `객체`와 유사합니다. 다만, `맵`은 키에 다양한 자료형을 허용한다는 점에서 차이가 있습니다.> 
> **Js에서의 자료구조**
> https://ko.javascript.info/map-set

 python에서 딕셔너리 같구만 객체는 key값으로 문자형만 허용했지만 map에서는 value에 다른 자료형을 허용한다
 뭐..이런 애들이 있단다.

```javascript
-   `new Map()` – 맵을 만듭니다.
-   `map.set(key, value)` – `key`를 이용해 `value`를 저장합니다.
-   `map.get(key)` – `key`에 해당하는 값을 반환합니다. `key`가 존재하지 않으면 `undefined`를 반환합니다.
-   `map.has(key)` – `key`가 존재하면 `true`, 존재하지 않으면 `false`를 반환합니다.
-   `map.delete(key)` – `key`에 해당하는 값을 삭제합니다.
-   `map.clear()` – 맵 안의 모든 요소를 제거합니다.
-   `map.size` – 요소의 개수를 반환합니다.
```
그냥 브라우저 콘솔에 찍어보면서 연습하겠어요

```javascript
const map = new Map();
//undefined
map.get("first")
//undefined
map.set("first", 1)
//Map(1) {'first' => 1}
map.set("second", map.get("first") +1)
//Map(2) {'first' => 1, 'second' => 2}
map.set("third", map.get("first") +1)
//Map(3) {'first' => 1, 'second' => 2, 'third' => 2}
map.set("third", map.get("first") +1)
//Map(3) {'first' => 1, 'second' => 2, 'third' => 2}
map.set("third", map.get("second") +1)
//Map(3) {'first' => 1, 'second' => 2, 'third' => 3}
map.has("first")
//true
map.values()
//MapIterator {1, 2, 3}
map.keys
//ƒ keys() { [native code] }
map.keys()
//MapIterator {'first', 'second', 'third'}
map.size()
//VM946:1 Uncaught TypeError: map.size is not a function
//  at <anonymous>:1:5
//(anonymous) @ VM946:1
map.size
3
map.delete("third")
//true
map
//Map(2) {'first' => 1, 'second' => 2}
map.clear()
//undefined
map
//Map(0) {size: 0}

```
아놔 프로퍼티인데 메서드인줄알고 소괄호 붙여서 굳이 reference error내기
무튼 이번 문제를 풀면서 map.set(key, map.get("key명") + 1)
이 형식이 자주 사용된다고 해서 흥미로웠는데
map.get으로 가져온 value가 존재한다면 뒤의 연산을 해주고 존재하지 않는다면 undefined를 반환하는게 아니라 1을 반환하기 때문이다
약간 널병합연산자라던지 옵셔널체이닝 연산자 뿐만 아니라 (값이 존재하지 않는다면) 가상의 맵이라는 자료구조의 값을 할당할 수 있어서 표현법을 다양하게 알게 된 느낌이라서 좋았다~ 껄껄


# 커비하고 싶은 사람들 풀이 모음
## 내가 짱좋아하는 이불님 풀이
블블이 프로페써~ 일요일날 유기묘 데려온다고 했는데 고생 꽤나 한거같아 걱정... 아무튼 잔말말고 풀이 갈김

불불이 프로페서도 해시맵(파이썬기준, js에선 맵)을 사용해서 푸시진 않았다!
문자열들을 통째로 배열로 얕복을 해서 가져온 다음 그 배열에서 filter를 하는데 jewels문자열이 stone(stones string이 배열이 된 상태에서의 element하나를 stone이라고 칭함)을 가지고 있다면(.includes) 그 배열의 길이를(stone에서 찾은 jewels들) 리턴한다고 깔끔하게 푸셨다 ~ 멋짐 그 자체 블블님 커비각

```javascript
var numJewelsInStones = function(jewels, stones) { return [...stones].filter(stone => jewels.includes(stone)).length };
```

## ~~해시맵으로 풀라고 했는데 말안듣고 정규표현식으로 푼  ~~디스캣님 풀이
이건 근데 이건 내가 애초에 "이 문제는 절대로 해시맵만 이용해서 푸세요"라고 말한 것도 아니고 **해시맵을 사용하지 않고도 풀 수 있는 방법이 있다면 그 풀이 또한 존중해야 하기 때문에** 매니징 실패여서 나중에 공지를 다시 때렸다.

그리고 교수님들(블블쨩, 탐토님...등...)은 해시맵따윈 진작 뿌셨을거라 "해시맵을 배우기 위해 이 문제를 푼다"라는 공동의 목적과는 벗어나 있기 때문에 상관이 없었다.

무튼 다시 돌아와서 디스캣 님풀이는 다음과 같다.
```javascript
const numJewelsInStones = (jewels, stones) => stones.match(new RegExp(`[${jewels}]`,'g'))?.length??0
```
옵셔널 체이닝 연산자랑 널 병합 연산자 오랜만~ㅎ2ㅎ2
저 친구들과의 추억..아련..(https://log-of-antarctic-penguin.tistory.com/89)
근데 다시 보니까 몰?루 MDN에서 syntax를 다시 찾아보았다.
> **syntax**
> obj?.prop
ref > https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Optional_chaining


stones.match(RegExp로 생성된 객체)가 string.match를 실행하고 나서 일치하는 값이 없다면 null을 반환할 거라** 저렇게 optional chaining연산자로 length라는 프로퍼티를 0 으로 해준다고 쓰신 것 같다. 근데 length 프로퍼티가 존재하지 않을 경우를 위해 또 ??를 써주신듯(?)

>>** 문자열이 정규식과 일치하면, 일치하는 전체 문자열을 첫 번째 요소로 포함하는 [`Array`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array)를 반환한 다음 괄호 안에 캡처된 결과가 옵니다. 일치하는 것이 없으면 [`null`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/null)이 반환됩니다.
>>https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/match

JS 내장객체 RegExp에 대해서는 요즘 읽고 있는 You don't know JS(예제가 웃겨 미치겠음)에서 일요일에 첨봤는데(존재만 앎) 그래도 사용법을 몰라서 MDN을 까보았다~
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp/RegExp

## [구문](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp/RegExp#%EA%B5%AC%EB%AC%B8 "Permalink to 구문")

리터럴, 생성자, 팩토리 표기법이 가능합니다.
```javascript
/pattern/flags
new RegExp(pattern[, flags])
RegExp(pattern[, flags])

```
이제 저 패턴과 flags가 뭔지 알아보자.

### [매개변수](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/RegExp/RegExp#%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98 "Permalink to 매개변수")

`pattern`

정규 표현식을 나타내는 텍스트.

ES5부터는, 생성자 표기법에 한정하여 다른 `RegExp` 객체 혹은 리터럴을 사용할 수 있습니다. 패턴은 [특수 문자](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Regular_Expressions#%ed%8a%b9%ec%88%98_%eb%ac%b8%ec%9e%90_%ec%82%ac%ec%9a%a9%ed%95%98%ea%b8%b0)를 포함할 수 있어서 일반적인 문자열 리터럴보다 더 넓은 범위의 값을 판별할 수 있습니다.

`flags`

정규 표현식에 추가할 플래그.

정규 표현식 객체를 패턴으로 제공한 경우 `flags` 문자열은 제공한 객체의 플래그를 모두 대체하며 `lastIndex`를 `0`으로 초기화합니다. (ES2015 이후)

`flags`를 지정하지 않았으면서 정규 표현식 객체를 제공한 경우, 해당 객체의 플래그와 `lastIndex`를 복제합니다.

`flags`는 다음 문자를 조합하여 지정할 수 있습니다.

`g` (global, 전역 판별)

처음 일치에서 중단하지 않고, 문자열 전체를 판별합니다.

=> 여기서 디스캣님이 달아주신 'g'라는 플래그는 input값과 정규표현식이 일치하더라도 끝내지 않고 들어오는 input(문자열)을 모두 판단하게 하려고 다신 것 같음
아놔 그러면 저 flag 안 달면 여기서 어떻게 될까 예상은 하나 찾고 끝날거 같단 말이지
https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String/match


## 직님의 파이썬 풀이
직님처럼 명령형과 파이썬을 잘하는 사람이 되고 싶다~
```python3
# jewels에 있는 글자와 stones에 있는 글자를 하나하나 비교하여(이중 for문) 
# 비교하고, 같으면 cnt++하여 cnt를 정답으로 리턴했다 
class Solution:
def numJewelsInStones(self, jewels, stones):
	cnt = 0
	for i in jewels:
		for j in stones:
			if i == j:
				cnt += 1
	return cnt
```
파이썬은 for i in ~이랑  for(const ~ of) 이랑 비슷한모양과역할을 한다는 건 알겠고
아따 i  == j이면 cnt를 +1해줘서 리턴하는 깔끔한 풀이 멋지구리


## 탐토님 풀이
맵에 대해서 아주 할말이 많으셔서 30분동안 물도 안마시고 설명해주심
이렇게 열심히 설명해주시면 정리를 안할 수가 없다고요ㅡㅡ
내 껄 리팩토링 한 듯한 느낌의 풀이 역시 깔끔하게 푸심 ~ 커비각 냠냠
```javascript
var numJewelsInStones = function(jewels, stones) {
		// O(M + N)	
    const counter = counter(stones);

		const result = [...jewels].map(jewel => counter.get(jewel) ?? 0);
    return sum(result); // jewel 이 없으면 0
};

function counter(arr){
    const result = new Map(); // 빈번하게 값을 바꿀 때에는 Map이 객체{}보다 빠르다
    for (const item of arr){
        result.set(item, (result.get(item) ?? 0) + 1);
    }
    return result;
}

function sum(arr){
    return arr.reduce((a,b) => a+b, 0);
}
// 61 ms	42.9 MB
```

