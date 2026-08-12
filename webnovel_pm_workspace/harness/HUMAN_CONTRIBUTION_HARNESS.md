# HUMAN_CONTRIBUTION_HARNESS

사용자의 창작적 선택, 수정, 승인 이력을 기록하기 위한 문서형 harness입니다.

## 목적

- 사용자가 직접 선택한 컨셉, 설정, 방향성 기록
- 사용자 피드백과 승인 이력 보존
- Codex 생성물과 사용자 창작 기여 구분
- 작업 파일과 권리/기여 관리 혼선 방지

## 필수 확인 파일

- `human_contribution_log.md`
- `user_feedback_log.json`
- `change_log.md`
- `rights_log.md`
- `feedback_application_plans/`
- `canon_change_requests/`

## 기록 대상

- 사용자가 제공한 제목, 장르, 핵심 아이디어, 금지 요소
- 사용자가 선택한 컨셉 후보
- 사용자가 승인한 final 또는 batch
- 사용자가 거절한 방향
- 사용자가 직접 제안한 문장, 장면, 설정, 캐릭터
- 사용자가 요구한 수정 방향
- 사용자가 승인한 canon 변경

## 작업 후 점검

- [ ] 사용자 피드백이 `user_feedback_log.json`에 기록되었다.
- [ ] 창작적 결정 또는 승인 사항이 `human_contribution_log.md`에 기록되었다.
- [ ] 설정/원고/canon 변경은 `change_log.md`에 기록되었다.
- [ ] canon 변경은 승인 전 `canon_change_request`에 머문다.
- [ ] 바로 반영이 아닌 피드백은 `feedback_application_plan`을 먼저 작성했다.

## 중단 조건

- 사용자 승인 없이 창작 방향을 확정하려 한다.
- 사용자 피드백을 기록하지 않고 원고를 수정하려 한다.
- canon 변경 승인 여부가 불분명한데 Bible 또는 final에 반영하려 한다.

## 보고 항목

- 기록한 사용자 기여
- 기록한 피드백
- 승인 대기 중인 항목
- 사용자 확인 필요 사항
