## 의상 (LV2)

분류가 해시길래 쫄았는데 빨리 풀렸다.

종류별로 다른 옷을 조합해서 입는거니까 일단 종류별로 분리를 해줘야 해서 dictionary를 사용했다.
각 종류별로 옷을 입을수도 있고 안입을수도 있으니까 옷의갯수+1만큼을 곱해준다.
근데 아예 안입는 경우는 없어야 하니까 1을 빼준다.

``` swift
import Foundation

func solution(_ clothes:[[String]]) -> Int {
    var dic: [String: [String]] = [:]
    
    for c in clothes {
        dic[c[1], default: []].append(c[0])
    }
    
    var ans = 1
    for i in dic.keys {
        ans = ans * (dic[i]!.count + 1)
    }
    
    return ans - 1
}

```

<img width="629" alt="image" src="https://github.com/wavve-algorithm/algorithm/assets/68391767/ee5536bb-bacc-4608-add0-02cfa4409173">
