## 하샤드 수 (Lv1)

Character는 Int로 바로 변환이 안된다!!!!!!! String으로 바꿔줘야 변환됨 (첨알았음)

``` swift
func solution(_ x:Int) -> Bool {
    let k = String(x)
    var sum = 0
    for i in k {
        sum += Int(String(i))!
    }
    return x % sum == 0
}
```
