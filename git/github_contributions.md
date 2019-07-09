
## Github Contribution 
- 1일 1커밋을 하거나 TIL를 작성하다면 contribution 그래프를 채우기 위해 한번쯤 필요했던 기능들 정리
- 가끔 그래프가 그려지지 않는 경우가 있음
- 자세한 내용은 그래프 하단의 [Learn how we count contributions](https://help.github.com/en/articles/why-are-my-contributions-not-showing-up-on-my-profile#contributions-that-are-counted) 참고

## Contribution 그려지는 조건
### Issue, Pull requests
- fork가 아닌 standalone repository 에서 오픈되는 경우

### Commits 
- Commit 한 email 주소가 GitHub 계정과 연결 되어 있을 경우
- fork가 아닌 standalone repository 에서 만들어 졌을 경우
- Commit이 repository의 default branch 에서 만들어 졌을 경우
- Commit이 gh-pages branch 에서 만들어 졌을 경우 

## 커밋 내용에서 author(작성자) 수정하기
```
$ git commit --amend --author="사용자명 <이메일>"

```
## 가장 최근 커밋 메시지 변경
```
$ git commit --amend -m "an updated commit message"

```
`-m` 옵션을 추가하면 편집기를 열지 않아도 명령줄에서 새 메시지

## 가장 최근 커밋 파일 변경
```
$ git commit --amend --no-edit

```
`--no-edit` 플래그를 사용하면 커밋 메시지를 변경하지 않아도 커밋 변경 가능

## 참고
- [Github -  Contribution 그래프가 그려지지 않을 때!](https://diordna.tistory.com/37)
- [이미 커밋된 내용에서 author(작성자) 수정하기](https://jojoldu.tistory.com/120)
- [Change the date of a git commit](https://codewithhugo.com/change-the-date-of-a-git-commit/#set-the-date-of-the-last-commit-to-an-arbitrary-date)