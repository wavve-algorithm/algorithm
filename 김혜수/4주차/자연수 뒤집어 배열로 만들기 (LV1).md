## 문제. 자연수 뒤집어 배열로 만들기 (LV1)

LV1이지만, 마지막 케이스에서 시간초과가 남.. ㄹㅇ 정직하게 뒤집음

``` swift
func solution(_ n: Int64) -> [Int] {
    let n = String(n)
    var answer: [Int] = []
    for i in 1...n.count {
        let idx = n.count - i
        let stringIdx = n.index(n.startIndex, offsetBy: idx)
        answer.append(Int(String(n[stringIdx]))!)
    }
    return answer
}
```

해결방법 -> reversed를 써준다. reversed()는 시간복잡도가 O(1)이라고 함.. 우와.. 첨알았음.


``` swift
func solution(_ n: Int64) -> [Int] {
    let n = Array(String(n))
    let a = n.reversed() as [Character]
    return a.map { Int(String($0))! }
}
```
