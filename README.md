# 팀 프로젝트 Git 세팅 가이드

## 목차
1. [팀장이 하는 일 (초기 세팅)](#1-팀장이-하는-일-초기-세팅)
2. [팀원이 하는 일 (초기 세팅)](#2-팀원이-하는-일-초기-세팅)
3. [작업할 때 순서 (공통)](#3-작업할-때-순서-공통)
4. [PR을 받았을 때 팀장이 하는 일](#4-pr을-받았을-때-팀장이-하는-일)

---

## 1. 팀장이 하는 일 (초기 세팅)

### (1) Organization 생성
- GitHub 메인 → 프로필 → Your organizations → New organization
- 무료 플랜 선택
- Organization 이름, 이메일 설정

### (2) 팀원 초대
- Organization 페이지 → People
- `Invite member` 클릭
- 팀원 이메일 입력
- 권한 설정 (member 권한)

### (3) Repository 생성
- Organization 페이지 → New repository
- 이름 설정 (예: `team-project`)
- public / private 선택
- `README.md` 생성 체크

### (4) 기본 파일 설정 (프로젝트 세팅)

1. 공용 저장소의 Fork 버튼을 눌러 내 개인 저장소로 복제
2. 로컬에 프로젝트 폴더 만들고 클론 따기
   ```bash
   git clone [개인 URL]
   ```
3. 리모트 연결 확인
   ```bash
   git remote -v
   # origin에 내 계정의 fork한 저장소가 등록되어야 함
   ```
4. 공용 저장소도 리모트 연결
   ```bash
   git remote add [별칭] [공용 저장소 주소]
   git remote -v  # 확인
   ```
5. `.gitignore` 파일 생성 등 프로젝트 기본 구조 만들기
6. 변경사항 스테이징 → 커밋 → push (fork한 origin으로)

### (5) 공용 저장소로 PR 보내기
- Fork한 저장소 → Pull Requests → New pull request
- 변경사항 확인 (충돌 없는지 확인) 후 `Create pull request`
- PR 제목 (무엇을 수정했는지), 내용 (자세히) 작성 → `Create pull request`

### (6) PR 요청 확인과 병합
- 공용 저장소 → Pull Requests (숫자 표시됨)
- PR 목록 중 1개 선택
- PR 설명과 `Files changed`에서 변경 파일 파악
- 이상 없으면 `Merge pull request`

### (7) 팀원들에게 세팅 완료 알리기

---

## 2. 팀원이 하는 일 (초기 세팅)

### (1) 초대 수락
- 이메일 초대 링크 수락
- 또는 GitHub 알림에서 수락

### (2) Fork 생성 (팀장 세팅 완료 후)
- Organization 저장소 들어가기
- `Fork` 버튼 클릭 → 내 저장소로 복제

### (3) 로컬 환경 설정
1. 로컬에 프로젝트 폴더 만들고 클론 따기
   ```bash
   git clone [개인 원격 저장소 URL]
   ```
2. 리모트 연결 확인
   ```bash
   git remote -v
   ```
3. 공용 저장소도 리모트 연결
   ```bash
   git remote add [별칭] [공용 저장소 주소]
   git remote -v  # 확인
   ```

---

## 3. 작업할 때 순서 (공통)

### (1) 작업 시작 전 준비
- `main` 브랜치로 이동
- **공용 저장소**에서 pull 받아 최신화
- 최신 `main` 브랜치에서 작업용 브랜치 생성

> ⚠️ **main 브랜치에서 직접 작업하지 말 것!**

### (2) 작업 진행
- **작업용 브랜치**에서만 작업
- 완료되면 커밋 (필요 시 여러 번 커밋 가능)

### (3) 원격 저장소에 push 준비
1. `main` 브랜치로 이동 후 **공용 저장소**에서 pull 받기 (최신화)
2. 작업 브랜치로 돌아와서 `main`을 병합(merge)
   - 충돌 발생 시: 충돌 해결 후 커밋
   - 충돌 없으면: 자동 커밋
3. **개인 원격 저장소**에 push
   ```bash
   git push origin [작업 브랜치명]
   # 동일한 이름의 브랜치를 원격에 생성하여 push
   ```

### (4) PR 생성
- **공용 저장소의 main**으로 PR 보내기
- PR 보낸 후 팀장에게 연락

---

## 4. PR을 받았을 때 팀장이 하는 일

- 공용 저장소 → Pull Requests (숫자 표시됨)
- PR 목록 중 1개 선택
- PR 설명과 변경된 파일 파악 (충돌 여부 확인)
- 이상 없으면 → `Merge pull request`
- 이상 있으면 → 팀원에게 재작업 요청