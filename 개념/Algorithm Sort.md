# `정렬`
: 데이터를 특정한 기준에 따라 순서대로 나열하는 것.

## 선택정렬
: 처리되지 않은 데이터 중에서 가장 작은 데이터를 선택해 맨 앞에 있는 데이터와 바꾸는 것을 반복한다.
마지막 인덱스는 처리하지 않아도 데이터가 정렬을 완료한 상태가 된다.

선택 정렬은 N번 만큼 가장 작은 수를 찾아서 맨앞으로 보내야 한다.
N + (N-1) + (N-2) + ... +2 = N^2 + N - 2 / 2
`시간복잡도` : O(N^2)
```python
array = [1,2,3,8,3,7,6,5,4,8] [7]

for i in range(len(array)):
	min_index = i #가장 작은 원소의 인덱스
		if array[min_index] > array[j]:
			min_index = j
	array[i], array[min_index] = array[min_index] array[i] #swap

# 결과 [0,1,2,3,4,5,6,7,8,9]
```

## 삽입정렬
처리되지 않은 데이터를 하나씩 골라 적절한 위치에 삽입한다.
앞쪽에 있는 item이 정렬되어 있다고 가정하고 1번째 인덱스부터 어떤 위치로 들어갈 지 판단한다.

시간복잡도 : O(N^2).
삽입정렬은 현재 리스트(배열)의 데이터가 거의 정렬되어 있는 상태라면 매우 빠르게 동작한다.
최선의 경우 O(N)의 시간 복잡도를 가진다.
만약 모두 정렬되어 있다고 한다면 item이 어느 위치로 삽입될 지는 선형탐색을 시행하기 때문에 상수시간으로 대체된다.
```python
array = [7,5,9,8,3,1,6,2,4,8]
for i in range(1, len(array)):
	for j in range(i, 0, -1): # 인덱스 i부터 1까지 1씩 감소하며 반복하는 문법
		if array[j] < array[j-1]: #한 칸 시 왼 쪽으로 이동
				array[j], array[j-1] = array[j-1], array[j]
		else: #자기보다 작은 데이터를 만나면 그 자리에서 멈춤
			break
```

## 퀵 정렬
기준 데이터(피벗)를 설정하고 그 기준보다 큰 데이터와 작은 데이터의 위치를 바꾸는 방법
기본적인 퀵 정렬은 첫 번째 데이터를 기준 데이터(Pivot)으로 설정한다.
피벗을 기준으로 데이터 묶음을 나누는 작업을 분할(Divide, Partition)라고 한다.
왼쪽 맨 끝에서부터 피벗값보다 큰 수, 오른쪽 맨 끝에서부터 피벗값보다 작은 수를 골라서 서로 위치를 바꾼다.
만약 바꾸다가 왼쪽에서 피벗값보다 작은수, 오른쪽에서부터 피벗값보다 큰 수를 선택하게 되었을 때(교차), 피벗의 위치와 피벗보다 작은 수의 위치를 바꾸고, 피벗값의 위치가 중간으로 와서 데이터가 분할된다.
시간 복잡도 O(NlogN)
너비 X 높이 = N X logN = NlogN
하지만 최악의 경우 O(N^2)의 시간복잡도를 가진다.
- 첫 번째 원소를 피벗으로 삼을 때, 이미 정렬된 배열에 대해서 퀵 정렬을 수행하면 어떻게 될까?(최악)

```python

arr = [6, 5, 1, 4, 7, 2, 3]
[6,5,1 ,4, 7,2,3]

[1, 2, 3] 4 [5, 6, 7]

def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    lesser_arr, equal_arr, greater_arr = [], [], []
    for num in arr:
        if num < pivot:
            lesser_arr.append(num)
        elif num > pivot:
            greater_arr.append(num)
        else:
            equal_arr.append(num)
    return quick_sort(lesser_arr) + equal_arr + quick_sort(greater_arr)
```
