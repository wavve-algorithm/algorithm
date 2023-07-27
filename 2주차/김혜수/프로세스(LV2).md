#### 문제 1. 프로세스 (LV2)

##### 풀이 설명 & 과정 (또는 코드 중간에 주석 작성)

하나씩 인덱스를 돌면서 그 인덱스 부분이 가장 큰 우선순위를 가지고 있으면, -1로 바꾼다.

결국 몇번째 처리되는지가 중요하기 때문에 -1로 바꿀때마다 answer를 +1 해준다

인덱스 부분과 location부분이 동일하면 해당 location의 작업이 수행된 것이므로 반복문을 멈추고 그 때가 몇번째인지를 리턴해준다.

##### 코드

``` swift
import Foundation

func solution(_ priorities: [Int], _ location: Int) -> Int {
    var index = 0
    var answer = 0
    var tmpPriorities = priorities
    
    while true {
        if tmpPriorities.max() == priorities[index] {
            tmpPriorities[index] = -1
            answer += 1
            if location == index {
                break
            }
        }
        index = (index+1) % priorities.count
    }
    
    return answer
}
```
