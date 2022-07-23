```jsx
// 풀이과정
function solution(bridge_length, weight, truck_weights) {
  const bridge = Array.from({length: bridge_length}, ()=> 0);
	//[0,0]
  let time = 0;

  while (bridge.length) {
    bridge.shift(); // 다리 끝 트럭이 있으면... 도착지에 내려준다
		// [0]
		// go
    time += 1;

    if (truck_weights.length) { // 아직 못 건넌 트럭이 있으면

			// 다리에 올라간 모든 트럭의 무게
      let sum = bridge.reduce((acc, cur) => acc + cur);

			// 새 트럭이 올라가도 한계 하중을 넘지 않으면...
      if (sum + truck_weights[0] <= weight) {
				// truck_weights에서 트럭을 빼서... 다리에 올린다
        bridge.push(truck_weights.shift());
				// [0,5]
      } else {
        bridge.push(0);
				// [8,0]
      }
    }
  }

  return time;
}
```