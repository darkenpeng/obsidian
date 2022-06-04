```js
function solution(answers) {
  
    const first= [1,2,3,4,5]
    const second = [2,1,2,3,2,4,2,5]
    const third = [3,3,1,1,2,2,4,4,5,5]
    

    const correct = [
        {first : []},
        {second : []},
        {third : []},
         
    ]
        for(let i = 0; i<answers.length; i++){
            i = i % first.length
            if(first[i] === answers[i]){
            correct[0].first.push(first[i])
            }
        }
            
        for(let i = 0; i<answers.length; i++){
            i = i % second.length
            if(second[i] === answers[i]){
            correct[1].second.push(second[i])

            }
        }
        
        for(let i = 0; i<answers.length; i++){
            i = i % third.length
            if(third[i] === answers[i]){
            correct[2].third.push(third[i])
        }
            
        }
        return correct.sort((a,b)=> b.length - a.length)
        
    }
```