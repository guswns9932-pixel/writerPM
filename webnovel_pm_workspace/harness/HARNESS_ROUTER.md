# HARNESS_ROUTER

작업 유형별로 반드시 확인해야 할 harness와 프로젝트 상태 파일을 지정하는 문서형 router입니다.

## 목적

- Codex가 작업 유형별 필수 harness를 누락하지 않도록 한다.
- 승인 없는 회차 작성, final 덮어쓰기, 능력 규칙 drift, 복선 망각, 말투 drift, 보고 누락을 사전에 차단한다.
- 이 workspace는 API나 외부 자동화 앱이 아니라 Codex 안에서 자연어 지시로 운영되는 문서/템플릿 중심 workspace임을 유지한다.

## 공통 hard gate

모든 작업 전 다음을 확인합니다.

- `AGENTS.md`
- `CODEX_WORKFLOW.md`
- `PROJECT_POLICY.md`
- `REPORT_FORMAT.md`
- `WORKFLOW_HARNESS.md`
- `MEMORY_HARNESS.md`
- `VERSIONING_HARNESS.md`
- `projects/{project_id}/approval_state.json` 또는 해당 역할 문서
- `projects/{project_id}/final_registry.json` 또는 해당 역할 문서

다음 중 하나라도 불명확하면 원고, final, 다음 배치, canon 변경을 진행하지 않고 사용자 확인 필요 사항으로 보고합니다.

- 승인된 작업 범위
- 수정 가능한 파일 범위
- current_stage
- 기존 final 보호 상태
- critical issue 여부

## Request type routing

| request_type | 예시 사용자 요청 | 반드시 확인할 harness | 반드시 확인할 상태 파일 | 금지 행동 |
|---|---|---|---|---|
| `audit_only` | “검토해줘”, “문제만 찾아줘” | CONTINUITY, QUALITY, ORIGINALITY, CONTENT_RISK | 관련 원고, 기억 파일, final_registry | 파일 수정, 원고 재작성, 설정 반영 |
| `plan_only` | “계획만 작성해줘”, “바로 수정하지 마” | WORKFLOW, FEEDBACK, RECOVERY, VERSIONING | approval_state, final_registry, user_feedback_log | 원고/설정 직접 수정 |
| `concept_generation` | “컨셉 후보 생성” | WORKFLOW, ORIGINALITY, HUMAN_CONTRIBUTION | brief, user_taste_profile | 선택 전 Bible 확정 |
| `bible_generation` | “Bible 생성/보강” | MEMORY, CONTINUITY, ORIGINALITY, THEMATIC, CONTEXT_COMPRESSION | approval_state, canon_log, approved canon 역할 문서, thematic_compass, arc_canon_snapshot | 승인 없는 핵심 canon 확정 |
| `episode_outline` | “N화 outline 작성” | WORKFLOW, MEMORY, CONTINUITY, QUALITY, CAST, PATTERN_REPETITION, LONGFORM, THEMATIC, PACING, VOICE_DRIFT, CONTEXT_COMPRESSION | approval_state, arc_state, payoff_schedule, episode_pattern_log, opposition_ladder, voice_samples, thematic_compass, pacing_curve, emotional_promise_ledger, world_expansion_policy | 승인되지 않은 회차 outline 작성 |
| `episode_draft` | “N화 draft 작성” | WORKFLOW, MEMORY, CONTINUITY, QUALITY, CAST, PATTERN_REPETITION, CONTENT_RISK, STYLE, READABILITY, KOREAN_GRAMMAR | approval_state, ability_usage_log, payoff_schedule, voice_samples, final_registry | 승인되지 않은 회차 본문 작성 |
| `revision` | “수정해줘” | FEEDBACK, VERSIONING, CONTINUITY, QUALITY, STYLE, READABILITY, KOREAN_GRAMMAR, CHARACTER/VOICE 역할 문서 | feedback_application_plan, final_registry, voice_samples, approval_state | 기존 final 직접 편집 |
| `canon_change_request` | “설정 변경 요청서 작성” | CONTINUITY, RECOVERY, ORIGINALITY | canon_log, story_bible, ability_rules, approval_state | 사용자 승인 전 Bible 직접 수정 |
| `recovery_plan` | “복구 계획 작성” | RECOVERY, VERSIONING, CONTINUITY | final_registry, episode_status, run_report_index | 복구 계획 없이 final 저장 |
| `project_discontinuation` | “이 프로젝트 그만할래”, “중단해줘” | RECOVERY, WORKFLOW, VERSIONING | approval_state, final_registry, quality_trend_log | discontinuation_report 없이 프로젝트 폴더 삭제/정리 |
| `packaging` | “패키징/투고 준비” | VERSIONING, RIGHTS, PLATFORM, CONTENT_RISK, ORIGINALITY | final_registry, rights_log, platform_policy_check, ai_usage_disclosure_note | 권리/플랫폼 미확인 공개용 확정 |

