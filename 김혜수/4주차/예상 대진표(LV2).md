#### 문제 1. 예상 대진표

<img width="707" alt="image" src="https://github.com/wavve-algorithm/algorithm/assets/68391767/8b0571e9-07de-4b05-89a7-c0b81af45d8d">

둘로 나누면 같아지는 지점에 둘이 붙는다. 같아질때까지 2로 나눔

``` swift
import Foundation

func solution(_ n:Int, _ a:Int, _ b:Int) -> Int
{
    var answer = 0
    var nextA = a
    var nextB = b

    repeat {
        nextA = (nextA + 1) / 2
        nextB = (nextB + 1) / 2
        answer += 1
    } while nextA != nextB

    return answer
}
```

