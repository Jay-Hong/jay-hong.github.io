---
title:  Jekyll - mmistakes 공지사항 ⌜.notice⌟ 및 글자정렬 & TOC아이콘변경
categories: Jekyll
tag: [📐 jekyll]
toc: true
toc_icon: "fas fa-snowflake fa-spin"
# toc_icon: "fas fa-star fa-spin"
# toc_icon: "fas fa-sun fa-spin"
# toc_icon: "fas fa-sync-alt fa-spin"
# toc_icon: "fas fa-wine-bottle fa-spin"
# toc_icon: "fas fa-yin-yang fa-spin"
# https://fontawesome.com/v5/search?p=3&o=r&s=solid
excerpt: false
---
<br><br>

[공지사항] 등 글 내용을 강조하고 싶다면 Notice 클래스를 이용할 수 있다.
{: .notice--info}

아래와 같이 강조할 글 아래에 .notice 클래스 추가!
```markdown
[공지사항] 등 글 내용을 강조하고 싶다면 Notice 클래스를 이용할 수 있다.
{: .notice--info}
```


<br>

| Notice Type |          Class         |
|-------------|------------------------|
|   Default   |   `.notice`            |
|   Primary   |   `.notice--primary`   |
|   Info      |   `.notice--info`      |
|   Warning   |   `.notice--warning`   |
|   Success   |   `.notice--success`   |
|   Danger    |   `.notice--danger`    | 

<br>

### .notice
**Notice** 이 글은  `{: .notice}` class 로 _강조_ 됨
{: .notice}
```markdown
**Notice** 이 글은  `{: .notice}` class 로 _강조_ 됨
{: .notice}
```
<br>

### .notice--primary
**Notice** 이 글은  `{: .notice--primary}` class 로 _강조_ 됨
{: .notice--primary}
```markdown
**Notice** 이 글은  `{: .notice--primary}` class 로 _강조_ 됨
{: .notice--primary}
```
<br>

### .notice--info
**Notice** 이 글은  `{: .notice--info}` class 로 _강조_ 됨
{: .notice--info}
```markdown
**Notice** 이 글은  `{: .notice--info}` class 로 _강조_ 됨
{: .notice--info}
```
<br>

### .notice--warning
**Notice** 이 글은  `{: .notice--warning}` class 로 _강조_ 됨
{: .notice--warning}
```markdown
**Notice** 이 글은  `{: .notice--warning}` class 로 _강조_ 됨
{: .notice--warning}
```
<br>

### .notice--success
**Notice** 이 글은  `{: .notice--success}` class 로 _강조_ 됨
{: .notice--success}
```markdown
**Notice** 이 글은  `{: .notice--success}` class 로 _강조_ 됨
{: .notice--success}
```
<br>

### .notice--danger
**Notice** 이 글은  `{: .notice--danger}` class 로 _강조_ 됨
{: .notice--danger}
```markdown
**Notice** 이 글은  `{: .notice--danger}` class 로 _강조_ 됨
{: .notice--danger}
```
<br>

### 추가 (가운데정렬)
**Notice** 이 글은  `{: .text-center}` class 로 _정렬_ 됨
{: .notice--warning .text-center}
```markdown
**Notice** 이 글은  `{: .text-center}` class 로 _정렬_ 됨
{: .notice--warning .text-center}
```
<br>

### 추가 (오른쪽정렬)
**Notice** 이 글은  `{: .text-right}` class 로 _정렬_ 됨
{: .notice .text-right}
```markdown
**Notice** 이 글은  `{: .text-right}` class 로 _정렬_ 됨
{: .notice .text-right}
```
<br>


### 여러줄 공지사항
<div class="notice--success">
<h4>여러줄 공지사항 만들기</h4>
<ul>
    <li> div 태그에 .notice class를 추가하여</li>
    <li>여러줄의 공지사항을</li>
    <li>만들 수 있다</li>
</ul>
</div>
```markdown
<div class="notice--success">
<h4>여러줄 공지사항 만들기</h4>
<ul>
    <li> div 태그에 .notice class를 추가하여</li>
    <li>여러줄의 공지사항을</li>
    <li>만들 수 있다</li>
</ul>
</div>
```

<br><br>
원문참조 (페이지 하단 Notices)

<https://mmistakes.github.io/minimal-mistakes/docs/utility-classes/>