## High-risk state files

다음 상태 파일은 High 심각도/High 발생 가능성 위험을 줄이기 위한 우선 확인 대상입니다.

- `approval_state.json`: 승인 없는 회차/배치 작성 방지
- `final_registry.json`: final 후보/승인본/버전 보호
- `ability_usage_log.json`: 능력 규칙 위반과 갑작스러운 파워업 방지
- `payoff_schedule.json`: 복선 망각과 독자 보상 지연 방지
- `voice_samples.md`: 주인공/조연 말투 drift 방지
- `quality_trend_log.json`: 재미 하락 추세 감지
- `reader_reward_ledger.json`: 독자 보상 반복/누락 감지
- `run_report_index.json`: 보고 누락과 최신 작업 범위 혼선 방지
- `thematic_compass.json`: 주제 drift 방지
- `pacing_curve.json`: 거시적 페이싱 붕괴 방지
- `emotional_promise_ledger.json`: 독자 감정 계약 이행 추적
- `arc_canon_snapshot` (latest): arc 경계 이후 일관성 기준점
- `world_expansion_policy.json`: 세계관 비대화 방지
- `context_compression_log.md`: 메모리 압축 상태 확인

## 중단 조건

다음 경우 즉시 중단하고 `halt_reason_code`와 `recovery_plan`을 작성합니다.

- `approval_state`가 허용하지 않은 회차 또는 배치를 작성하려는 경우
- 기존 final 파일을 직접 수정하려는 경우
- final_registry와 episode status가 충돌하는 경우
- 능력 사용이 ability_rules/power_progression/ability_usage_log 기준과 충돌하는 경우
- payoff_schedule상 overdue thread가 critical인데 새 복선을 추가하려는 경우
- voice_samples와 충돌하는 말투 drift가 발생했는데 revision_note 없이 final 저장하려는 경우
- STYLE_HARNESS/READABILITY_HARNESS/KOREAN_GRAMMAR_HARNESS 기준 위반(AI식 문장, 가독성 미달, 문법 오류)이 반복되는데 revision_note 없이 final 저장하려는 경우
- run_report 없이 작업을 완료하려는 경우

## Request Type 선판정 규칙

작업 전 사용자 요청을 먼저 분류합니다.

| request_type | 판단 기준 | 파일 변경 가능 여부 | 필수 보고 |
|---|---|---|---|
| `audit_only` | 검토, 리뷰, 점검, 문제 찾기 | 원칙적으로 불가 | 발견 사항, 수정 제안, 수정 금지 준수 |
| `plan_only` | 계획, recovery_plan, feedback_application_plan, canon_change_request | 요청한 계획 파일만 가능 | 원문/해석/승인 필요 여부 |
| `proposal_only` | 제안, 추천, 분석 보고서 | 원칙적으로 불가 | 제안 목록, 우선순위 |
| `episode_outline` | 회차 outline 작성 | 승인된 회차만 가능 | approval_state, ability_usage 계획 |
| `episode_draft` | draft/final 작성 | 승인된 회차만 가능 | ability/payoff/reward/final 보호 |
| `revision` | 수정 요청 | 기존 final 직접 수정 불가 | feedback plan, 새 버전 여부 |

`audit_only`, `proposal_only` 요청에서 파일 변경이 필요해 보이면 변경하지 않고 “수정 제안”으로만 보고합니다.

## Required Outputs Matrix 연결

`REQUIRED_OUTPUTS_MATRIX.md`가 있으면 모든 prompt 실행 전 다음을 확정합니다.

- 필수 입력 파일
- 필수 출력 파일
- 작업 후 업데이트 파일
- 금지 파일 또는 읽기 전용 파일
- run_report 필요 여부
- 사용자 승인 필요 여부

matrix와 사용자 요청이 충돌하면 사용자 요청 범위를 우선하되, 안전 규칙 위반이 있으면 작업을 중단하고 보고합니다.

> **장기 연재(20화+) 주의사항**: episode_outline 및 episode_draft 작업 전 `CONTEXT_COMPRESSION_HARNESS.md`의 Cold Start 프로토콜 확인 필수. rolling_context.md가 압축되지 않은 상태에서 작업하면 설정 drift 위험이 높다.
