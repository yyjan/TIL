# reset (커밋 삭제하기)
- `HEAD` 마지막 커밋 스냅샷, 다음 커밋의 부모 커밋  
---
```
$ git reset --soft HEAD~
```
- 워킹 디렉토리는 그대로 두고 마지막 커밋을 되돌린다.  
---
```
$ git reset --hard HEAD~
```
- 생성한 마지막 커밋을 되돌린다.
- 워킹 디렉토리의 내용까지도 되돌린다.  
---
```
$ git reset [--mixed] HEAD~
```
- 명령을 실행할 때 아무 옵션도 주지 않으면 기본적으로 `--mixed` 옵션으로 동작
- 그러고 나서 Staging Area 를 비운다. git commit 명령도 되돌리고 git add 명령까지 되돌리는 것   


## 참고
- [git-reset](https://git-scm.com/docs/git-reset)
- [7.7 Git 도구 - Reset 명확히 알고 가기](https://git-scm.com/book/ko/v2/Git-%EB%8F%84%EA%B5%AC-Reset-%EB%AA%85%ED%99%95%ED%9E%88-%EC%95%8C%EA%B3%A0-%EA%B0%80%EA%B8%B0)
