---
title:  Swift - 고차함수 Map, Filter, Reduce 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---

​&nbsp;​

[Swift :: 고차함수 - Map, Filter, Reduce 알아보기] : [Swift :: 고차함수 - Map, Filter, Reduce 알아보기](https://shark-sea.kr/entry/Swift-%EA%B3%A0%EC%B0%A8%ED%95%A8%EC%88%98-Map-Filter-Reduce-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0)


[Swift : 클로저기초 및 고차함수 (map, filter, reduce)] : [Swift : 기초문법 클로저 및 고차함수 (map, filter, reduce)](https://seons-dev.tistory.com/entry/Swift-%ED%81%B4%EB%A1%9C%EC%A0%80-%EB%B0%8F-%EA%B3%A0%EC%B0%A8%ED%95%A8%EC%88%98map-filter-reduce)


[Swift3 : map개념 / String을 Int로 변환하는 방법] : <https://zeddios.tistory.com/72>

```swift
// map
let numArray = [1,3,5,7,9]
let multiArray = numArray.map { $0 * 2 }
print(multiArray)
// [2, 6, 10, 14, 18]


// filter
let stringArray = ["가수", "대통령", "개발자", "선생님", "의사", "검사", "건물주"]
let threeCountArray = stringAttay.filter { $0.count == 3 }
print(threeCountArray)
// ["대통령", "개발자", "선생님", "건물주"]


// reduce
let numberArray = [1,2,3,4,5,6,7,8,9,10]
let sum = numberArray.reduce(0) { $0 + $1 }
print(sum)
// 55

// String 가져와 숫자배열로 바꾸기
let stringInput = "6,2,11,9"
var stringArray = stringInput.split(separator: ",")     //  ["6", "2", "11", "9"]
var numberArray = stringArray.map { Int($0)! }          //  [6, 2, 11, 9]
// numberArray.sort()                                   //  [2, 6, 9, 11]
var sortedArray = numberArray.sorted()                  //  [2, 6, 9, 11]

// map 반복 사용시
let strToInt: (Substring) -> Int = { Int($0) ?? 9999 }  //  .map() 사용 위함 -> String을 Int로 변환해줌
var stringArray = stringInput.split(separator: ",").map(strToInt)
```

​

​

​
