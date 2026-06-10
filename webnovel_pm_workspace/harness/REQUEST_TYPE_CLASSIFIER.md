# REQUEST_TYPE_CLASSIFIER

Codex가 사용자 요청을 작업 전에 분류해 작업 범위 초과와 원치 않는 파일 수정을 막기 위한 문서형 harness입니다.

## 분류 순서

1. 사용자 요청에 “검토만”, “리뷰만”, “분석”, “제안”, “아직 수정하지 말고”, “보고서만”이 있는지 확인한다.
2. 위 표현이 있으면 기본 request_type은 `audit_only`, `proposal_only`, `plan_only` 중 하나다.
3. 사용자가 파일 저장 위치를 명시했는지 확인한다.
4. 파일 저장 위치가 있어도 “수정하지 말고”가 있으면 기존 파일은 수정하지 않고 요청한 보고서 파일만 생성 가능한지 판단한다.
5. 원고, outline, draft, final, batch, revision, canon 변경은 `approval_state.json`과 `HARNESS_ROUTER.md` 기준으로 별도 승인한다.

## request_type별 기본 행동

| request_type | 기본 행동 | 금지 행동 |
|---|---|---|
| `audit_only` | 대화 보고 또는 요청된 audit 파일 작성 | 원고/설정 수정 |
| `proposal_only` | 제안 목록 작성 | 파일 생성/수정, 원고 작성 |
| `plan_only` | 요청된 계획서 작성 | 계획 범위를 넘어 실제 수정 |
| `episode_outline` | 승인된 회차 outline 작성 | 승인 없는 다음 회차 |
| `episode_draft` | 승인된 회차 draft/final 작성 | 기존 final 덮어쓰기 |
| `revision` | 승인된 범위의 새 버전 제안/작성 | 기존 final 직접 편집 |
| `canon_change_request` | 변경 요청서 작성 | 승인 전 Bible 직접 수정 |

## 보고 필수 항목

- 판정한 request_type
- 파일 생성/수정 가능 여부
- 승인 상태 확인 여부
- 금지된 작업 범위
- 사용자 확인 필요 사항
