# MEMORY_HARNESS

원고 작성 전 필수 기억 파일을 확인하기 위한 문서형 harness입니다.

## 목적

원고 작성 전 프로젝트의 확정 설정, 인물, 능력 규칙, 시간선, 복선, 문체, 직전 맥락을 확인해 설정 충돌과 연속성 오류를 방지합니다.

## 필수 기억 파일 목록

원고 작성 전 다음 파일을 모두 확인해야 합니다.

- [ ] `story_bible.json`
- [ ] `character_bible.json`
- [ ] `ability_rules.json`
- [ ] `power_progression.json`
- [ ] `timeline.json`
- [ ] `arc_state.json`
- [ ] `cast_registry.json`
- [ ] `location_registry.json`
- [ ] `canon_log.json`
- [ ] `foreshadowing_ledger.json`
- [ ] `style_guide.json`
- [ ] `rolling_context.md`
- [ ] `user_feedback_log.json`
- [ ] `user_taste_profile.json`
- [ ] `episode_format_policy.json`
- [ ] `change_log.md`
- [ ] `human_contribution_log.md`
- [ ] `rights_log.md`
- [ ] `platform_policy_check.md`
- [ ] `episode_pattern_log.json`
- [ ] `opposition_ladder.json`
- [ ] `content_risk_check.md`
- [ ] `real_entity_risk_check.md`
- [ ] `sensitivity_check.md`

## 확인 기준

각 파일에서 최소한 다음 항목을 확인합니다.

### `story_bible.json`

- 작품 핵심 전제
- 장르 약속
- 핵심 갈등
- 금지 설정

### `character_bible.json`

- 주요 인물 성격
- 욕망과 결핍
- 말투
- 관계 변화

### `ability_rules.json`

- 능력 사용 조건
- 능력 한계
- 비용과 대가
- 금지된 사용 방식

### `power_progression.json`

- 현재 성장 단계
- 허용된 강화 범위
- 갑작스러운 파워업 금지 조건

### `timeline.json`

- 사건 순서
- 이동 시간
- 회복 시간
- 정보 전달 시점

### `arc_state.json`

- 현재 arc
- arc 목표
- 주인공 상태 변화
- 열린 갈등

### `cast_registry.json`

- active cast
- 신규 named character
- 역할 중복
- dormant/merged/removed 상태

### `location_registry.json`

- 장소 구조
- 이동 가능성
- 공간 제약
- 장소별 canon 상태

### `canon_log.json`

- 확정 canon
- canon 변경 이력
- 사용자 승인 여부

### `foreshadowing_ledger.json`

- 활성 복선
- 회수 예정 복선
- 아직 공개하면 안 되는 정보

### `style_guide.json`

- 문체
- 대사 톤
- 금지 표현
- 모바일 가독성 기준

### `rolling_context.md`

- 직전 회차 요약
- 현재 감정선
- 미해결 갈등
- 다음 회차에 유지해야 할 정보

## 누락 시 작업 중단

필수 파일이 하나라도 누락되면 다음을 수행합니다.

1. 원고 작성과 final 저장을 중단한다.
2. 누락된 파일 목록을 기록한다.
3. `halt_reason_code: MEMORY_FILE_MISSING`을 기록한다.
4. 누락 파일 생성 또는 보강을 위한 `recovery_plan`을 작성한다.
5. 사용자 승인 또는 지시 전에는 원고 작성을 진행하지 않는다.

## 장기 연재 추가 확인

20화 이상 장기 연재 프로젝트는 원고 작성 전 `CAST_HARNESS`와 `LONGFORM_HARNESS`도 함께 확인합니다. 특히 새 인물 추가, 10화 단위 audit, arc gate, 복선 회수 계획은 별도 점검 대상입니다.

투고, 공개, packaging, 민감 소재, 실존 유사성, 외부 자료 사용이 포함되면 `RIGHTS_HARNESS`, `PLATFORM_HARNESS`, `CONTENT_RISK_HARNESS`, `HUMAN_CONTRIBUTION_HARNESS`, `PATTERN_REPETITION_HARNESS`도 확인합니다.

## High-risk 추가 필수 기억 파일

High 심각도/High 발생 가능성 위험을 줄이기 위해 원고 작성, 회차 개요, 수정, 배치 작업 전 다음 파일도 확인합니다.

- [ ] `approval_state.json`
- [ ] `final_registry.json`
- [ ] `ability_usage_log.json`
- [ ] `payoff_schedule.json`
- [ ] `quality_trend_log.json`
- [ ] `reader_reward_ledger.json`
- [ ] `voice_samples.md`
- [ ] `run_reports/run_report_index.json`

누락 시 final 저장 전 누락 사실을 보고하고, 해당 파일 생성 또는 보강을 사용자 확인 필요 사항으로 정리합니다.
