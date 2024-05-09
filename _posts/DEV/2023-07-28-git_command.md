---
title:  Git 명령어
categories: Git.Hub
tag: [🐙 Git﹒GitHub]
toc: true
excerpt: false
---
<br>
# Git 명령어

## test branch 생성 및 이동
```
$ git checkout -b test
```

## 브랜치를 삭제하는 이유
프로젝트에서 코드의 변경 사항을 저장하기 위해 브랜치를 만들었다고 가정해봅시다.

그렇지만 해당 브랜치의 변경 사항이나 새 기능을 프로젝트의 본 버전에 반영 완료한 후에는 해당 브랜치를 유지할 필요가 없어집니다. 따라서 프로젝트 저장소가 복잡해지지 않도록 작업이 완료된 브랜치는 삭제하는 것이 일반적입니다.

## 로컬 branch 삭제
`git branch`는 로컬 브랜치를 삭제하는 명령어입니다.

`-d` 는 `--delete` 의 약자입니다.
```
$ git branch
-------------------
  development
  master
* test1
(END)
-------------------

$ git checkout development

$ git branch -d test1
Deleted branch test1 (was a594bc6).
```
브랜치에 병합되지 않은 변경 사항 및 푸시되지 않은 커밋이 있는 경우 -d 플래그를 사용해 로컬 브랜치를 삭제할 수 없습니다.

브랜치가 가지고 있는 커밋이 다른 브랜치 혹은 저장소에 기록되어 있지 않을 경우, 커밋 기록이 실수로 손실되는 것을 Git이 방지하기 때문입니다.

만일 이러한 상황에서 git branch -d 명령어를 실행하면 에러가 발생합니다.

따라서 **해당 브랜치를 강제로 삭제**하려면 `-D` 플래그를 사용해야 합니다.

대문자 "D"가 있는 -D 플래그는 --delete --force(강제 삭제)의 줄임말이며, 병합 여부와 관계없이 로컬 브랜치를 강제로 삭제합니다.

브랜치 삭제 여부를 재확인하는 절차가 따로 없으므로 이 명령어는 주의해서 사용해야 합니다.

로컬 브랜치를 확실히 삭제하려는 경우에만 사용해야 한다는 점을 잊지 마세요.

다른 브랜치로 변경 이력을 병합하거나 코드 베이스의 원격 브랜치로 푸시하지 않은 상태에서 로컬 브랜치를 삭제하면 변경 사항이 손실될 위험이 있습니다.

```
$ git brnach -D test2
Deleted branch test2 (was a594bc6).
```

## 원격 branch 삭제
로컬 브랜치를 삭제하는 `git branch` 명령어를 사용하는 대신 `git push` 명령어를 이용해 원격 브랜치를 삭제해야 합니다.

git push 명령어 다음에 원격 저장소의 이름을 전달해야 합니다. 대부분은 `origin`입니다.

`-d` 플래그는 삭제라는 의미를 가진 `--delete`의 줄임말입니다.

원격 브랜치 목록을 확인하려면 다음과 같은 명령어를 사용해야 합니다.


```
$ git branch -a

$ git branch -r
```
`-a` 플래그(모두란 의미를 가진 --all의 줄임말)를 사용하면 로컬, 원격 브랜치를 모두 확인할 수 있습니다.

--remotes의 줄임말인 `-r` 플래그를 사용하면 원격 저장소만 확인할 수 있습니다.

origin/test3 브랜치를 삭제하길 원한다면 다음과 같은 명령어를 사용해야 합니다. (test3 앞에 origin/ 이 붙지 X)
```
$ git push origin -d test3
```


## 빨리감기 병합 안하기
```
$ git marge --no-ff [병합할Branch]
```

## 커밋 수정하기
메시지만 수정
```
$ git commit --amend -m "수정할 커밋 메시지"
```

변경내용 수정

```
$ git add .
$ git commit --amend
```

⬇️ 수정 후 강제푸쉬

## 강제푸쉬
```
$ git push (origin master) --force-with-lease
```

## log 이쁘게 출력
```
$ git log --oneline --graph --all --decorate
```

## 되돌리기
```
git reset [testfile]            //  testfile 스테이징 취소하기 (soft, mixed, hard 중 mixed reset으로 작동)
git reset --hard [testfile]     //  변경사항 되돌리기 (커밋하지 않은)

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