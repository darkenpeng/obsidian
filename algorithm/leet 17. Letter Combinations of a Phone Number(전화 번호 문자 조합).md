```javascript
    const alphabet = {
        "2" : 'abc',
        "3" : 'def',
        "4" : 'ghi',
        "5" : 'jkl',
        "6" : 'mno',
        "7" : 'pqrs',
        "8" : 'tuv',
        "9" : 'wxyz',
    }
    
var letterCombinations = function(digits) {
    const digitList = digits.split('').map((char, _)=> Number(char))
    //const empty = ""
    const charsList = digitList.map((d, i)=> alphabet[d].split(''))
    //"123".split('').map((v,i)=> [4,5,6].map((e)=> e + v)).flat()
    //['41', '51', '61', '42', '52', '62', '43', '53', '63']
    if(digits.length === 0) {
        return [];
    } 
    
    if(digits.length === 1){
        return alphabet[digits].split('')
    }
    if(digits.length ===2) {
        return charsList[0].map((v)=> charsList[1].map((e)=> v+e)).flat()
        
    }
   return charsList[0].map((v)=> letterCombinations(digits.slice(1)).map((e)=> v+e)).flat()
    
    
};
```
https://leetcode.com/problems/letter-combinations-of-a-phone-number/submissions/
