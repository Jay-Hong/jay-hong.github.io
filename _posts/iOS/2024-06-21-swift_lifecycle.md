---
title:  Swift - App's Life Cycle 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---

​&nbsp;

✔️ iOS 13 버전 혹은 그 이후 버전

Scene 기반 앱의 생명 주기 이벤트에 응답하기 위해 UISceneDelegate 객체를 사용한다.
{: .notice}

✔️ iOS 12 버전 혹은 그 이전 버전

UIApplicationDelegate 객체를 사용하여 생명 주기 이벤트에 응답한다.
{: .notice}

​

## 앱의상태

![App State](https://velog.velcdn.com/images/ahneve/post/bde722d5-b433-4bc8-a0b2-9aff7c42510c/image.png){: .align-center}

+ NotRunning
  + 앱이 아직 실행되지 않았거나, 완전히 종료되어 동작하지 않는 상태

+ Foreground - Inactive
  + Inactive는 앱이 실행중이지만 사용자로부터 이벤트를 받을 수 없는 상태이다. 멀티태스킹 윈도우로 진입하거나 앱 실행중 전화, 알림 등에 의해 앱을 사용할 수 없게 되는 경우 이 상태로 진입한다.

+ Foreground - Active
  + Active는 앱이 실제 실행중이고 사용자 이벤트를 받아서 상호작용할 수 있는 상태이다. 바로 Active상태는 될 수 없으며 Inactive 상태를 거쳐서 Active 상태가 된다.

+ Background - Running
  + Background는 홈 화면으로 나가거나 다른 앱으로 전환되어 현재 앱이 실질적인 동작을 하지 않는 상태이다. 예를 들어 뮤직 앱을 닫아도 재생한 음악이 계속 실행되는 경우, 사용자가 앱을 사용하지 않는 동안 서버와 데이터를 동기화하거나 타이머가 실행되어야 하는 등의 작업을 이 상태에서 할 수 있다.

+ Background - Suspended
  + Suspended는 앱을 다시 실행했을 때 최근 작업을 빠르게 로드하기 위해서 메모리에 관련 데이터만 저장되어 있는 상태이다. 앱이 Background 상태에 진입했을 때 다른 작업을 하지 않으면 Suspended 상태로 진입하게 된다. (보통 2-3초 이내)
  + Suspended 상태의 앱들은 iOS의 메모리가 부족해지면 가장 먼저 메모리에서 해제된다. 따라서 앱을 종료시킨 적이 없더라도 앱을 다시 실행하려고 하면 처음부터 다시 실행된다. 따라서 앱을 종료시킨 적이 없더라도 앱을 다시 실행하려고 하면 처음부터 다시 실행된다.

​

## 앱의 생명주기 관리

### iOS 13 버전 혹은 그 이후 버전 : Scene 사용

[앱의 생명주기 (App’s life cycle)] : [앱의 생명주기 (App’s life cycle)](https://velog.io/@ahneve/iOSSwift-%EC%95%B1%EC%9D%98-%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0-Apps-life-cycle)

​

### iOS 12 버전 혹은 그 이전 버전 : App Delegate

​

![App Delegate](https://velog.velcdn.com/images/ahneve/post/fda3273a-90e5-4711-b05b-78a77daaefd0/image.png){: .align-center}

​

> ⒈ 앱 실행 : Not Running - Inactive - Active

앱이 실행되면 Not Running 상태에서 Inactive를 거쳐 Active 상태로 전환됨.

이 때, App Delegate는 시스템에 다음 메소드를 호출하도록 요청함.

+ Active 시 UI 구성을 완료하고 사용자와 상호 작용할 준비를 함

```swift
application(_:didFinishLaunchingWithOptions:) 
```

+ 앱이 실행 되고 앱을 화면에 띄우기 위한 모든 설정이 완료된 뒤, 실제로 화면에 나타나기 직전에 호출됨

+ UIWindow를 생성하는 등의 작업을 할 수 있음

+ StoryBoard를 사용하다면 StoryBoard에서 엔트리 포인트를 찾아 내부적으로 UIWindow를 생성함

```swift
applicationDidBecomeActive(_: )     //  📲
```

+ 앱이 Inactive에서 Active 상태로 전환되었을 때 호출됨

​

> ⒉ 앱 실행 후 홈 화면으로 나가면 : Active - Inactive - Background (-Suspended)

앱 실행 후 홈 화면으로 나가면 Active에서 Inactive를 거쳐 Background 상태로 전환됨.

이 때, App Delegate는 시스템에 다음 메소드를 호출하도록 요청함

```swift
applicationWillResignActive(_:)
```

+ 앱이 Active에서 Inactive 상태로 전환될 때 호출됨

```swift
applicationDidEnterBackground(_:)
```

+ 앱이 Background 상태로 전환되었을 때 호출됨

​

> ⒊ Background 상태에 있는 앱을 다시 실행하면 : Background - Inactive - Active

사용자가 직접 앱을 종료시키는 경우, 앱은 다시 Not Running 상태로 돌아감.

이 때, App Delegate는 시스템에 다음 메소드를 호출하도록 요청함

```swift
applicationWillEnterForeground(_:)   //  백그라운드에서 다시 활성화 될때만 호출되는 메소드
```

+ 앱이 Background에서 Inactive 상태로 전환될 때 호출됨

```swift
applicationDidBecomeActive(_: )     //  📲
```

+ 앱이 Inactive에서 Active 상태로 전환될 때 호출됨

​

> ⒋ 앱 종료: (Some State) - Background or Suspended - Not Running

사용자가 직접 앱을 종료시키는 경우, 앱은 다시 Not Running 상태로 돌아감.

이 때, App Delegate는 시스템에 다음 메소드를 호출하도록 요청함

```swift
applicationWillTerminate(_:)
```

+ 앱이 사용자에 의해 종료될 때 호출됨. 시스템에 의해 예기치 못한 상황에서 종료될 때는 호출되지 않음

​

> ⒌ 앱 실행 후 들어올렸다 다시 클릭

```swift
applicationWillResignActive(_:)
```

+ 백그라운드 가기 직전

```swift
applicationDidBecomeActive(_: )     //  📲
```

+ 클릭하면 다시 활성상태

​

> ⒍ 앱 실행 후 들어올린 후 종료

```swift
applicationWillResignActive(_:)
```

+ 백그라운드 가기 직전

```swift
applicationDidEnterBackground(_:)
```

+ 앱이 Background 상태로 전환되고

```swift
applicationWillTerminate(_:)
```

+ 사용자에 의해 종료 됨

​

​

## 기본설명 및 공수계산기 예제

```swift

    func applicationWillResignActive(_ application: UIApplication) {
        // Sent when the application is about to move from active to inactive state.
        // This can occur for certain types of temporary interruptions
        // (such as an incoming phone call or SMS message)
        // or when the user quits the application and it begins the transition to the background state.
        // Use this method to pause ongoing tasks, disable timers,
        // and invalidate graphics rendering callbacks. Games should use this method to pause the game.
        
        print("\n applicationWillResignActive \n")
    }

    func applicationDidEnterBackground(_ application: UIApplication) {
        // Use this method to release shared resources, save user data, invalidate timers,
        // and store enough application state information to restore your application
        // to its current state in case it is terminated later.
        // If your application supports background execution,
        // this method is called instead of applicationWillTerminate:
        // when the user quits.
        print("\n applicationDidEnterBackground \n")
        setLastLaunchTime()
        exit(0)
    }

    func applicationWillEnterForeground(_ application: UIApplication) {
        // Called as part of the transition from the background to the active state;
        // here you can undo many of the changes made on entering the background.
        // 백그라운드에서 ➡️ 활성화 될때만 실행 (그냥은 실행되지 않음)
        
        print("\n applicationWillEnterForeground \n")
        
    }

    func applicationDidBecomeActive(_ application: UIApplication) {
        // Restart any tasks that were paused (or not yet started) while the application was inactive.
        // If the application was previously in the background, optionally refresh the user interface.
        
        print("\n applicationDidBecomeActive \n")
        
        requestIDFA()
    }

    func applicationWillTerminate(_ application: UIApplication) {
        // Called when the application is about to terminate. Save data if appropriate.
        // See also applicationDidEnterBackground:.
        
        print("\n applicationWillTerminate \n")
        
        setLastLaunchTime()
    }

```

​

[앱의 생명주기 (App’s life cycle)] : [앱의 생명주기 (App’s life cycle)](https://velog.io/@ahneve/iOSSwift-%EC%95%B1%EC%9D%98-%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0-Apps-life-cycle)

[] : <>

​

​

​
