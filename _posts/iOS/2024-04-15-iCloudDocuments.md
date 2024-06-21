---
title:  Swift - iCloud Documents 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---

​&nbsp;

[In-Depth Guide to iCloud Documents: Fundamental Setup and File Operations] : <https://fatbobman.com/en/posts/in-depth-guide-to-icloud-documents/>

[Advanced iCloud Documents: Understanding Placeholder Files, Space Optimization, and Operational Techniques] : <https://fatbobman.com/en/posts/advanced-icloud-documents/>

[iCloud를 앱에 통합하는 방법] : <https://developer.apple.com/library/archive/documentation/General/Conceptual/iCloudDesignGuide/Chapters/Introduction.html#//apple_ref/doc/uid/TP40012094-CH1-SW1>

⬇️ 번역

[번역: iCloud 프로그래밍 디자인 가이드 시리즈] : <https://swiftcoding.org/series/icloud-design-guide>

[iOS의 문서 기반 애플리케이션 정보] : <https://developer.apple.com/library/archive/documentation/DataManagement/Conceptual/DocumentBasedAppPGiOS/Introduction/Introduction.html#//apple_ref/doc/uid/TP40011149-CH1-SW1>

[FileManager 사용하면서 알아두면 좋을 것들] : <https://zeddios.tistory.com/441> (선별적으로 정보취할 것)

```swift
//  info.plist 에 추가  (iCloud Drive 에서 파일 보기위한 설정)

<key>NSUbiquitousContainers</key>
    <dict>
        <key>iCloud.com.Jay.Calculendar</key>
        <dict>
            <key>NSUbiquitousContainerIsDocumentScopePublic</key>
            <true/>
            <key>NSUbiquitousContainerSupportedFolderLevels</key>
            <string>Any</string>
            <key>NSUbiquitousContainerName</key>
            <string>공수계산기</string>
        </dict>
    </dict>

```

<br><br><br>

[] : []()

[] : <>

​[]()

​

​

​
