```python
def flat_map(f, xs):
    ys = []
    for x in xs:
        ys.extend(f(x))
    return ys

def solution(n, lost, reserve):

    lost_set = set(lost)
    reserve_set = set(reserve)
    real_lost = lost_set - reserve_set
    real_reserve = reserve_set - lost_set
    candidate = set(flat_map(lambda s : (s-1, s+1), real_lost))
    rent = real_reserve & candidate

    return n - max(len(real_lost) - len(rent), 0)

n = 5
lost = [2, 4, 5]
reserve = [3, 5]
print(solution(n, lost, reserve))
```

차집합 교집합 구하는 게 이렇게...간단하다니...
flatMap은 직접안깎고 어디서 훔쳐옴