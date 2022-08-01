# 스택과 큐
스택은 후입선출 (LIFO: Last In First Out),
큐는 FIFO(First In First Out)

파이썬에서는 스택 자료형을 별로도 제공하지는 않지만, 리스트가 스택의 모든 연산을 지원한다.
=> 자바스크립트에서는 배열이 스택의 모든 연산을 지원한다.
하지만 리스트는 동적 배열(가변길이)로 구현되어 있어 큐의 연산을 수행하기에는 효율적이지 않다.
=> 큐를 위해서는 데크(Deque)라는 별도의 자료형을 사용해야 성능이 좋다.
스택은 `삽입`과 `삭제`에 O(1), `탐색`에 O(n)의 시간복잡도가 소요된다.

하지만 파이썬에서 리스트는 스택과 큐의 모든 연산을 지원하기 때문에 성능을 고려하여 구현할 게 아니라면 스택과 큐를 이용한 연산은 리스트를 통해 가능하다. 

> 대표적으로 `JAVA`의 경우에는 `java.util.Queue`를 임포트하여 사용할 수 있고 `파이썬`의 경우 `collections`에서 `deque`를 임포트해 큐처럼 사용할 수 있다. 그러나 자바스크립트는 당연히 큐와 관련된 객체가 내장되어 있지 않다. 따라서 큐를 이용하기 위해서는 직접 자료구조를 작성해야 할 필요가 있다.

### [Javascript] 스택 구현
```
- Class를 이용해 직접 구현하기
- Array를 이용해 직접 구현하기
```

#### Class를 이용해 직접 구현하기
```javascript
//reference https://www.geeksforgeeks.org/implementation-stack-javascript/

class Stack {
	// Array is used to implement stack
	constructor() {
		this.items = [];
	}

	// push(item)
	push(element) {
	// push element into the items
		this.items.push(element);
	}
	// pop()
	pop() {
	// return top most element in the stack
	// and removes it from the stack
	// Underflow if stack is empty
		if (this.items.length == 0) return "Underflow";
			return this.items.pop();
	}
	
	// peek()
	peek() {
	// return the top most element from the stack
	// but does'nt delete it.
		return this.items[this.items.length - 1];
	}

	// isEmpty()
	isEmpty() {
	// return true if stack is empty
		return this.items.length == 0;
	}

	// printStack()
	printStack() {
	const str = "";
	for (let i = 0; i < this.items.length; i++) str += this.items[i] + " ";
		return str;
	}
}
```

#### Array를 이용해 직접 구현하기
```javascript
const stack = [];

//put value on top of stack
stack.push(1);

//remove value from top of stack
const value = stack.pop();
```

### [Javascript] 큐 구현
```
- 라이브러리 사용
- Array를 이용해 직접 구현하기
```

#### - 라이브러리 사용
아래의 라이브러리는 단순한 예시입니다.
openbase라는 웹사이트에서 1.1k의 다운로드 수를 가진 라이브러리를 가져왔을 뿐, 반드시 이 라이브러리를 사용해야 한다는 의미는 아닙니다!
`Reference` : 
https://openbase.com/js/@supercharge/queue-datastructure
`API docs`
: https://www.npmjs.com/package/@supercharge/queue-datastructure
`Implementation` : 
```Javascript
const Queue = require('@supercharge/queue-datastructure')

// create a queue from an existing array
const queue = new Queue([ 1, 2, 3 ])

// or, create a queue from individual items
const queue = new Queue(1, 2, 3)

// or, create an empty queue
const queue = new Queue()
```
#### - Array를 사용하여 직접 구현하기

### python에서 리스트, JS에서 배열로 큐 연산을 수행했을 때 성능이 왜 느려지나요?

참고 : C언어의 포인터
> http://www.tcpschool.com/c/c_pointer_intro

JS에서 배열, python에서 리스트는 가변길이 (각각의 element가 같은 길이를 가진 것이 아닌, 존재하지 않을 경우 Undefined라는 값으로 저장이 되어 있기 때문에 index를 이용해 요소를 찾으려고 할 때 인덱스에 해당하는 값을 찾기 위해 해당 인덱스가 위치한 메모리까지 값의 길이를 계산하기 때문에 속도가 느려질 수 있습니다.)
`삽입` 및  `삭제`에 O(1), 탐색에 O(n)이 걸린다.

>  사실 투 포인터를 사용한다면 위처럼 꼭 객체(`Object`)가 아니라 배열(`Array`)을 사용해서도 `O(1)`의 접근 시간을 보장할 수 있다. 다만 이 경우엔 배열의 첫 번째 원소를 제거하더라도 이미 선언된 공간은 `undefined`라는 값이 차지하고 있기 때문에 별도의 과정 없이는 공간 최적화가 이루어지지 않을 수 있다.
   ref : https://velog.io/@longroadhome/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-JS%EB%A1%9C-%EA%B5%AC%ED%98%84%ED%95%98%EB%8A%94-.%ED%81%90-Queue

### 스택의 연산
스택은 2가지 연산을 지원한다.
 - push() : 요소를 컬렉션에 추가한다.
 - pop() : 가장 최근에 삽입된 요소를 제거한다.
    단, 아직 제거되지 않은 요소여야 함.

![[Pasted image 20220516184416.png]]
> 메모리 상에 아이템을 위한 공간을 할당하고 새로운 아이템이 추가될 때 마다 포인터로 연결하기만 하면 된다. 아래 그림에서 좌측 ADT는 스택의 연산을 지원하기 위해 1부터 5까지 각 요소가 접시 쌓듯 차곡차곡 놓이겠지만, 실제로 연결 리스트로 구현하게 된다면 물리 메모리 상에는 순서와 관계 없이 여기저기에 무작위로 배치되고 포인터로 가리키게 될 것이다.

### [python] 연결리스트를 이용한 스택의 구현
`Reference`
: 파이썬 알고리즘 인터뷰
`Implementation`
```python

class Node:
	def _init_(self, item, next):
	self.item = item
	self.next = next
	
class Stack:
	def _init_(self):
	self.last = None
	
	def push(self,item):
	self.last = Node(item,self.last)
	
	def pop(self):
	item = self.last.item
	self.last = self.last.next
	return item
```
