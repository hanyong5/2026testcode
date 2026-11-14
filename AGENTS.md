# 에이전트 작업 지침

이 문서는 저장소 전체에서 작업하는 코딩 에이전트에 적용합니다.

## 프로젝트와 범위

- HTML5, CSS3, Vanilla JavaScript, LocalStorage 기반 Todo List입니다.
- 화면 진입점은 `index.html`, 스타일은 `css/style.css`, 스크립트는 `js/app.js`입니다.
- 프레임워크나 빌드 도구는 작업에 필요한 경우에만 도입하고 이유를 설명합니다.
- 요청한 Issue 범위만 작업합니다. 환경 설정 작업에서 Todo CRUD를 구현하지 않습니다.

## 작업 전 확인

- `git status --short --branch`로 현재 브랜치와 미커밋 변경을 확인합니다.
- 연결된 Issue의 목적, 체크리스트, 완료 조건과 기존 파일을 읽습니다.
- 사용자 변경과 기존 파일을 보존합니다. 요청 없이 삭제하거나 강제로 덮어쓰지 않습니다.
- 검증만 요청받은 경우 파일을 수정하지 않습니다. 발견한 문제와 수정 방향을 먼저 보고합니다.

## 구현 규칙

- 시맨틱 HTML과 접근 가능한 입력·버튼 이름을 사용합니다.
- CSS는 반응형 배치와 키보드 포커스 표시를 고려합니다.
- 사용자 입력은 안전한 텍스트로 렌더링합니다.
- LocalStorage 구현 시 JSON 파싱, 데이터 형식 및 저장 실패를 처리합니다.
- 로직 변경 시 해당 동작에 필요한 검증을 수행하고 관련 문서를 갱신합니다.

## 실행과 검증

프로젝트 폴더에서 `python3 -m http.server 8000 --bind 127.0.0.1`을 실행하고
http://127.0.0.1:8000 에서 확인합니다. 서버 루트에 민감한 파일을 두지 않습니다.

- HTML·CSS·JS 리소스 로딩과 브라우저 콘솔 오류를 확인합니다.
- JavaScript 변경 시 필요에 따라 `node --check js/app.js`로 문법을 확인합니다.
- 기능 변경 시 정상·경계·예외 입력, 기존 기능 영향과 LocalStorage 복원을 확인합니다.
- UI 변경 시 모바일·데스크톱 화면과 키보드 조작을 확인합니다.
- 실행하지 못한 검증을 성공했다고 기록하지 않습니다.

## GitHub 작업

- GitHub MCP를 우선 사용합니다. 사용자에게 지정받은 도구 제한을 따릅니다.
- Issue·라벨·브랜치·PR을 만들기 전에 기존 항목을 확인해 중복을 방지합니다.
- 작업 브랜치는 `<phase>/<issue번호>-<작업명>` 형식을 사용합니다.
- 작업 시작 시 가능한 경우 Project 상태를 `In progress`로 변경합니다.
- 커밋에는 요청 범위의 파일만 포함하고 PR에 관련 Issue와 검증 결과를 작성합니다.
- 사용자의 명시적 요청 없이 PR을 병합하거나 Issue를 완료 처리하지 않습니다.

## 민감 정보

- `.env`, GitHub PAT 및 인증 정보를 출력하거나 커밋하지 않습니다.
- `.codex/`는 로컬 설정으로 취급합니다.
- `.gitignore`에 있어도 이미 추적 중이면 제외되지 않습니다. 추적 여부를 별도로 확인합니다.
- 민감 정보가 발견되면 값은 노출하지 않고 파일 경로와 추적 여부만 보고합니다.
- 토큰 폐기·재발급이나 Git 이력 재작성은 사용자와 범위를 확인한 뒤 진행합니다.

## 결과 보고

변경 파일, 검증 결과, 미완료 항목과 제약을 간결하게 보고합니다.
원격 변경을 수행한 경우 가능한 범위에서 재조회하고 Issue·PR·브랜치 링크를 제공합니다.

## GitHub Issue Automation Rules

### 1. Issue Verification

- Read the target Issue using GitHub MCP.
- Review its description, checklist, and acceptance criteria.
- Check the current local Git state.
- Check existing branches, commits, and Pull Requests.
- Never duplicate completed work.

### 2. Completed Issue Handling

If all acceptance criteria are satisfied:

- Skip unnecessary implementation.
- Update only verified checklist items.
- Verify the related PR and merge status.
- Close the Issue only when completion is confirmed.
- Update GitHub Project status to Done when supported.
- Proceed to the next Issue in the planned sequence.

### 3. Incomplete Issue Handling

If an Issue is incomplete:

- Work only on missing requirements.
- Create or reuse an Issue-specific branch.
- Preserve existing files and changes.
- Implement the required changes locally.
- Run relevant tests.
- Update verified checklist items.
- Commit and push changes.
- Create a Pull Request.
- Never merge without user approval.

### 4. GitHub Workflow

- Prefer GitHub MCP for supported operations.
- Do not create duplicate Issues, branches, or PRs.
- Use Conventional Commits.
- Include `Closes #N` in PR descriptions.
- Never force-push or delete branches without approval.
- Never overwrite uncommitted changes.

### 5. Sequential Issue Execution

- Process Issues in the specified order.
- Skip implementation for already completed Issues.
- Proceed automatically only when the previous Issue
  is fully verified and completed.
- Stop when a PR requires approval or merge.
- Do not assume Issue numbers always represent
  development priority.

### 6. Reporting

For each Issue, report:

- Issue number and title
- Completion status
- Branch name
- Changed files
- Test results
- Updated checklist items
- Commit hash
- Pull Request URL
- Remaining work or blockers
