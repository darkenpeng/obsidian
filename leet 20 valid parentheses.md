
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