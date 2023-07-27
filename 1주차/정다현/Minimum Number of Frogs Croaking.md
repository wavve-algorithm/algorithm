- 처음엔 croaks를 dict가 아니라 list로 관리했는데
- 이러면 index 찾을 때 시간초과가 남

```python
from collections import defaultdict
class Solution:
    def minNumberOfFrogs(self, croakOfFrogs: str) -> int:

        CROAK = 'croak'
        CROAK_INDEX = {
            'c': 0,
            'r': 1,
            'o': 2,
            'a': 3,
            'k': 4
        }

        # 진행 중인 croak을 관리
        croaks = defaultdict(int)
        max_frogs = 0
        curr_frogs = 0

        for l in croakOfFrogs:
            idx = CROAK_INDEX[l]
            if (idx == 0): # 'c'일 경우. 신규 개구리
                croaks[idx] += 1
                curr_frogs += 1
                max_frogs = max(max_frogs, curr_frogs)
            else:
                if (croaks[idx - 1] == 0): return -1 
                croaks[idx - 1] -= 1
                if (idx == 4): # 'k'일 경우.
                    curr_frogs -= 1
                else:
                    croaks[idx] += 1

        for i in range(4): # 남은 게 있는지 확인
            if (croaks[i] != 0): return -1

        return max_frogs

```
