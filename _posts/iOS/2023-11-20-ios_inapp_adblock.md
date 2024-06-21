---
title:  iOS - ios 인앱광고 차단하기 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---
​
​&nbsp;​

[ios 인앱광고 차단하기] : <https://www.eyes.co.kr/mohae/mohae_view/547>
​
​

아이폰 쓰는 사람 중에 인앱 광고 특히 게임 같은 거 할 때 저처럼 인앱 광고 많이 나와서 하기 싫은 사람들 있을 거예요

저는 아이가 좋아하는 무한의 계단이나 애니팡하는데 두세 판마다 인앱 광고가 나와서 검색하다 알게 된 팁 공유합니다.

광고를 차단하는 원리는 광고의 서버접속을 막는 겁니다.

이를 이용하기 위해서 광고 차단을 제공하는 DNS 서버를 사용하도록 수정하는 방법입니다.

AdGuard DNS는 광고를 차단해주는 무료 공개 DNS 서버로 기기에서 DNS 서버로 설정만 해주면 기본적으로 인앱 광고가 차단됩니다.

​

## 적용하기

https://adguard.com/ko/blog/encrypted-dns-ios-14.html

IOS기기 (아이폰/아이패드등)에서 위 사이트 접속 후 " AdGuard DNS 프로파일 " 링크 열기

( 직접 접속 url : https://cdn.adtidy.org/public/Dns/adguard-dns.mobileconfig )

![](https://wimg.eyes.co.kr//resource/mohae/2022/12/c913e74ad512f5711dfa2183bb47f539.png)

​

​

프로파일 다운로드 후

" 이 웹 사이트가 구성 프로파일을 다운로드하려고 합니다. 이 동작을 허용하겠습니까? "

팝업 뜨면 허용 선택

![](https://wimg.eyes.co.kr//resource/mohae/2022/12/4ef8953c66e0e16cc5124d6e2ede5380.png)

이제 아이폰 설정에 들어가면 상단에 프로파일이 다운로드됨이라는 메뉴가 생깁니다.

![](https://wimg.eyes.co.kr//resource/mohae/2022/12/2a29e4ec7709ece4072b078fce0fe990.png)

선택 후 우측상단 설치 선택

설치가 완료되었으면 프로파일 서명자란에 확인 완료 체크가 뜨면 끝입니다.

![](https://wimg.eyes.co.kr//resource/mohae/2022/12/2359b2c90a245e6b7f6d094836b0e2e3.png)

설정 > 일반 > VPN, DNS 및 기기 관리 화면에서 DNS가 Adguard DNS로 되어있는지 확인하고 자동으로 되어있다면

Adguard DNS 로 선택하시면 끝입니다.

DNS 서버 설정 후 주로 사용하는 게임/ 어플에 인앱 광고나 영상으로 뜨는 광고들은 대부분 차단이 됩니다.

다만 인앱에서 광고 시청 후 받을 수 있는 보상등은 못 받게 되니 원하시면 DNS 서버를 자동으로 수정 후인 앱을 종료 후 재접속하시면

정상적으로 광고가 다시 시청됩니다.

안드로이드는 설정 > 기타 연결 설정에서 프라이빗 DNS 공급자 호스트 이름을 선택하신 뒤 

" dns.adguard.com " 으로 입력만 해주시면 더 간단하게 설정 가능합니다.

그럼 이만

​

​

​
