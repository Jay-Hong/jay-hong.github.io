---
title:  Swift - View Controller Life-Cycle 🔗
categories: iOS
tag: [🍏 iOS, 🔗 link]
toc: false
excerpt: false
---
<br>

[View Controller의 생명주기(Life-Cycle)] : <https://zeddios.tistory.com/43>
​
<br><br><br>
​
View Contorller의 생명주기?

앱들은 이 'View Contorller'로 이루어져있는데요,

화면이 하나로 되어있는 앱 들도 물론 있겠지만,

보통 하나 이상의 화면이 있죠?이 각각의 뷰컨들은 생명주기를 가지고 있답니다.

결론만 말씀드리면, 뷰는 

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F2613D13C58C64DE32C)

이러한 주기를 가지게됩니다.

&nbsp; loadView

&nbsp; &nbsp; &nbsp; ⬇️

viewDidLoad

&nbsp; &nbsp; &nbsp; ⬇️

viewWillAppear

&nbsp; &nbsp; &nbsp; ⬇️

viewDidAppear

&nbsp; &nbsp; &nbsp; ⬇️

viewWillDisappear

&nbsp; &nbsp; &nbsp; ⬇️

viewDidDisappear

하나씩 볼까요?

<br>

## 1. loadView

바로 컨트롤러가 관리하는 뷰를 '만드는' 역할을 합니다.

그럼 loadView가 뷰를 만들고, 메모리에 올린 후에!

viewDidLoad가 호출된다고 할 수 있겠네요.

<br>

## 2. viewDidLoad

프로젝트를 새로 만들면 보이는 

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F2105263758C62EF90D)

viewDidLoad()함수입니다

이 viewDidLoad()가 왜 있는 걸까요? 하는 기능은 뭘까요?

apple문서를 보시면,

Called after the controller view is loaded into memory

➡️ 뷰의 컨트롤러가 메모리에 로드되고 난 후에 호출됩니다.

일단 '뷰'라는 것을 만들고, 메모리에 올려야 접근이 가능하겠죠?

이 viewDidLoad 메소드는 뷰의 로딩이 완료 되었을 때 

시스템에 의해 자동으로 호출되기 때문에

일반적으로 리소스를 초기화하거나

초기 화면을 구성하는 용도로 주로 사용합니다.

화면이 처음 만들어질 때 한 번만 실행되므로,

처음 한 번만 실행해야 하는 초기화 코드가 있을 경우

이 메소드 내부에 작성하면 됩니다.

<br>

## 3. viewWillAppear

앱의 초기화 작업은 viewDidLoad에서 해도 되겠지만,

다른뷰에서 갔다가 다시 돌아오는 상황에해주고 싶은 처리가 있겠죠?

이때는 viewWillAppear에서 해주면 된답니다.

<br>

## 4. viewDidAppear

iewDidAppear는 뷰가 나타났다는 것을 컨트롤러에게 알리는 역할을 합니다.

또한 화면에 적용될 **애니메이션을** 그려줘요.

이 viewDidAppear는 뷰가 화면에 나타난 직후에 실행됩니다.

이 것을 제외하고 viewDidAppear와 viewWillAppear는 거의 같아요.

<br>

## 5. viewWillDisappear

viewWillDisAppear는 뷰가 사라지기 직전에 호출되는 함수인데요,

뷰가 삭제 되려고하고있는 것을 뷰 콘트롤러에 통지합니다.

<br>

## 6. viewDidDisappear

역시 위와 같아요viewDidDisAppear가 호출되면,뷰 컨트롤러가 뷰가 제거되었음을 알려준답니다. 

<br>

