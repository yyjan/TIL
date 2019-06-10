# branch

## branch 목록보기 
```
$ git branch
  iss53
* master
  testing
```
```
$ git branch -v
  iss53   93b412c fix javascript issue
* master  7a98805 Merge branch 'iss53'
  testing 782fd34 add scott to the author list in the readmes
```
- `git branch -v` 명령을 실행하면 브랜치마다 마지막 커밋 메시지도 함께 보여줌

## branch 생성 
```
$ git checkout -b iss53
Switched to a new branch "iss53"
```
```
$ git branch iss53
$ git checkout iss53
```

## branch 이동
```
$ git checkout master
```

## 로컬 branch 삭제 
```
$ git branch -d iss53 
```

## 리모트 branch 삭제
```
$ git push origin :serverfix
```

## push 하기
```
$ git push origin serverfix
```

## 참고
- [Git 브랜치 - 리모트 브랜치](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EB%B8%8C%EB%9E%9C%EC%B9%98)
