---
title:  Jekyll - mmistakes ⌜이미지 올리기⌟
categories: Jekyll
tag: [📐 jekyll]
toc: true
excerpt: false
---


기본적으로 markdown, HTML 모두 가능하다

### 1. markdown 문법

```markdown
### 기본
![대체텍스트](/assets/images/noteJay.png)
```

![대체텍스트](/assets/images/noteJay.png)

```md
### URL로 추가하기
![대체텍스트](https://jay-hong.github.io/assets/images/noteJay.png)
```

![대체텍스트](https://jay-hong.github.io/assets/images/noteJay.png)


```markdown
### 가운데정렬 및 링크설명 적용 가능
![대체텍스트](/assets/images/noteJay.png "설명"){: .align-center}
```

![대체텍스트](/assets/images/noteJay.png "설명"){: .align-center}

여기서 _**[대체텍스트]**_ 부분은 대체문자(alternative text)로 이미지가 보이지 않을경우 대신해 보여줄 **텍스트** 이다.

_**"설명"**_ 은 해당 이미지위에 마우스를 올려놓고 잠시 기다려보면 알 수 있다.

당연히, 지정해준 경로에 해당 이미지 파일이 있어야 겠지?




### 2. html 문법

```html
<center>
    <img src="/assets/images/noteJay.png" width="50%" height="50%" title="title" alt="alt"/>
</center>
```

<center>
<img src="/assets/images/noteJay.png" width="50%" height="50%" title="title" alt="alt"/> 
</center>




### 참고
- <a href="https://rosejam.github.io/blogging/how-to-image/">https://rosejam.github.io/blogging/how-to-image</a>
- <a href="https://seungwubaek.github.io/blog/first_post/">https://seungwubaek.github.io/blog/first_post/</a>


1. [https://rosejam.github.io/blogging/how-to-image](https://rosejam.github.io/blogging/how-to-image)
2. [https://seungwubaek.github.io/blog/first_post/](https://seungwubaek.github.io/blog/first_post/)