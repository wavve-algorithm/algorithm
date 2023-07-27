### Task Scheduler

링크: https://leetcode.com/problems/task-scheduler

```python
from collections import Counter, deque
import heapq
class Solution:
    def leastInterval(self, tasks: List[str], n: int) -> int:

        tasksCountMap = dict(Counter(tasks))
        print(tasksCountMap)

        t = 0
        q = [(-val, 0, item) for item, val in tasksCountMap.items()]

        heapq.heapify(q)

        # heap에 삽입할 때 (-갯수(많은 순), 마지막 실행 시간, task)
        # 10000 * 100

        t = 0
        while (q):
            t += 1
            # 다음에 실행할 거 선택
            _next = None
            for i in range(len(q)):
                if (q[i][1] == 0 or t - q[i][1] > n):
                    _next = q[i]
                    break

            if (_next is None):
                continue

            # heapq에서 빼내기
            popped = []
            while (q):
                _last = heapq.heappop(q)
                if (_last == _next): break
                popped.append(_last)

            # 앞에서 빼낸 거 다시 삽입
            for el in popped:
                heapq.heappush(q, el)

            if (_next[0] == -1): continue
            heapq.heappush(q, (_next[0]+1, t, _next[2]))


        return t
```
