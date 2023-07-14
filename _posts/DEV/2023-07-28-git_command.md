---
title:  Git 명령어
categories: Git.Hub
tag: [🐙 Git﹒GitHub]
toc: true
excerpt: false
---
<br>
# Git 명령어

## 빨리감기 병합
```
git marge --no-ff [병합할Branch]
```

## 강제푸쉬
```
git push (origin master) --force-with-lease
```

## log 이쁘게 출력
```
git log --oneline --graph --all --decorate
```

## test branch 생성 및 이동
```
git checkout -b test
```

## 되돌리기
```
git reset --hard HEAD~
git reset --hard HEAD~3
git reset --hard HEAD^
```
⌜팀 개발을 위한 Git GitHub시작하기⌟ p.255 참고

## 이력관리
```
$ git rebase -i HEAD~7
hint: Waiting for your editor to close the file... 
pick 8120d7ab Customizing JayNote Blog 1
pick d4166c0d 포스트 수정
pick 2cbca00c 페이지 이동 색상변경
pick be75d6d3 홈 화면 최근포스트 없애고, 포스트 7개씩 보이게 변경
pick 241b6757 글자 크기 수정
pick 7e568715 포스트 수정 및 추가 (계획들어감)
pick 693f5ca0 포스트 대량 수정

# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
```
⬇️ 아래와 같이 수정
```
pick 8120d7ab Customizing JayNote Blog 1
s d4166c0d 포스트 수정
s 2cbca00c 페이지 이동 색상변경
s be75d6d3 홈 화면 최근포스트 없애고, 포스트 7개씩 보이게 변경
s 241b6757 글자 크기 수정
s 7e568715 포스트 수정 및 추가 (계획들어감)
s 693f5ca0 포스트 대량 수정
```
⌜Customizing JayNote Blog 1⌟ 이력 하나로 합쳐짐 완성


<br><br>