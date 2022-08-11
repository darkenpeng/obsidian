https://leetcode.com/problems/majority-element/submissions/
```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
    const N = nums.length
    const map = new Map();
    
    for(const num of nums){
        map.set(num, (map.get(num) || 0 ) + 1)
    }
    
    const maxFreq = Math.max(...map.values())
    return [...map.keys()].find((n)=> map.get(n) === maxFreq)

};
```