---
title:  Swift - 이미지 하나로 기본 애니메이션 효과주기 (CABasicAnimation) 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---
<br>

[CABasicAnimation] : <https://developer.apple.com/documentation/quartzcore/cabasicanimation>

[Swift - Png 한장으로 애니메이션 효과주기 CABasicAnimation] : <https://hooni99918.tistory.com/78>
​
<br><br><br>
​
[공식문서](https://developer.apple.com/documentation/quartzcore/cabasicanimation)에는 총 4가지가 기술되어 있습니다.

1.Opacity를 설정하거나

```swift
let animation = CABasicAnimation(keyPath: "opacity") 
animation.fromValue = 0 
animation.toValue = 1
```


2.배경색깔을 변경하거나

```swift
let animation = CABasicAnimation(keyPath: "backgroundColor")
animation.fromValue = NSColor.red.cgColor
animation.toValue = NSColor.blue.cgColor
```


3.위치를 변경하거나(왼쪽에서 오른쪽처럼)

```swift
let animation = CABasicAnimation(keyPath: "position")
animation.fromValue = [0, 0]
animation.toValue = [100, 100]
```


4.크기를 변경하거나

```swift
let animation = CABasicAnimation(keyPath: "transform.scale.x")
animation.fromValue = 1
animation.toValue = 2
```


등의 기능을 지원합니다.

어려운 내용이 아니다보니 실사용 코드로 확인해보겟습니다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbgOLhN%2Fbtsiwk7Dy0v%2FN57GWRRxu49hGB9cz6h9S0%2Fimg.png){: .align-center}

간단하게 스토리보드에 이미지뷰를 올려주고 3xPng 사진을 넣었습니다.

공통 기본사항
```swift
//ViewdidLoad
shakeAnimation(imageView: PresentImage)
```
viewDidLoad 에 사용될 func를 지정해 줍니다.
 

1.투명해지기
```swift
//투명해지기
    func shakeAnimation(imageView: UIImageView) {
        let animation = CABasicAnimation(keyPath: "opacity")
        animation.fromValue = 1.0 // 완전 불투명
        animation.toValue = 0.0 // 완전 투명
        animation.duration = 3 // 1초 동안
        imageView.layer.add(animation, forKey: "opacity")

    }
```

결과물

<center>
    <img src="https://blog.kakaocdn.net/dn/bFXdcQ/btsiusrQzbq/Nd5M2kDivmkKqRMC2LqpTK/img.gif" width="50%" height="50%" title="title" alt="alt"/> 
</center>


2.위치변경(좌우로)
```swift
 func shakeAnimation(imageView: UIImageView) {
        let animation = CABasicAnimation(keyPath: "position")
        animation.duration = 0.1
        animation.repeatCount = 40
        animation.autoreverses = true
        animation.fromValue = NSValue(cgPoint: CGPoint(x: imageView.center.x - 30, y: imageView.center.y))
        animation.toValue = NSValue(cgPoint: CGPoint(x: imageView.center.x + 30, y: imageView.center.y))
        imageView.layer.add(animation, forKey: "position")
    }
```

결과물

<center>
    <img src="https://blog.kakaocdn.net/dn/cuAJjO/btsiyUU61eC/9YpZk8Gk6JkmnVCiURfL7k/img.gif" width="50%" height="50%" title="title" alt="alt"/> 
</center>
 

3.돌려돌려돌림판

```swift
   func shakeAnimation(imageView: UIImageView) {
    let animation = CABasicAnimation(keyPath: "transform.rotation")
    animation.fromValue = 0 // 시작 각도
    animation.toValue = Double.pi * 200 // 360도 회전
    animation.duration = 50 // 1초 동안
            imageView.layer.add(animation, forKey: "rotation")
}
```

결과물

<center>
    <img src="https://blog.kakaocdn.net/dn/cHfAtc/btsiBJyZrWd/Fazq13ITGVyYZSzKUTLSw1/img.gif" width="50%" height="50%" title="title" alt="alt"/> 
</center>


4.점점 커지는 이미지

```swift
    func shakeAnimation(imageView: UIImageView) {
        let animation = CABasicAnimation(keyPath: "transform.scale")
        animation.fromValue = 1.0 // 원래 크기
        animation.toValue = 10.0 // 2배로 확대
        animation.duration = 10 // 1초 동안
        imageView.layer.add(animation, forKey: "scale")
    }
```

결과물

 


번외

다 합쳣을때

```swift
  func shakeAnimation(imageView: UIImageView) {
        
    // Position Animation
    let positionAnimation = CABasicAnimation(keyPath: "position")
    positionAnimation.fromValue = NSValue(cgPoint: CGPoint(x: 250, y: 250))
    positionAnimation.toValue = NSValue(cgPoint: CGPoint(x: 120, y: 130))
    
    // Scale Animation
    let scaleAnimation = CABasicAnimation(keyPath: "transform.scale")
    scaleAnimation.fromValue = 1.0
    scaleAnimation.toValue = 10.0
    
    // Rotation Animation
    let rotationAnimation = CABasicAnimation(keyPath: "transform.rotation")
    rotationAnimation.fromValue = 0
    rotationAnimation.toValue = Double.pi * 200
    
    // Opacity Animation
    let opacityAnimation = CABasicAnimation(keyPath: "opacity")
    opacityAnimation.fromValue = 1.0
    opacityAnimation.toValue = 0.0
    
    // Animation Group
    let animationGroup = CAAnimationGroup()
    animationGroup.animations = [positionAnimation, scaleAnimation, rotationAnimation, opacityAnimation]
    animationGroup.duration = 10 // 모든 애니메이션을 1초 동안 수행
    animationGroup.fillMode = .forwards // 애니메이션 완료 후 상태 유지
    animationGroup.isRemovedOnCompletion = false // 애니메이션 완료 후 제거하지 않음
    
    imageView.layer.add(animationGroup, forKey: "myAnimationGroup")
}
```

코드를 커스텀해서 원하는 결과물을 얻어보아요
