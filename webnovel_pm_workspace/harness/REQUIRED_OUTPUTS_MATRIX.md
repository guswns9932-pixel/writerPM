# REQUIRED_OUTPUTS_MATRIX

작업 유형별 필수 입력 파일, 출력 파일, 업데이트 파일, 금지 행동을 정리한 문서형 matrix입니다.

## 공통 입력

- `AGENTS.md`
- `CODEX_WORKFLOW.md`
- `PROJECT_POLICY.md`
- `REPORT_FORMAT.md`
- `HARNESS_ROUTER.md`
- `REQUEST_TYPE_CLASSIFIER.md`
- `approval_state.json`
- `final_registry.json`

## Matrix

| request_type | 필수 입력 | 필수 출력 | 작업 후 업데이트 | 금지 행동 |
|---|---|---|---|---|
| `audit_only` | 대상 파일, 관련 harness | 대화 보고 또는 요청된 audit report | 없음 또는 요청된 report만 | 원고/설정 직접 수정 |
| `plan_only` | 대상 issue, 관련 status/log | plan 파일 | user_feedback_log 또는 run_report 필요 시 | 실제 원고/설정 반영 |
| `concept_generation` | brief, policy, taste profile | concept_candidates | rolling_context, run_report | 선택 전 Bible 확정 |
| `bible_generation` | concept, brief, approval_state | Bible 후보 또는 보강안 | canon_log 또는 canon_change_request, run_report | 승인 없는 핵심 canon 변경 |
| `episode_outline` | memory files, approval_state, ability_usage_log, payoff_schedule, voice_samples | episode_XXX_outline | ability_usage_log 예정 사용, payoff_schedule 예정 회수, run_report | 승인 없는 회차 outline |
| `episode_draft` | outline, memory files, approval_state, ability_usage_log, payoff_schedule, voice_samples | draft/final 후보 | ability_usage_log 실제 사용, reader_reward_ledger, quality_trend_log, status, run_report | 기존 final 덮어쓰기 |
| `revision` | feedback_plan, final_registry, status, target final | 새 version 파일, revision_note | final_registry, status, run_report | 기존 final 직접 편집 |
| `canon_change_request` | issue, Bible files, canon_log | canon_change_request | user_feedback_log 또는 run_report 필요 시 | 승인 전 Bible 수정 |
| `recovery_plan` | halt issue, status, registry, logs | recovery_plan | run_report 또는 index 필요 시 | 복구 전 final 저장 |
| `packaging` | final_registry, status, rights/platform/content checks | packaging report | run_report, policy check files | 권리/플랫폼 미확인 공개용 확정 |

## 완료 조건

- 필수 출력이 누락되면 작업 완료로 보고하지 않는다.
- 업데이트 파일이 누락되면 누락 사유와 사용자 확인 필요 사항을 보고한다.
- matrix가 사용자 요청과 충돌하면 안전 규칙을 우선하고 중단 사유를 보고한다.
