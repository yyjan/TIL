# rebase (커밋 변경하기)
이미 커밋한 히스토리를 변경 또는 삭제하고 싶은 경우에 사용
옵션의 i는 interactive의 약자

```
$ git rebase -i [수정을 시작할 커밋의 이전 커밋] 
```
```
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out

pick : 해당 커밋을 이용한다.
reword : 해당 커밋을 이용하고, 메세지를 변경한다.
edit : 해당 커밋을 이용하고, 커밋을 수정한다.
squash : 해당 커밋을 이용하고, 이전 커밋과 합친다.
fixup : squash와 같지만, 이 커밋 로그 메세지는 버린다.
exec : 쉘을 이용한 명령을 수행한다.
```

## 커밋 합치기
`squash` 를 입력하면 해당 커밋과 바로 이전 커밋이 합쳐진다.
```
pick f7f3f6d changed my name a bit
squash 310154e updated README formatting and added blame
squash a5f4a0d added cat-file
```
- 3개의 커밋이 모두 합쳐친다.

## 커밋 분리하기
기존의 커밋을 해제하고 Stage를 여러 개로 분리하고 나서 그것을 원하는 횟수만큼 다시 커밋한다.
```
pick f7f3f6d changed my name a bit
edit 310154e updated README formatting and added blame
pick a5f4a0d added cat-file
```
- edit > `git reset HEAD^` 명령어로 커밋을 해재
- Unstaged 상태로 파일이 올라옴 > 나누어 커밋 > `git rebase --continue`

### 예시
```
$ git reset HEAD^
$ git add README
$ git commit -m 'updated README formatting'
$ git add lib/simplegit.rb
$ git commit -m 'added blame'
$ git rebase --continue
```

## 커밋 순서 바꾸기
```
pick f7f3f6d changed my name a bit
pick 310154e updated README formatting and added blame
pick a5f4a0d added cat-file
```
위와 같은 스크립트를 아래처럼 변경
```
pick 310154e updated README formatting and added blame
pick f7f3f6d changed my name a bit
```
- 커밋 순서가 바뀌었고 `a5f4a0d added cat-file` 커밋은 삭제 된다.

## Rebase의 위험성
"이미 공개 저장소에 Push 한 커밋을 Rebase 하지 마라"  
이 지침만 지키면 Rebase를 하는 데 문제 될 게 없다. 
Rebase는 기존의 커밋을 그대로 사용하는 것이 아니라 내용은 같지만 다른 커밋을 새로 만든다. 새 커밋을 서버에 Push 하고 동료 중 누군가가 그 커밋을 Pull 해서 작업을 한다고 하자. 그런데 그 커밋을 git rebase 로 바꿔서 Push 해버리면 동료가 다시 Push 했을 때 동료는 다시 Merge 해야 한다. 그리고 동료가 다시 Merge 한 내용을 Pull 하면 내 코드는 정말 엉망이 된다.

## 참고
- [git-rebase](https://git-scm.com/docs/git-rebase)
- [7.6 Git 도구 - 히스토리 단장하기](https://git-scm.com/book/ko/v2/Git-%EB%8F%84%EA%B5%AC-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EB%8B%A8%EC%9E%A5%ED%95%98%EA%B8%B0)
