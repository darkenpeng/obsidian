```jsx
function solution(s){
    const stack = [];
    
    for(let i = 0; i<s.length;i++){
        if(s[0] == ")"){
            return false
        }
        if(s[s.length - 1] == "("){
            return false
        }
        if (s[i] == "("){
            stack.push(s[i])
            
            if(s[i] == ")"){
                stack.shift()
            }
            
        }
        //console.log(stack)
        return stack.length == 1 ? true : false
        
    }
}
```

```jsx
테스트 1 〉	통과 (0.05ms, 30.1MB)
테스트 2 〉	통과 (0.05ms, 29.9MB)
테스트 3 〉	통과 (0.05ms, 30MB)
테스트 4 〉	통과 (0.12ms, 30MB)
테스트 5 〉	실패 (0.06ms, 29.8MB)
테스트 6 〉	통과 (0.05ms, 30MB)
테스트 7 〉	통과 (0.06ms, 30.1MB)
테스트 8 〉	통과 (0.06ms, 29.8MB)
테스트 9 〉	통과 (0.07ms, 30.1MB)
테스트 10 〉	통과 (0.06ms, 29.9MB)
테스트 11 〉	실패 (0.06ms, 30.1MB)
테스트 12 〉	통과 (0.08ms, 29.9MB)
테스트 13 〉	통과 (0.07ms, 30MB)
테스트 14 〉	통과 (0.08ms, 30.1MB)
테스트 15 〉	통과 (0.08ms, 30MB)
테스트 16 〉	통과 (0.09ms, 30MB)
테스트 17 〉	실패 (0.08ms, 29.9MB)
테스트 18 〉	통과 (0.08ms, 30.2MB)
효율성  테스트
테스트 1 〉	통과 (35.31ms, 34.8MB)
테스트 2 〉	실패 (시간 초과)
```

# 2트

```jsx
function solution(s){
    const stack = [];

    if(s[0]== ")"|| s[s.length - 1] == "("){
        return false
    }
    for(const c of s){
        if(c == "("){
           stack.push(1) 
        }
        if(c == ")"){
            stack.pop()
        }
        
    }
   return stack.length == 0 ? true : false
        
}
```

```jsx
테스트 1 〉	통과 (0.05ms, 29.9MB)
테스트 1 〉	통과 (0.05ms, 29.9MB)
테스트 2 〉	통과 (0.05ms, 30.1MB)
테스트 3 〉	통과 (0.05ms, 30.1MB)
테스트 4 〉	통과 (0.05ms, 30.1MB)
테스트 5 〉	통과 (0.05ms, 29.8MB)
테스트 6 〉	통과 (0.06ms, 30MB)
테스트 7 〉	통과 (0.06ms, 30.1MB)
테스트 8 〉	통과 (0.06ms, 30MB)
테스트 9 〉	통과 (0.07ms, 29.8MB)
테스트 10 〉	통과 (0.06ms, 29.8MB)
테스트 11 〉	통과 (0.06ms, 30.1MB)
테스트 12 〉	통과 (0.09ms, 30MB)
테스트 13 〉	통과 (0.08ms, 29.7MB)
테스트 14 〉	통과 (0.08ms, 30MB)
테스트 15 〉	통과 (0.14ms, 30MB)
테스트 16 〉	통과 (0.08ms, 30.1MB)
테스트 17 〉	통과 (0.11ms, 30.1MB)
테스트 18 〉	통과 (0.06ms, 30MB)
효율성  테스트
테스트 1 〉	통과 (8.04ms, 35.4MB)
테스트 2 〉	통과 (7.53ms, 35.1MB)
```

8/17다시풂
```js
function solution(s){
    const stack =[];
    if (s[0] == ')'){
      return false;  
    } 
    for(const c of s){
        if( c === '('){
            stack.push(c)
        }
        if(c===')'){
            stack.pop()
        }
    }
    return stack.length === 0 ? true : false
}
```