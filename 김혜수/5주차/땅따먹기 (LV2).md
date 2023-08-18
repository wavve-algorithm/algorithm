## 땅따먹기 (LV2)

<img width="671" alt="스크린샷 2023-08-18 오전 1 12 24" src="https://github.com/wavve-algorithm/algorithm/assets/68391767/d886b859-361f-428b-9544-590d71b2274d">


마지막 라인까지 가서 마지막 라인에서 최댓값을 구해주면 되는 문제다. 그래서 최댓값을 계속 저장해가면서 마지막 라인에 도달한 값들끼리 최댓값을 더해주면 되지 않을까? 라는 생각이 들어 dp로 풀었다. 2차원 dp로 풀면된다. \
근데 테케 하나가 런타임 에러가 나서 n==1일때 예외처리 추가해주니까 됨 (for i in 1..<land.count에서 걸린듯)

``` swift
func solution(_ land:[[Int]]) -> Int{
    var d: [[Int]] = land
    let n = land.count
    
    if n == 1 {
        return d[0].max()!
    }
    
    for i in 1..<land.count {
        for j in 0..<4 {
            switch j {
            case 0:
                d[i][j] += max(d[i-1][1], d[i-1][2], d[i-1][3])
            case 1:
                d[i][j] += max(d[i-1][0], d[i-1][2], d[i-1][3])
            case 2:
                d[i][j] += max(d[i-1][1], d[i-1][0], d[i-1][3])
            case 3:
                d[i][j] += max(d[i-1][1], d[i-1][2], d[i-1][0])
            default:
                break
            }
        }
    }

    return d[n-1].max()!
}
```
