### 커비한 풀이1
```js
const isValid = function(s) {
    const open = ["(", "[", "{"];
    const openClose = {
        "(" : ")",
        "[" : "]",
        "{" : "}",
    }
    const stack = [];

    for (const c of s) {
        if (open.includes(c)) {
          stack.push(c);
    } else {
        const last = stack.pop();   
        if (openClose[last] !== c){
            return false
        }
    }
        
    }

    return stack.length == 0
}
```

### 커비한 풀이2
```js
	const openClose = {
    	"(" : ")",
    	"[" : "]",
    	"{" : "}",
	}

	const stack = [];

	const isValid = function(s) {
    	for(const c of s){
        	if(c in openClose){
            	stack.push(c)
        	} else {
            	const last = stack.pop()
            	if(openClose[last]!= c){
                	return false
            	}
        	}
    	} return stack.length === 0  
}
```