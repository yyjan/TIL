# Git 리모트 관리

## 리모트 저장소 추가
` git remote add [단축이름] [url]`
```
$ git remote
origin
$ git remote add pb git://github.com/paulboone/ticgit.git
$ git remote -v
origin  git://github.com/schacon/ticgit.git
pb  git://github.com/paulboone/ticgit.git
```

## 리모트 저장소 확인
```
$ git remote
origin
```
```
$ git remote -v
origin  git://github.com/schacon/ticgit.git (fetch)
origin  git://github.com/schacon/ticgit.git (push)
```
- `-v` 옵션을 주어 단축이름과 URL 함께 볼 수 있음

## 리모트 저장소 이름 변경
```
$ git remote rename pb paul
$ git remote
origin
paul
```

## 리모트 저장소 삭제
```
$ git remote rm paul
$ git remote
origin
```

## 리모트 브랜치 모두 확인
```
$ git branch -a
```

## 리모트 브랜치 최신 정보로 업데이트 하기
```
$ git remote prune origin
```
- 자신의 로컬에 있는 리모트 브랜치를 최신으로 업데이트
- `origin`으로 추가한 리모트에 있는 브랜치가 변경 되었을 때, **추가/삭제된** 정보를 최신으로 업데이트


## 참고
- [Git의 기초 - 리모트 저장소](https://git-scm.com/book/ko/v1/Git의-기초-리모트-저장소)
- [Git Remote 관리 명령어 한눈에 보기](https://webisfree.com/2016-12-16/git-remote-관리-명령어-한눈에-보기)