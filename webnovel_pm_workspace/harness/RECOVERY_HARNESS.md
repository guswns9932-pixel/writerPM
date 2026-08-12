# RECOVERY_HARNESS

critical issue 발생 시 안전하게 중단하고 복구 계획을 작성하기 위한 문서형 harness입니다.

## critical issue 예시

- 사용자 승인 없는 2화 이후 생성
- 요청 범위 초과 작업
- 기존 final 파일 덮어쓰기 위험
- 설정 충돌
- 능력 규칙 위반
- 갑작스러운 파워업
- canon 충돌
- 시간선 오류
- 인물 성격 붕괴
- 특정 기존 작품 또는 작가 문체 모방 위험

## 발생 시 기본 절차

1. 즉시 작업을 중단한다.
2. final 저장을 중단한다.
3. `halt_reason_code`를 기록한다.
4. 영향 범위를 확인한다.
5. 수정 범위를 분류한다.
6. `recovery_plan`을 작성한다.
7. 사용자 승인 또는 지시 전에는 확정 반영하지 않는다.

## 수정 범위 분류

### `TEXT_ONLY`

문장, 문단, 대사, 표현만 수정하면 해결 가능한 경우입니다.

- canon 변경 없음
- 장면 구조 변경 없음
- 시간선 영향 없음

### `SCENE_REWRITE`

특정 장면을 재작성해야 하는 경우입니다.

- 장면 목표 유지 가능
- 회차 전체 구조 유지 가능
- 인물 행동 또는 갈등 재설계 필요

### `EPISODE_OUTLINE_REWRITE`

회차 개요부터 다시 조정해야 하는 경우입니다.

- 장면 순서 변경 필요
- 회차 목표 또는 엔딩 훅 수정 필요
- 독자 보상 구조 재설계 필요

### `CONTINUITY_REPAIR`

연속성 보정이 필요한 경우입니다.

- 설정 충돌
- 능력 규칙 위반
- 시간선 오류
- 인물 성격 붕괴
- 공간 설정 충돌

### `BIBLE_CHANGE_REQUIRED`

Bible 또는 canon 변경이 필요한 경우입니다.

- 기존 canon과 충돌하지만 변경이 서사적으로 필요하다.
- 능력 규칙, 세계관 규칙, 인물 설정 변경이 필요하다.
- `canon_change_request`가 필요하다.
- 사용자 승인 전에는 반영하지 않는다.

## `BIBLE_CHANGE_REQUIRED` 승인 규칙

`BIBLE_CHANGE_REQUIRED`는 반드시 사용자 승인이 필요합니다.

처리 순서:

1. final 저장을 중단한다.
2. `canon_change_request`를 작성한다.
3. 변경 이유, 장점, 위험, 영향 범위를 적는다.
4. 사용자 승인 전에는 Bible, canon_log, 원고 final에 반영하지 않는다.
5. 승인 후에만 관련 파일을 갱신한다.

## recovery_plan 필수 항목

- `halt_reason_code`
- 문제 요약
- 수정 범위 분류
- 영향 받는 파일
- 보존해야 할 기존 파일
- 제안 복구 절차
- 사용자 승인 필요 여부
- 재개 가능한 최소 작업 단위

## High-risk 상태 복구 범위

다음 상태 파일 불일치는 recovery_plan 대상으로 처리합니다.

- `approval_state.json` 승인 범위와 실제 생성 파일 불일치
- `final_registry.json`과 `episode_XXX_status.md` 불일치
- `ability_usage_log.json` 누락 또는 능력 규칙 위반 기록 누락
- `payoff_schedule.json` 누락 또는 overdue thread 미보고
- `quality_trend_log.json` / `reader_reward_ledger.json` 누락으로 품질 추세 확인 불가
- `voice_samples.md` 기준 말투 drift 발생
- `run_report_index.json` 누락 또는 최신 run_report 불일치

## High/High recovery triggers

다음은 즉시 중단하고 recovery_plan을 작성해야 하는 High/High trigger입니다.

- `approval_state`와 사용자 요청 범위가 충돌한다.
- `final_registry`와 `episode_status`가 서로 다른 final을 가리킨다.
- 기존 final 파일을 직접 편집했거나 편집하려 한다.
- Bible 계열 핵심 설정 변경이 필요한데 canon_change_request가 없다.
- ability_usage_log 없이 능력 사용 장면을 final로 저장하려 한다.
- payoff_schedule상 critical overdue thread가 있는데 새 장기 복선을 추가하려 한다.
- run_report 없이 완료 보고하려 한다.

## 프로젝트 전체 중단(discontinuation) 절차

개별 회차 issue가 아니라 프로젝트 자체를 더 이상 진행하지 않기로 하는 경우(컨셉 폐기, 반복된 품질 미달, 사용자 지시 등)에는 위의 회차 단위 `recovery_plan`이 아니라 아래 절차를 따릅니다. 프로젝트 폴더를 삭제하는 것만으로 완료 처리하지 않습니다.

1. 중단 전 마지막 상태를 확인한다(`approval_state.json`, `final_registry.json`, `quality_trend_log.json`).
2. `projects/_discontinued/{project_id}_discontinuation_report.md`를 `templates/project_discontinuation_report_template.md` 형식으로 작성한다.
3. 보고서에 다음을 반드시 기록한다.
   - `discontinuation_reason`: 중단 사유(품질, 컨셉, 사용자 지시 등 구체적으로)
   - `decision_date`
   - `last_completed_stage`: 중단 시점까지 완료된 단계
   - `salvaged_learnings`: 이번 프로젝트에서 얻어 harness/prompt/template에 반영한 규칙이나 교훈
   - `preserved_artifacts`: git 이력 등 실제 삭제되지 않고 보존되는 위치
   - `user_confirmation`: 사용자가 중단을 승인했는지 여부
4. 프로젝트 폴더를 삭제하거나 비우기 전에 3번 보고서를 먼저 커밋한다.
5. `salvaged_learnings`에 적은 harness/prompt 변경이 실제로 반영되었는지 확인한다(반영되지 않았다면 중단 처리를 완료로 보고하지 않는다).
