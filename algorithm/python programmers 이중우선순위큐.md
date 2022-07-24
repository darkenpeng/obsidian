```python
import heapq

def solution(operations):
    # 최소힙
    heap = []
    for exp in operations:
        command, number = exp.split(' ')
        if command == 'I':
            heapq.heappush(heap, int(number))
        if command == 'D':
            if len(heap) != 0:
                if number == "1":
                    heap.remove(max(heap))
            # D -1일 때
                else:
                    heapq.heappop(heap)
    
    if(len(heap) == 0):
        return [0,0]
    else:
        return [max(heap), min(heap)]
```
