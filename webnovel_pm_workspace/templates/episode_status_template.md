# Episode Status Template

## 회차 정보

- episode_id: episode_001
- episode_number: 1
- title: 예시 회차 제목
- status: outline / draft / review / revision / final_candidate / approved / halted
- current_final: 승인 대기 또는 `episode_001_final_v1.md`
- user_approval: pending / approved / rejected

## 현재 파일

- latest_outline: `episode_001_outline.md`
- latest_draft: `episode_001_draft_v1.md`
- latest_review: `episode_001_review_v1.md`
- latest_revision_note: `episode_001_revision_note_v1.md`
- latest_run_report: `run_report_YYYYMMDD_001.md`

## 품질 체크

- 첫 500자 후킹: pending / pass / fail
- 주인공 욕망과 선택: pending / pass / fail
- 독자 보상: pending / pass / fail
- 클리프행어: pending / pass / fail
- 모바일 가독성: pending / pass / fail
- 독창성: pending / pass / fail

## 연속성 체크

- story_bible: pending / pass / fail
- character_bible: pending / pass / fail
- ability_rules: pending / pass / fail
- power_progression: pending / pass / fail
- timeline: pending / pass / fail
- canon_log: pending / pass / fail

## 이전 버전 보존 목록

| version | file | status | note |
|---|---|---|---|
| v1 | episode_001_final_v1.md | candidate | 사용자 승인 대기 |

## 다음 가능한 작업

-

## High-risk 상태 참조

- approval_state_ref: `approval_state.json`
- final_registry_ref: `final_registry.json`
- ability_usage_log_ref: `ability_usage_log.json`
- payoff_schedule_ref: `payoff_schedule.json`
- quality_trend_log_ref: `quality_trend_log.json`
- reader_reward_ledger_ref: `reader_reward_ledger.json`
- voice_samples_ref: `voice_samples.md`

## High-risk 체크

- 승인된 작업 범위 안에서 작성됨: pending / pass / fail
- final_registry와 current_final 일치: pending / pass / fail
- 능력 사용 기록 완료: pending / pass / fail / not_applicable
- 복선 회수 일정 갱신: pending / pass / fail / not_applicable
- 독자 보상 ledger 갱신: pending / pass / fail
- 품질 추세 갱신: pending / pass / fail
- 주인공/주요 인물 말투 안정성: pending / pass / fail

## Registry / Approval Sync

- approval_state_current_stage:
- approval_state_allowed_scope:
- final_registry_current_final_candidate:
- final_registry_approved_final:
- status_registry_match: pending / pass / fail
- mismatch_halt_reason_code: none / FINAL_REGISTRY_STATUS_MISMATCH
- existing_final_read_only_confirmed: pending / pass / fail
