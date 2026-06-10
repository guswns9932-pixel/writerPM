# VERSIONING_HARNESS

원고 final과 수정본의 버전 보존을 위한 문서형 harness입니다.

## 목적

- 기존 final 덮어쓰기 금지
- 수정본을 `v3`, `v4`처럼 새 버전으로 저장
- `episode_XXX_status.md`에서 `current_final` 지정
- 이전 버전 보존

## final 파일 보호 원칙

- 기존 final 파일은 절대 덮어쓰지 않습니다.
- final 수정본은 새 파일로 저장합니다.
- 덮어쓰기 위험이 있으면 즉시 중단하고 `halt_reason_code`와 `recovery_plan`을 작성합니다.

## 버전명 규칙

권장 예시:

- `episode_001_final_v1.md`
- `episode_001_final_v2.md`
- `episode_001_final_v3.md`
- `episode_001_revision_note_v3.md`
- `episode_001_review_v3.md`

수정본은 `v3`, `v4`처럼 증가하는 버전 번호를 사용합니다. 기존 버전을 직접 수정하지 않습니다.

## `episode_XXX_status.md` 필수 항목

각 회차마다 `episode_XXX_status.md`를 작성하고 다음 항목을 포함합니다.

- 회차 번호
- 현재 상태
- `current_final`
- 최신 draft
- 최신 review
- 최신 revision_note
- 사용자 승인 상태
- 다음 가능한 작업
- 보존해야 할 이전 버전 목록

## `current_final` 지정 규칙

- `current_final`은 사용자가 현재 기준본으로 승인했거나 Codex가 최신 final 후보로 보고한 파일을 가리킵니다.
- 새 final 버전을 만들면 `episode_XXX_status.md`에 `current_final` 후보를 업데이트합니다.
- 사용자 승인 전에는 “승인 대기” 상태를 함께 기록합니다.

## 이전 버전 보존 규칙

- 이전 final 버전은 삭제하지 않습니다.
- 이전 review와 revision_note도 가능한 한 보존합니다.
- 폐기된 버전이라도 archive 또는 상태 파일에 이유를 기록합니다.
- 파일 정리가 필요하면 사용자에게 먼저 확인합니다.

## 작업 전 점검

- [ ] 수정 대상 final 파일이 기존 파일인지 확인했다.
- [ ] 새 버전 파일명을 정했다.
- [ ] `episode_XXX_status.md` 갱신이 필요한지 확인했다.
- [ ] 이전 버전을 삭제하거나 덮어쓰지 않는다.

## 작업 후 점검

- [ ] 새 버전 파일이 별도 저장되었다.
- [ ] `episode_XXX_status.md`의 `current_final` 또는 승인 대기 상태가 갱신되었다.
- [ ] 이전 버전이 보존되었다.
- [ ] 변경 파일 목록을 보고했다.

## final_registry 필수 연동

- final 후보 또는 승인본을 생성하면 `final_registry.json` 또는 해당 역할 문서를 갱신합니다.
- 기존 final 파일은 읽기 전용으로만 참조하고 직접 편집하지 않습니다.
- `episode_XXX_status.md`의 `current_final`과 `final_registry.json`의 `current_final_candidate`가 다르면 final 저장을 중단합니다.
- 승인된 final과 승인 대기 final 후보를 구분합니다.
- registry/status 불일치가 있으면 `halt_reason_code: FINAL_REGISTRY_MISMATCH`를 기록하고 `recovery_plan`을 작성합니다.
