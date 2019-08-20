## Git Commit Message Guide
좋은 커밋 메시지 작성하는 방법 정리

## Git 커밋 메시지 작성법
![Jekyll Now Theme Screenshot](https://imgs.xkcd.com/comics/git_commit_2x.png )

### 좋은 커밋 메시지가 중요한 이유
1. 커밋 로그 가독성
2. 협업과 쉬운 코드리뷰
3. 코드 유지보수

### Git 커밋 메시지의 규칙
- 하나의 Commit 에는 하나의 기능만 업데이트한다 (작은 단위로 커밋)
- 메시지는 명료하고 이해하기 쉽게 남긴다.
- 제목과 본문을 빈 행으로 분리 한다
- 제목은 50자로 제한한다
- 제목 끝에 마침표를 사용한다
- 제목에 명령문을 사용한다
- 본문을 72자 단위로 개행한다
- 어떻게 보다는 '무엇'과 '왜' 를 설명한다 

### Type
```
- **feat:** a new feature (새로운 기능 추가)
- **fix:** a bug fix (버그 수정)
- **docs:** changes to documentation (문서 수정)
- **style:** formatting, missing semi colons, etc; no code change (코드 포맷 변경, 코드 수정이 없는 경우)
- **refactor:** refactoring production code (리랙토링)
- **test:** adding tests, refactoring test; no production code change (테스트 추가)
- **chore:** updating build tasks, package manager configs, etc; no production code change (빌드 테스트, 패키지 매니저 설정)
```
  
### Example Commit Message

```
feat: Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of the commit and the rest of the text as the body. The
blank line separating the summary from the body is critical (unless
you omit the body entirely); various tools like `log`, `shortlog`
and `rebase` can get confused if you run the two together.

Explain the problem that this commit is solving. Focus on why you
are making this change as opposed to how (the code explains that).
Are there side effects or other unintuitive consequenses of this
change? Here's the place to explain them.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded
   by a single space, with blank lines in between, but conventions
   vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```


### Closing issues using keywords (GitHub)
GitHub는 커밋 메시지 키워드를 통해 이슈를 자동으로 종료시키는 기능이 있다.
`키워드 #이슈번호`

```
- close
- closes
- closed
- fix
- fixes
- fixed
- resolve
- resolves
- resolved
```

( `close` 계열은 일반 개발 이슈, `fix` 계열은 버그 픽스나 핫 픽스 이슈, `resolve` 계열은 문의나 요청 사항에 대응한 이슈에 사용하면 적당하다는 관례)

Github 저장소의 default branch를 `master`로 설정해뒀을 경우, `master` 브랜치에 커밋 후 푸시하면 즉시 해당 번호의 이슈가 닫히고, `develop` 브랜치에 푸시했다면,  `develop -> master Merge`가 되었을 때 닫힌다.


## 참고
- [Udacity Git Commit Message Style Guide](https://udacity.github.io/git-styleguide/)
- [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/)
- [Closing issues using keywords](https://help.github.com/en/articles/closing-issues-using-keywords)
- [Git 커밋 메시지 작성법](https://item4.github.io/2016-11-01/How-to-Write-a-Git-Commit-Message/)
- [좋은 git commit 메시지를 위한 영어 사전 (추천!!)](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html) 
