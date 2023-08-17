## 나누어 떨어지는 숫자 배열 (LV1)

ㅋㅋ 문제 잘못읽어서 세번이나 틀림

``` swift
func solution(_ arr:[Int], _ divisor:Int) -> [Int] {
    let answer = arr.filter { $0 % divisor == 0 }.sorted()
    if answer.isEmpty { return [-1] }
    return answer
}
```
