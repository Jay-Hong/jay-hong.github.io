---
title:  Swift - View 하나로 기본 애니메이션 효과주기 (CAKeyframeAnimation) 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---

​&nbsp;​

[CAKeyframeAnimation 애니메이션, 키프레임, 쉐이킹 애니메이션] : <https://ios-development.tistory.com/841>

[CAKeyframeAnimation 대하여] : <https://wookiphone.tistory.com/81>

[Animation 테크닉 - 오토레이아웃, 단일 애니메이션, 연속 애니메이션, 스프링, 뒤집기 (autolayout, CAKeyframeAnimation, animateKeyFrames)](https://ios-development.tistory.com/908)

```swift
//  imageView 가 아니라 그냥 UIView 여도 된다
override func viewDidAppear(_ animated: Bool) {
        advancedAnimation(imageView: jobNewsButton.imageView!)
}

func advancedAnimation(imageView: UIImageView) {
    let opacityKeyframe = CAKeyframeAnimation(keyPath: "opacity")
    opacityKeyframe.values = [0.1, 1.0, 1.0, 0.1]
    opacityKeyframe.keyTimes = [0, 0.32, 0.68, 1]
//    opacityKeyframe.duration = 2.3
//    opacityKeyframe.repeatCount = .infinity
        
    let scaleKeyFrame = CAKeyframeAnimation(keyPath: "transform.scale")
    scaleKeyFrame.values = [0.9, 1.0, 1.0, 0.9]
    scaleKeyFrame.keyTimes = [0, 0.32, 0.68, 1]
        
    let animationGroup = CAAnimationGroup()
    animationGroup.animations = [opacityKeyframe, scaleKeyFrame]
    animationGroup.duration = 2.3
    animationGroup.repeatCount = Float.infinity
    animationGroup.fillMode = .forwards             // 애니메이션 완료 후 상태 유지
    animationGroup.isRemovedOnCompletion = false    // 애니메이션 완료 후 제거하지 않음

    imageView.layer.add(animationGroup, forKey: "advancedAnimationGroup")

//    애니메이션 삭제 방법
//    imageView.layer.removeAnimation(forKey: "myAnimationGroup")
}

```

​

​

​
