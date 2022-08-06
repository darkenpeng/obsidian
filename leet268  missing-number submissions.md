https://leetcode.com/problems/missing-number/submissions/



```js
const missingNumber = function(nums) {
    nums.sort((a,b)=> a-b)
    let max = Math.max(...nums)
    let min = 0
    const range = Array.from({length : max+1}, (_,i)=> min+i)
	
	//조기리턴
	if(range.length == nums.length){
        return nums.length
    }
    return range.filter((n,i)=> !nums.includes(n))
};


```