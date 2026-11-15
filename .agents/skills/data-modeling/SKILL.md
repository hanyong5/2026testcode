---
name: data-modeling
description: "Design or review Todo List entities, field constraints, JSON Schema, LocalStorage keys and versions, CRUD data flows, validation, and recovery policies. Use for 데이터 모델·저장 구조 설계 and Mermaid data diagrams, not runtime feature implementation."
---

# Data Modeling

이 저장소의 요구사항을 검증 가능한 데이터 설계로 연결합니다.
사용자가 구현까지 요청하지 않았다면 설계 문서·예시·스키마만 작성합니다.

## 입력과 기준

- AGENTS.md, 대상 Issue의 실제 본문, docs/requirements.md와 docs/user-scenarios.md를 읽고 기존 정책·산출물·PR을 확인합니다.
- 확정된 요구사항과 새 설계 제안을 구분하고 FR·US·미확정 정책 ID를 연결합니다. 기존 Todo 텍스트 규칙, 필터 동작, 배열 순서와 데이터 보호 요구를 임의로 바꾸지 않습니다.
- HTML5·CSS3·Vanilla JavaScript·LocalStorage 범위에서 설계합니다. 요청 없이 서버·데이터베이스·인증을 도입하지 않습니다.

## 모델과 저장 계약

- 엔티티·속성별 타입, 필수 여부, 생성 기본값, 수정 가능 여부, 직렬화 형태를 정의합니다. JSON의 문자열·숫자·불리언과 JavaScript의 Date·undefined 등을 구분합니다.
- ID 생성·충돌 확인·실패 정책과 createdAt·updatedAt의 시각 형식·시간 역행·수정 시점을 정의합니다. 목록 순서의 기준을 명시합니다.
- 저장 문서의 JSON 예시와 JSON Schema 방언을 명시합니다. 필드 누락·추가 필드·타입 불일치와 Unicode 길이를 검토합니다.
- JSON Schema의 default는 값을 자동 보충하지 않습니다. uniqueItems만으로 객체의 id 유일성을 보장하지 않으며, 필드 간 시간 순서는 별도 의미 검증으로 정의합니다. format 검증을 실제 활성화했는지 확인합니다.
- LocalStorage 키, 저장 단위, 초기 상태, 버전 식별·호환성·마이그레이션·미지원 버전 정책을 구체화합니다. 필터·편집 초안·저장 오류처럼 메모리 전용 상태를 영속 데이터에서 분리합니다.

## 데이터 흐름과 보호

- CRUD·완료 전환별 입력 검증 → 데이터 변경 → 전체 스냅샷 직렬화·저장 → 화면 피드백을 연결합니다. 필터가 숨긴 데이터도 포함하고 조회·필터 변경의 비변경 조건을 명시합니다.
- 사용자 입력 정규화와 저장된 데이터의 검증을 구분합니다. 잘못된 저장 데이터를 조용히 보정·부분 삭제하여 덮어쓰지 않습니다.
- 파싱 실패, 구조·의미 검증 실패, 읽기 제한, 직렬화 실패, 용량 초과 및 일반 쓰기 실패를 구분합니다. 메모리 데이터·마지막 저장 데이터·사용자 안내·재시도 조건을 각각 정의합니다.
- 손상·미지원 원본을 보호하고 명시적 초기화·교체 동의 전의 자동 저장을 차단합니다. 다른 앱의 키를 건드리거나 저장 전에 기존 값을 먼저 삭제하는 흐름을 만들지 않습니다.
- 복구 시 메모리의 미저장 변경과 기존 저장 데이터가 충돌하면 자동 병합·폐기를 가정하지 않습니다. 미결정 정책은 제안과 영향으로 보고합니다.

## 산출물과 검증

- 기본 산출물은 docs/data-model.md입니다. 목적·요구사항 연결·필드 표·JSON 예시·JSON Schema·저장 정책·CRUD 흐름·예외 처리·결정 근거를 포함합니다.
- 다이어그램이 요청되면 classDiagram, flowchart TD, sequenceDiagram, stateDiagram-v2를 GitHub의 mermaid 코드 블록으로 작성하고 문서 계약과 대조합니다.
- JSON 파싱, 스키마 자체 검증과 예시 검증을 실제 도구로 수행합니다. 정상·경계·잘못된 값 및 스키마 밖의 ID·시간·정규화 제약을 구분해 확인합니다.
- Mermaid 파서 또는 렌더러로 문법을 검사하고 사용 버전을 기록합니다. 정적 검사·로컬 렌더링·GitHub 화면 확인을 서로 구분합니다.
- 설계·스킬 검증과 실제 브라우저 LocalStorage 동작 검증을 구분합니다. 검증한 항목만 Issue에 체크하고, 요청 범위와 AGENTS.md에 따라 커밋·PR 결과 및 남은 결정을 보고합니다.
