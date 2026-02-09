---
name: git-commit
description: 현재 세션에서의 작업 내용을 git에 commit -> push 할 때 사용
---

# git commit  skill 사용법

## git 사용 순서
- step 1. 해당 세션에서 작업한 파일들을 `git add`
- step 2. add 된 파일들을 `git commit` 실행
  - commit 네이밍과 커밋 메시지는 `git branch` 네이밍을 따른다.
- step 3. 커밋 후 `git push` 진행
- step 4. `.claude/docs/progress.md` 파일에 해당 내용을 최신화
  - [] 형태의 체크박스를 사용하여, 직관적으로 표현