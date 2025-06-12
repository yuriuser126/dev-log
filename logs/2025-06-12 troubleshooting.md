# 🔧 Git 브랜치 푸시 & 체크아웃 이슈 해결 정리

> ✅ 메인에서 작업한 커밋을 개인 브랜치로 옮기고, 푸쉬 및 병합까지 처리하는 방법 요약

---

## 📌 상황 요약

- 메인 브랜치에서 검색 기능 작업 → 커밋 완료
- 개인 브랜치(`feature/yuriuser-elastic`)로 넘어감
- 터미널에서는 개인 브랜치로 체크아웃되어 있음
- **BUT** 커밋 내용이 개인 브랜치에는 없음
- `git push` 시 다음과 같은 오류 발생:

```bash
error: src refspec yuriuser-elastic does not match any
```

---

## 🔍 원인 분석

- 메인 브랜치에서 커밋하고 **체크아웃 없이** 개인 브랜치로 푸시하려 함
- 현재 작업 내역은 메인 브랜치에만 존재 → 개인 브랜치엔 없음
- 잘못된 refspec 사용 or 푸시할 브랜치 내용이 없음

---

## ✅ 해결 방법

### 1. 메인에서 작업한 커밋 → 개인 브랜치로 옮기기

```bash
# 개인 브랜치로 이동
git checkout feature/yuriuser-elastic

# 메인 브랜치 내용 병합
git merge main
```

💡 *또는 rebase로 정리할 수도 있음:*

```bash
git rebase main
```

---

### 2. 변경된 커밋 푸시하기

```bash
git push origin feature/yuriuser-elastic
```

❗ 강제로 푸시해야 할 경우 (주의!)

```bash
git push -f origin feature/yuriuser-elastic
```

> ⚠️ `-f`는 팀 작업 시 주의 필요. 원격 브랜치 히스토리를 덮어씀.

---

### 3. GitHub에서 Pull Request 생성

- 브랜치 푸시 후 GitHub에서 `"Compare & pull request"` 클릭
- PR 생성 → 리뷰 또는 확인 후 `"Merge pull request"` 클릭

---

## 💡 팁 & 체크리스트

| 항목 | 확인 여부 |
|------|------------|
| `git status` 로 현재 브랜치 확인 | ☑ |
| 작업 중인 브랜치에서 커밋했는가? | ☑ |
| 변경사항이 있는지 확인했는가? | ☑ |
| 푸시 전에 브랜치 이름 정확히 입력했는가? | ☑ |

---

## 📁 dev-log에 정리하는 것에 대해

👍 **강력 추천**  
- 개인/팀 모두에게 도움이 됨  
- 반복적인 Git 문제를 빠르게 해결 가능  
- Markdown 형태로 기록하면 GitHub에서도 보기 좋음

```bash
📂 dev-log/
 └─ 📄 git-branch-push-troubleshooting.md
```

---

## 🧩 참고 명령어 요약

```bash
# 브랜치 상태 확인
git status

# 브랜치 이동
git checkout feature/브랜치명

# 메인 병합
git merge main

# 푸시
git push origin feature/브랜치명

# 강제 푸시 (주의)
git push -f origin feature/브랜치명
```

---
🕒 작성일: 2025-06-12
