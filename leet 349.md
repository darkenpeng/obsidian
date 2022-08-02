```js
const unique = function(arr){
   return Array.from(new Set(arr))
}
var intersection = function(nums1, nums2) {
    return unique(nums1).filter((o)=> unique(nums2).includes(o))
};
```