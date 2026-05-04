# git-cheatsheet 🗂️
> GitHub / Git 치트시트 레포 — 실행 플랜

---

## 레포 컨셉

**한 줄 설명**: Git & GitHub의 모든 커맨드, 단축키, 워크플로우를 한 곳에 — 웹사이트 + README

**왜 이게 스타를 받는가**
- 개발자라면 누구나 쓰는 Git, 근데 매번 검색하게 되는 것들이 있음
- 기존 git cheat sheet들은 디자인이 구리거나 내용이 너무 얕음
- 예쁜 사이트 버전이 있으면 북마크 + 공유가 동시에 일어남
- 취준생/주니어 개발자 레퍼런스로 꾸준히 유입

**차별화 포인트**
- 단순 커맨드 나열이 아닌 **상황별(Scenario-based)** 구성
- 인터랙티브 웹사이트 (검색, 복사 버튼)
- GitHub-specific 내용 포함 (Actions, CLI, PR, Issues 등)

---

## 레포 구조

```
git-cheatsheet/
├── README.md               # 메인 치트시트 (표 중심)
├── index.html              # 인터랙티브 웹사이트
├── assets/
│   └── preview.png         # 소셜 프리뷰 + README 임베드용
├── sections/               # 섹션별 상세 md (선택)
│   ├── basics.md
│   ├── branching.md
│   ├── remote.md
│   ├── undoing.md
│   ├── github-cli.md
│   └── github-actions.md
└── CONTRIBUTING.md
```

---

## README.md 구조

```
# 🐙 Git & GitHub Cheat Sheet

[뱃지: stars | last updated | PRs welcome | website]

[preview.png — 클릭하면 index.html (GitHub Pages)로 링크]

## 📚 Table of Contents
- Setup & Config
- Basic Commands
- Branching & Merging
- Remote & Sync
- Undoing Changes
- Stash
- Log & Diff
- GitHub CLI
- GitHub Actions
- Tips & Tricks

---

## ⚙️ Setup & Config
## 📁 Basic Commands
## 🌿 Branching & Merging
## 🔄 Remote & Sync
## ↩️ Undoing Changes
## 📦 Stash
## 🔍 Log & Diff
## 💻 GitHub CLI (gh)
## ⚡ GitHub Actions
## 💡 Tips & Tricks

---
[Contributing] [License] [Website 링크]
```

---

## 콘텐츠 — 채워야 할 내용

### Setup & Config
```bash
git config --global user.name "이름"
git config --global user.email "이메일"
git config --global core.editor "code --wait"   # VS Code
git config --list                                # 설정 확인
git config --global alias.st status              # 별칭 설정
```

### Basic Commands
```bash
git init                        # 레포 초기화
git clone <url>                 # 클론
git clone <url> --depth 1       # 최신 커밋만 클론
git add .                       # 전체 스테이징
git add -p                      # 변경사항 선택적 스테이징
git commit -m "msg"             # 커밋
git commit --amend              # 마지막 커밋 수정
git status                      # 상태 확인
git diff                        # 변경사항 확인
git diff --staged               # 스테이징된 변경사항
```

### Branching & Merging
```bash
git branch                      # 브랜치 목록
git branch <name>               # 브랜치 생성
git switch <name>               # 브랜치 이동 (modern)
git switch -c <name>            # 생성 + 이동
git checkout -b <name>          # 생성 + 이동 (legacy)
git merge <branch>              # 머지
git merge --no-ff <branch>      # Fast-forward 없이 머지
git rebase <branch>             # 리베이스
git rebase -i HEAD~3            # 인터랙티브 리베이스
git branch -d <name>            # 브랜치 삭제
git branch -D <name>            # 강제 삭제
```

### Remote & Sync
```bash
git remote -v                   # 리모트 목록
git remote add origin <url>     # 리모트 추가
git push origin <branch>        # 푸시
git push -u origin <branch>     # 업스트림 설정 + 푸시
git push --force-with-lease     # 안전한 강제 푸시
git pull                        # 풀 (fetch + merge)
git pull --rebase               # 풀 (fetch + rebase)
git fetch origin                # 리모트 변경사항 가져오기
```

### Undoing Changes
```bash
git restore <file>              # 워킹트리 되돌리기
git restore --staged <file>     # 스테이징 취소
git reset HEAD~1                # 마지막 커밋 되돌리기 (변경사항 유지)
git reset --hard HEAD~1         # 마지막 커밋 완전 삭제
git revert <commit>             # 커밋 되돌리기 (새 커밋 생성)
git clean -fd                   # 추적 안된 파일 삭제
```

