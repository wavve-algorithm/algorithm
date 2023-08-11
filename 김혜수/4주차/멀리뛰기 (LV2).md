## 문제. 멀리뛰기 (LV2)

처음엔 조합의 합을 써야하나 했는데 피보나치 문제였음

%1234567을 마지막에만 하면 중간에 오버플로우가 생긴다.

``` swift
import Foundation

func solution(_ n: Int) -> Int {
    
    var array = Array<Int>(repeating: 0, count: n+1)
    
    if n <= 3 {
        return n
    }
    
    array[1] = 1
    array[2] = 2
    
    for i in 3...n {
        array[i] = (array[i-1] + array[i-2]) % 1234567
    }

    return array[n]
}
```
