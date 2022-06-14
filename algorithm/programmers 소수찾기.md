# 삽질

```javascript
//#psudo 
// input = '147' '1'+getAll('47') 4 + getAll('7') 
// input.split('') 
//['1', '7'] 
// ['1','7','17', '71'].filter(isPrime) 
// return ['7','17','71'].length
```


```javascript
  

	const isPrime = (num) => {

		for (let i = 2; i < num.length; i++) {

			if(n===1) return false;

			if (n % i === 0) {

				return false;

			}

		}

	return true;

	};

function getAll(input) { //string

	if (input.length === 1) {

		return [input];

	}

	if (input.length === 2) { //['1', '7']

		return [input[0], input[1], input[0] + input[1], input[1] + input[0]];

	}

	if (input.length ===3 ){
		//index를 어떻게하지? 배열을 어떻게 자르지?
	}

}
```

# 탐토님 풀이(depth 안맞아서 빡쳐서 js로 옮긴거 따로있음)
```js
String.prototype.dropAt = function (index) {

return this.slice(0, index) + this.slice(index + 1, this.length);

};

// "abc".dropAt(1) => "ac"

  

// [1,2,3].filter((_, i) => i !== 1) // [1,3]

// 01234

// "12754"

// "12" + "54"

  

Array.prototype.unique = function unique() {

return Array.from(new Set(this));

};

// [1,2,1,1,4].unique() => [1,2,4]

  

Array.prototype.count = function (predicate) {

let result = 0;

for (let i = 0; i < this.length; i++) {

if (predicate(this[i])) {

result++;

}

}

return result;

};

// [1,2,3,4,5].count(n => n%2 === 0) => 2

  

const isPrime = (n) => {

if (n === 0) return false;

if (n === 1) return false;

  

for (let i = 2; i < Math.sqrt(n + 1); i++) {

if (n % i === 0) {

return false;

}

}

return true;

};

  

function getCases(input) {

// '127'

if (input.length === 1) return [input]; // ['1']

  

if (input.length === 2) {

// '17'

const first = input[0]; // '1'

const second = input[1]; // '7'

return [first, second, first + second, second + first];

}

  

return [...input] // ['1','2','7']

.flatMap((n, i) => getCases(input.dropAt(i)).map((m) => n + m))

.concat([...input]) // ['1', '2', '7']

.unique();

}

  

function solution(numbers) {

return getCases(numbers)

.map((s) => parseInt(s))

.unique() // ['011', '11'] => 11, 11

.count(isPrime);

}

```