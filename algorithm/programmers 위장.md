```JS
// #psudo
// # [1]
// [["yellowhat", "headgear"], ["bluesunglasses", "eyewear"], ["green_turban", "headgear"]]
// 2차원 배열의 1번째 index가 key, value는 여러 개 
// 카운터를 만들어서 
// 2차원 배열을 돌면서 각 e의 1번째 index를 key, 0번째 index를 value로 가지는 
// 카운터를 만들어서 옷의 개수를 value로 만들고 
// # [2] 
// 경우의 수 구하기 
// - 1개 선택하는 경우의 수 
// 2C1+1C1 => 3 // = 2*1/1 + 1*1/1 = 3 // - 2개 선택하는 경우의 수 // 2C2 => 2 // = 2*2/2 = 2 // 총합 = 2+3 = 5 //... // 하지만 그 선택하는 n번째가 counter의 value의 제일 큰수보다 작아야 함(루프 끝나는 기준)
```

```JS
// for (const cloth of clothes) {
// clothesMap.set(cloth[1], (clothesMap.get(cloth[1])+1))
// }
// => function extract

const counter = (outerArray, mapName) => {

// entry... value key 순서가 거꾸로!
// 어떤 배열인지 ? 의미가 안보임
// item category
// 구조 분해 할당을 하는게 더 깔끔할 것 같음! (라도님)
// 성능이슈...

	for (const innerArray of outerArray) {

	return mapName.set(innerArray[1], (mapName.get(innerArray[1]) || 0) + 1);

	}
};

const clothesCounter = counter(clothes, clothesMap);
console.log(clothesCounter); // Map { 'headgear' => 1 }

// clothes.length로 루프를 돌리면 될 듯?!
```

```JS

function solution(clothes) {
    const clothesMap = new Map();
    for (const [cloth, kind] of clothes){
    clothesMap.set(kind,(clothesMap.get(kind)||0)+ 1)

	}
    // 경우의 수
    const clothesArr = [...clothesMap]
    const cases = clothesArr.map((cloth)=>cloth[1]+1).reduce((a,b)=> a*b)
    return cases -1
}
```
![[Pasted image 20220510171646.png]]