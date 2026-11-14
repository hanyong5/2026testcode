# Todo List

HTML5, CSS3, Vanilla JavaScript, LocalStorage 기반 Todo List 프로젝트입니다.

저장소: https://github.com/hanyong5/2026testcode

## 현재 개발 상태

개발 환경 구성 단계입니다. HTML에서 CSS와 JavaScript 파일을 연결했으며,
JavaScript 실행 시 브라우저 콘솔에 `test`가 출력됩니다. CSS 파일은 현재 비어 있습니다.
Todo CRUD, 완료 상태, 필터 및 LocalStorage 저장·복원은 아직 구현하지 않았습니다.

## 기술 스택

- HTML5: 시맨틱 화면 구조
- CSS3: 스타일과 반응형 레이아웃
- Vanilla JavaScript: 사용자 이벤트와 Todo 상태 관리
- LocalStorage: 브라우저 내 데이터 저장·복원 (구현 예정)

프레임워크, 패키지 설치 및 빌드 과정은 필요하지 않습니다.

## 폴더 구조

```text
2026testcode/
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── feature.md
│   │   ├── bug.md
│   │   └── task.md
│   └── pull_request_template.md
├── css/
│   └── style.css
├── js/
│   └── script.js
├── index.html
├── .gitignore
├── AGENTS.md
└── README.md
```

## 로컬 실행

Git과 Python 3가 설치된 환경에서 다음 명령을 실행합니다.

```sh
git clone https://github.com/hanyong5/2026testcode.git
cd 2026testcode
git switch setup/2-dev-environment
python3 -m http.server 8000 --bind 127.0.0.1
```

브라우저에서 http://127.0.0.1:8000 을 엽니다. 서버 종료는 `Ctrl+C`입니다.
이미 저장소가 있다면 해당 폴더에서 서버 명령만 실행할 수 있습니다.
작업 파일이 원격 브랜치에 커밋·푸시된 이후에는 새 환경에서도 같은 방법으로 실행할 수 있습니다.

로컬 실행에 `.env` 또는 GitHub 인증 토큰은 필요하지 않습니다.
서버는 프로젝트 폴더의 파일을 제공하므로 `.env` 등 민감한 파일은 서비스 루트 밖에 보관합니다.

## 지원 브라우저 및 검증

지원 목표는 최신 안정 버전의 Chrome, Edge, Firefox, Safari입니다.
현재 초기 페이지 로딩은 Chrome headless에서 확인했으며 다른 브라우저는 검증 예정입니다.

초기 환경 확인 절차:

1. 개발자 도구의 Network에서 HTML, `css/style.css`, `js/script.js` 로딩을 확인합니다.
2. Console에서 `test` 출력과 오류 유무를 확인합니다.
3. JavaScript 문법은 `node --check js/script.js`로 추가 확인할 수 있습니다. Node.js는 앱 실행 필수 요건이 아닙니다.

기능 구현 후에는 CRUD, 완료 전환, 필터, 새로고침 후 데이터 복원 및 예외 상황을 검증합니다.

## 개발 및 협업 규칙

- Issue에 작업 목적, 체크리스트, 완료 조건을 작성하고 담당자·phase 라벨·Milestone을 지정합니다.
- 작업 시작 시 Project 상태를 `In progress`로 변경합니다.
- 기본 브랜치는 `main`이며 작업은 `<phase>/<issue번호>-<작업명>` 브랜치에서 진행합니다.
- Issue #2의 작업 브랜치는 `setup/2-dev-environment`입니다.
- 변경 내용을 검증하고 관련 파일만 커밋한 뒤 원격 작업 브랜치로 푸시합니다.
- PR은 `main`을 대상으로 생성하며 관련 Issue를 `Closes #번호`로 연결합니다.
- PR에 변경 사항과 실제 테스트 결과를 기록하고 리뷰 후 병합합니다. 자동 병합은 하지 않습니다.
- `.env`, 인증 토큰, 로컬 설정은 커밋하지 않습니다. `.gitignore`는 이미 추적 중인 파일을 자동 제외하지 않으므로 커밋 전 `git status`와 `git diff --cached`를 확인합니다.

## 배포

GitHub Pages 배포는 Issue #16에서 진행할 예정입니다. 현재 배포 URL은 등록하지 않았습니다.
