---
title:  Swift - contains 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---

[ 문자열"AGZ"이 문자열배열 ["A","B","C","D"]의 어떤 값이라도 갖는지 탐색] : <https://stackoverflow.com/questions/52711049/detect-if-string-contains-any-element-of-a-string-array>

ex. 문자열 "house near the beach" 가 문자열(String)배열 ["beach", "water", "view", "ocean", "close"] 중 하나의 값이라도 갖는지 탐색

[] : []()

[] : <>

```swift
if "토트넘 전직 동료 케인 손흥민과 유로파리그 맞대결!" has any element of ["SON","손흥민" ,"이강인","김민재","류현진"] ?

let title = "토트넘 전직 동료 케인 손흥민과 유로파리그 맞대결"
let inputString = "SON,손흥민,이강인,김민재,류현진"
var words = [Substring]()
words = inputString.split(separator: ",") //  ["SON", "손흥민" , "이강인", "김민재", "류현진"]

let haveWord:Bool = title.contains(words)

extension String {
    func contains(_ strings: [String]) -> Bool {
        strings.contains { contains($0) }
    }
    func contains(_ strings: [Substring]) -> Bool {
        strings.contains { contains($0) }
    }
}
```
