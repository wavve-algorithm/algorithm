#### 풀이 1. 풀이 제목
(LV2) 롤케이크 자르기 https://school.programmers.co.kr/learn/courses/30/lessons/132265

1. toppings 배열을 앞에서 하나씩 돌면서 Set을 이용해서 중복을 제거하고 .count를 해서 개수 같으면 answer += 1 => 시간초과남
2. 철수가 모두 가지고 있다가 동생이 하나씩 뺏는다고 생각하면서 계산해준다. -> 해결



``` swift 
func solution(_ toppings: [Int]) -> Int {
    var answer = 0
    var dic = [Int: Int]()
    var rightDic = [Int: Int]()
    
    for topping in toppings {
        dic[topping, default: 0] += 1
    }
    
    var leftCount = dic.keys.count
    var rightCount = 0
    
    for (idx, topping) in toppings.enumerated() {
        dic[topping]! -= 1
        if rightDic[topping] == nil {
            rightCount += 1
            rightDic[topping] = 1
        } else {
            rightDic[topping, default: 0] += 1
        }
    
        if dic[topping]! == 0 {
            leftCount -= 1
        }
        
        if leftCount == rightCount {
            answer += 1
        }
        
    }
    return answer
}
```

<img width="546" alt="image" src="https://github.com/wavve-algorithm/algorithm/assets/68391767/fc6739b8-6325-4b14-80a7-05ce30dc83fe">


--- 

#### 새롭게 알게된 점
+ (있으면 작성)

#### 어려웠던 점
+ (있으면 작성)
