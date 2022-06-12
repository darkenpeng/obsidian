# 냅다 풀은 풀이
```js

    var twoSum = function(nums, target) {
        //두개를 뽑는다
        //reduce로 더한다
        // target과 같으면 그 두 개의 인덱스를 리턴한다
        
        for(let i = 0; i<nums.length;i++){
            for(let j = i+1; j<nums.length;j++){
                if(nums[i]+nums[j] === target){
                    return [i,j]
                }
                
            }
            
        }
    };
```
