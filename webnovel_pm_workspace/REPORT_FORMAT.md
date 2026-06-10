# REPORT_FORMAT.md

이 문서는 Codex가 작업 완료 후 사용자에게 항상 보고해야 하는 형식을 정의합니다.

## 기본 보고 원칙

- 보고는 작업 직후 작성합니다.
- 사용자가 요청한 범위 안에서 수행한 내용만 보고합니다.
- 변경 파일 목록을 명확히 구분합니다.
- 사용자 확인이 필요한 항목과 다음 가능한 작업을 분리합니다.
- 다음 작업은 제안만 가능하며, 사용자 지시 없이 실행하지 않습니다.

## 보고 형식

Codex는 작업 완료 후 아래 형식을 사용합니다.

```md
## 작업 완료 보고

### 1. 수행한 작업

-

### 2. 생성한 파일

-

### 3. 수정한 파일

-

### 4. 검수 결과

- 설정:
- 능력 규칙:
- 인물:
- 시간선:
- 문체:
- 재미:
- 복선:
- 독창성:

### 5. 설정 충돌 여부

- 상태: 없음 / 있음 / 확인 필요
- 상세:

### 6. 품질 이슈 여부

- 상태: 없음 / 있음 / 확인 필요
- 상세:

### 7. 사용자 확인 필요 사항

-

### 8. 다음 가능한 작업

-
```

## 필수 보고 항목 설명

### 수행한 작업

이번 요청에서 실제로 수행한 작업만 요약합니다.

### 생성한 파일

새로 만든 파일 경로를 나열합니다. 생성한 파일이 없으면 “없음”이라고 적습니다.

### 수정한 파일

기존 파일 중 수정한 파일 경로를 나열합니다. 수정한 파일이 없으면 “없음”이라고 적습니다.

### 검수 결과

원고 또는 기획 산출물이 포함된 작업이라면 다음 항목을 점검합니다.

- 설정
- 능력 규칙
- 인물
- 시간선
- 문체
- 재미
- 복선
- 독창성

문서 구조만 변경한 작업이라면 “원고 생성 없음” 또는 “해당 없음”으로 표시합니다.

### 설정 충돌 여부

설정 충돌, 능력 규칙 위반, 인물 붕괴, 시간선 오류가 있는지 기록합니다. 확인이 불가능하면 “확인 필요”로 표시합니다.

### 품질 이슈 여부

후킹, 주인공 선택, 독자 보상, 클리프행어, 장르 기대 충족, 독창성에 문제가 있는지 기록합니다. 원고 작업이 아니면 “해당 없음”으로 표시합니다.

### 사용자 확인 필요 사항

사용자의 승인, 선택, 추가 정보가 필요한 항목을 적습니다. 없으면 “없음”이라고 적습니다.

### 다음 가능한 작업

다음에 진행할 수 있는 작업 후보만 적습니다. Codex는 이 항목을 작성해도 사용자 지시 전에는 실행하지 않습니다.

## critical issue 보고 형식

critical issue가 발생하면 일반 보고와 함께 아래 항목을 추가합니다.

```md
### Critical Issue

- halt_reason_code:
- 문제 요약:
- 영향 범위:
- 관련 파일:
- recovery_plan:
- 사용자 결정 필요 사항:
```

## High-risk 필수 보고 항목

원고 생성, 회차 검수, 수정, 배치 작업, packaging 작업을 수행한 경우 기본 보고 형식에 더해 아래 항목을 반드시 보고합니다.

```md
### 9. 요청 유형 및 승인 상태

- request_type:
- approval_state 확인 여부:
- 승인된 작업 범위:
- current_stage:
- 다음 회차/다음 배치 진행 가능 여부:

### 10. Harness 확인 결과

- 확인한 harness:
- HARNESS_ROUTER 기준 충족 여부:
- 누락된 harness 또는 확인 불가 항목:

### 11. Final / Version 보호

- final_registry 갱신 여부:
- 새 final 파일:
- 기존 final 덮어쓰기 여부:
- current_final_candidate:
- approved_final:
- episode_status와 registry 일치 여부:

### 12. 능력 / 설정 안정성

- ability_usage_log 갱신 여부:
- 이번 회차 능력 사용:
- 능력 규칙 위반 여부:
- 갑작스러운 파워업 여부:
- canon_change_request 필요 여부:

### 13. 복선 / 독자 보상 / 장기 회수

- payoff_schedule 갱신 여부:
- reader_reward_ledger 갱신 여부:
- quality_trend_log 갱신 여부:
- 새 복선:
- 회수된 복선:
- 지연된 복선:
- 독자 보상 유형:
- 클리프행어 반복 위험:

### 14. 캐릭터 음성 / 피드백 안정성

- voice_samples 확인 여부:
- 주인공 말투 일치 여부:
- 주요 조연 말투 일치 여부:
- 피드백 영향 범위:
- character drift 위험:

### 15. 보고서 색인 및 완료 조건

- run_report 작성 여부:
- run_report_index 갱신 여부:
- 필수 산출물 누락 여부:
- 다음 가능한 작업에 실제 원고/설정 초안 포함 여부: 없음이어야 함
```

## High-risk critical issue 추가 보고 항목

critical issue가 approval, final registry, ability usage, payoff, voice, report index와 관련되면 아래 항목도 추가합니다.

```md
### High-risk State Impact

- approval_state 영향:
- final_registry 영향:
- ability_usage_log 영향:
- payoff_schedule 영향:
- voice_samples 영향:
- quality_trend_log 영향:
- reader_reward_ledger 영향:
- run_report_index 영향:
- 필요한 state repair:
```

## High/High 우선 보고 확장

원고 생성, 회차 outline/draft/review/final, 수정, batch, canon 변경 요청, feedback 반영 계획, recovery, packaging 작업 후에는 기본 보고에 더해 아래 항목을 포함합니다.

```md
### 16. 수정한 파일별 변경 이유

| 파일 | 변경 이유 | 연결된 High/High 항목 | 사용자 요청 범위 안 여부 |
|---|---|---|---|

### 17. High/High 안전 게이트 체크

- request_type 선판정:
- audit_only/plan_only 수정 금지 준수 여부:
- approval_state 확인 여부:
- 3화 초과 요청 제한 준수 여부:
- final_registry 확인 여부:
- episode_status/final_registry 일치 여부:
- 기존 final 덮어쓰기 여부:
- Bible 계열 직접 변경 여부:
- canon_change_request 필요 여부:
- ability_usage_log outline/draft/review 연결 여부:
- feedback_application_plan 영향도 매트릭스 확인 여부:
- foreshadowing_ledger/payoff_schedule 동기화 여부:
- HARNESS_ROUTER/REQUIRED_OUTPUTS_MATRIX 확인 여부:

### 18. 다음 프롬프트 추천

- 추천 목적:
- 사용자가 그대로 입력할 수 있는 프롬프트:
- 이 프롬프트가 진행하지 않는 것:
```

`다음 프롬프트 추천`에는 실제 다음 회차의 장면, 대사, 사건 전개, 새 canon 초안을 넣지 않습니다. 작업 후보와 안전 조건만 제안합니다.
