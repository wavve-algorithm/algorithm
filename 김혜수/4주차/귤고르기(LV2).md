## 문제: 귤고르기 (LV2)

개수(k)를 딱히 맞추지 않고 무게의 종류의 개수를 구하면 된다.

가장 많은 종류의 귤이 앞으로 오도록 정렬해서 앞부터 하나씩 개수를 넘지 않도록 채운다.

``` swift
func solution(_ k: Int, _ tangerine: [Int]) -> Int {
    var tmp = [Int: Int]()
    var result = 0
    var count = 0
    for t in tangerine {
        if tmp.keys.contains(t) {
            tmp[t]! += 1
        } else {
            tmp[t] = 1
        }
    }

    let sortedTmp = tmp.sorted(by: {
        $0.value > $1.value
    })

    for s in sortedTmp {
        if count < k {
            count += s.value
            result += 1
        }
    }
    
    return result
}
```
