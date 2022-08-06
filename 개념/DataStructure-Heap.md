>파이썬 알고리즘 인터뷰

# 힙(Heap)이란? 
> 힙은 힙의 특성(최소 힙 Min Heap)에서는 부모가 항상 자식보다 같거나 같다)을 만족하는 거의 완전한 트리(Almost complete Tree)인 특수한 트리 기반의 자료구조다.

힙은 그래프나 트리와는 전혀 관계 없어 보이는 독특한 이름과 달리, **트리 기반의 자료구조**다.
파이썬에서는 heapq 모듈이 힙으로 구현되어 있으며, 그 중에서도 파이썬에는 최소 힙만 구현되어 있다. 최소 힙은 부모가 항상 자식보다 작기 떄문에 루트가 결국 가장 작은 값을 갖게 되며, 우선순위 큐에서 가장 작은 값을 추출하는 것은 매번 힙의 루트를 가져오는 형태로 구현된다.

힙은 정렬된 구조가 아니다. 최소 힙의 경우 부모 노드가 항상 자식 노드보다 작다는 조건만 만족할 뿐, 서로 정렬되어 있지 않다. 예를 들면 오른쪽의 자식 노드가 레벨 차이에도 불구하고, 왼쪽 노드보다 더 작은 경우도 있을 수 있다. 부모, 자식간의 관계만 정의할 뿐, 좌우에 대한 관계는 정의하지 않기 때문이다.
자식이 둘인 힙은 특별히 `이진 힙(Binary Heap)`이라고 하며 대부분은 이진 힙이 널리 사용된다. 완전 이진트리형태인 이진 힙은 배열에 빈틈없이 배치가 가능하며, 대개 트리의 배열 표현의 경우 계산을 편하게 하기 위해 인덱스는 1부터 사용한다.

# 힙 연산
## 삽입
업힙 연산은 percolate_up()이라는 함수로 정의한다.
1. 요소를 가장 하위 레벨의 최대한 왼쪽으로 삽입한다. (배열로 표현할 경우, 가장 마지막에 삽입한다.)
2. 부모 값과 비교해 값이 더 작은 경우 위치를 변경한다.
3. 계속해서 부모 값과 비교해 위치를 변경한다. (가장 작은 값일 경우 루트까지 올라감)

```python
def _percolate_up(self):
	i = len(self)
	# 파이썬에서 // 연산자 : 기존 왼쪽 변수 값과 오른쪽 변수로 나눈 후 내림한 값
	parent = i // 2
	while parent > 0:
		if self.items[i] < self.items[parent]:
			self.items[parent], self.items[i] = self.items[i], self.items[parent]
			i = parent
			parent = i // 2
```
## 추출
다운힙 연산은 percolate_down()이라는 함수로 정의한다.
추출의 시간복잡도는 O(log n)이다. 루트를 추출하면 되지만 추출 이후 다시 힙의 특성을 유지하는 작업이 필요하기 때문이다.
1. 루트를 추출한다.
2. 비어있는 루트에 가장 마지막 요소가 올라간다.
3. 자식노드와 값을 비교해서 자식보다 크다면 내려간다.
```python
#최소 힙인 상황!
def _percolate_down(self, idx):
	left = idx * 2
	right = idx * 2 + 1
	smallest = idx
	
	# 왼쪽과 오른쪽을 비교해 더 작다면 해당 인덱스로 교체한다!
	if left <= len(self)and self.items[left] < self.items[smallest]:
		smallest = left

	if right <= len(self) and self.items[right] < self.items[smallest]:
		smallest right


	#

	if smallest != idx:
		self.items[idx]. self.items[smallest] = self.items[smallest], self.items[idx]
		self._percolate_down(smallest)


def extract(self):
	extracted = self.items(1)
	self.items[1] = self.items[len(self)]
	self.items.pop()
	self._percolate_down(1)
	return extracted
```

## 이진 힙 vs 이진탐색트리(BST)
힙은 상/하 관계를 보장하고, 이진탐색트리(BST)는 좌우관계를 보장한다.
특히 최소 힙에서는 부모가 자식보다 작다. **가장 작은 값을 추출하거나, 가장 큰 값을  추출하려고 할 때 이진 힙을 사용**한다. 이 때 최대/최솟값을 찾는 연산의 시간복잡도는 O(1)이다.
이진탐색트리에서는 부모는 왼쪽 자식보다는 크며, 오른쪽 자식보다는 작거나 같다. 이 때문에 탐색과 삽입 모두 O(log n)에 가능하며 **모든 값이 정렬되어야 할 때 사용**한다.

