# 풀이
```js
var findKthLargest = function(nums, k) {
	return nums.sort((a,b)=> b-a)[k-1] 
}
```

이 문제가 힙인 이유?