### Stash
```bash
git stash                       # 변경사항 임시 저장
git stash push -m "메시지"      # 메시지와 함께 stash
git stash list                  # stash 목록
git stash pop                   # 최신 stash 적용 + 삭제
git stash apply stash@{0}       # 특정 stash 적용
git stash drop stash@{0}        # stash 삭제
git stash clear                 # 전체 stash 삭제
```

### Log & Diff
```bash
git log --oneline               # 한 줄 로그
git log --oneline --graph       # 브랜치 그래프
git log -p                      # 변경사항 포함 로그
git log --author="이름"         # 작성자별 필터
git log --since="2 weeks ago"   # 기간별 필터
git show <commit>               # 특정 커밋 확인
git blame <file>                # 라인별 작성자
git shortlog -sn                # 기여자 요약
```

### GitHub CLI (gh)
```bash
gh repo create                  # 레포 생성
gh repo clone <owner>/<repo>    # 클론
gh pr create                    # PR 생성
gh pr list                      # PR 목록
gh pr checkout <number>         # PR 체크아웃
gh pr merge <number>            # PR 머지
gh issue create                 # 이슈 생성
gh issue list                   # 이슈 목록
gh release create               # 릴리즈 생성
gh workflow run <name>          # 워크플로우 실행
gh gist create <file>           # Gist 생성
```

### Tips & Tricks
```bash
# 빈 커밋 (CI 트리거용)
git commit --allow-empty -m "trigger CI"

# 다른 브랜치의 특정 커밋만 가져오기
git cherry-pick <commit>

# 태그 생성 + 푸시
git tag v1.0.0
git push origin v1.0.0

# 글로벌 .gitignore
git config --global core.excludesfile ~/.gitignore_global

# 이전 브랜치로 돌아가기
git switch -

# 특정 파일만 다른 브랜치에서 가져오기
git checkout <branch> -- <file>

# 커밋하지 않고 변경사항 확인
git diff HEAD
```

---

## index.html 기능 설계

### 핵심 기능
- **검색**: 커맨드 또는 키워드로 실시간 필터링
- **복사 버튼**: 코드 블록 클릭 시 클립보드 복사
- **카테고리 탭**: 섹션 탭으로 빠른 이동
- **다크/라이트 모드 토글**

### 디자인 방향
- **테마**: GitHub 스타일 (배경 #0d1117, 포인트 #238636)
- **폰트**: `JetBrains Mono` (코드), `Inter` (UI)
- **레이아웃**: 좌측 사이드바 네비게이션 + 우측 콘텐츠
- **컬러**: GitHub 다크 테마 팔레트 그대로

### URL
- GitHub Pages로 배포: `https://<username>.github.io/git-cheatsheet`
- README에 Website 뱃지로 링크

---

## 레포 세팅 체크리스트

### 만들기
- [ ] `README.md` 작성 (모든 섹션 + 코드블록)
- [ ] `index.html` 완성 (검색 + 복사 + 다크모드)
- [ ] `preview.png` 스크린샷 저장
- [ ] `CONTRIBUTING.md` 작성

### 레포 세팅
- [ ] 레포 이름: `git-cheatsheet`
- [ ] Description: "🐙 The most complete Git & GitHub cheat sheet — commands, workflows, and GitHub CLI in one place"
- [ ] Topics 태그: `git`, `github`, `cheatsheet`, `git-commands`, `github-cli`, `developer-tools`, `reference`, `awesome`
- [ ] GitHub Pages 활성화 (Settings → Pages → main branch / root)
- [ ] Social Preview: `preview.png` 업로드
- [ ] License: MIT

### 홍보 (만든 날 바로)
- [ ] **Hacker News** — Show HN: "A complete Git & GitHub cheat sheet with interactive search"
- [ ] **Reddit** — r/git, r/github, r/learnprogramming, r/webdev
- [ ] **X(트위터)** — preview.png 스크린샷 첨부
- [ ] **GeekNews** — 한국 개발자 커뮤니티
- [ ] **Discord** — 각종 개발 서버 #resources 채널

---

## 차별화 전략 (기존 레포 대비)

| 기존 git cheat sheet | 이 레포 |
|---|---|
| 커맨드 나열만 | 상황별(Scenario) 구성 |
| 정적 MD 파일 | 인터랙티브 웹사이트 |
| Git 기초만 | GitHub CLI + Actions 포함 |
| 디자인 없음 | GitHub 스타일 미려한 UI |
| 업데이트 없음 | 커뮤니티 기여 환영 |

---

*예상 첫 달 목표: GitHub Pages 트래픽 1000+, Stars 300+*
