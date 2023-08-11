## 문제. 뒤에 있는 큰 수 찾기 (LV2)

처음에 이중 for문 돌렸다가 시간초과 남 → stack을 이용해서 해결함

스택에는 아직 뒤에서 더 큰 수를 찾지 못한 아이들의 index값이 들어감

예시) [2, 3, 3, 5], stack = [], answer = [-1, -1, -1, -1]

stack 괄호뒤에는 편의상.. numbers[인덱스]값 씀

step1) index = 0

stack = [0(2)], answer = [-1, -1, -1, -1]

step2) index = 1 → 값은 3

1. stack마지막값과 비교
    1. 2 < 3 (마지막값이 더 작음)
    2. answer[stack.last!]를 현재 값으로 바꿔줌 (answer = [3, -1, -1, -1])
    3. 찾았으니까 stack에서 pop 해줌
    4. 이걸 스택에 값이 다 없어지거나 이미 스택에 있는게 더 클때까지 하고 지금값 스택에 넣어줌

stack = [1(3)], answer = [3, -1, -1, -1]

step3) index = 2 → 값은 3

스택 마지막 값과 비교했는데 3=3 이니까 스택에 넣고 넘기기

stack=[1(3), 2(3)], answer = [3, -1, -1, -1]

step4) index = 3 → 값은 5

스택 마지막값과 비교 1) 3<5 니까

stack[1(3)], anwer = [3, -1, 5, -1]

비교2) 또 3<5니까

stack[], answer = [3, 5, 5, -1]

이제 없으니까 비교 끝

stack[5]

이제 더 뒤에 없으니까 그냥 끝남

``` swift
import Foundation

func solution(_ numbers: [Int]) -> [Int] {
    var stack: [Int] = []
    var answer = Array<Int>(repeating: -1, count: numbers.count)
    
    
    for i in 0..<numbers.count {
        if stack.count == 0 {
            stack.append(i)
            continue
        }
        while stack.count != 0 {
            if numbers[stack.last!] < numbers[i] {
                answer[stack.last!] = numbers[i]
                stack.removeLast()
                continue
            } else { break }
        }
        stack.append(i)
    }
    
    return answer
}
```
