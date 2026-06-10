# CONTINUITY_HARNESS

원고와 기획 산출물이 기존 canon 및 연속성과 충돌하지 않는지 검수하기 위한 문서형 harness입니다.

## 검수 기준 파일

다음 파일을 기준으로 검수합니다.

- `story_bible.json`
- `character_bible.json`
- `ability_rules.json`
- `power_progression.json`
- `timeline.json`
- `arc_state.json`
- `cast_registry.json`
- `location_registry.json`
- `canon_log.json`
- `foreshadowing_ledger.json`
- `episode_pattern_log.json`
- `opposition_ladder.json`
- `content_risk_check.md`
- `real_entity_risk_check.md`
- `sensitivity_check.md`

## 검수 항목

### 능력 규칙 위반

- [ ] 능력 사용 조건을 무시하지 않았다.
- [ ] 능력 한계가 갑자기 사라지지 않았다.
- [ ] 비용, 대가, 부작용이 유지된다.
- [ ] 금지된 사용 방식이 승인 없이 등장하지 않았다.

### 갑작스러운 파워업

- [ ] `power_progression.json`의 현재 성장 단계와 맞다.
- [ ] 강화에는 원인, 대가, 학습, 사건 중 하나 이상의 근거가 있다.
- [ ] 독자가 납득할 준비 과정 없이 위기를 해결하지 않는다.

### canon 충돌

- [ ] `canon_log.json`의 확정 설정과 충돌하지 않는다.
- [ ] 변경이 필요한 경우 `canon_change_request`를 먼저 작성한다.
- [ ] 사용자 승인 전 canon 변경을 원고나 Bible에 확정 반영하지 않는다.

### 시간선 오류

- [ ] 사건 순서가 `timeline.json`과 맞다.
- [ ] 이동, 회복, 수련, 정보 전달 시간이 납득된다.
- [ ] 같은 시간대에 동일 인물이 두 장소에 있지 않다.

### 인물 성격 붕괴

- [ ] `character_bible.json`의 욕망, 결핍, 말투와 일치한다.
- [ ] 성격 변화에는 사건 또는 감정적 근거가 있다.
- [ ] 단기 편의를 위해 인물이 기존 가치관과 모순되게 행동하지 않는다.

### 등장인물 과다 및 역할 중복

- [ ] 새 named character가 기존 인물로 대체 가능한 역할이 아니다.
- [ ] active cast가 arc 상한을 과도하게 넘지 않는다.
- [ ] 조연/빌런의 목적이 편의상 바뀌지 않았다.
- [ ] 새 인물은 `cast_registry.json`에 기록된다.

### 패턴 반복

- [ ] 최근 회차와 같은 전개/보상/cliffhanger가 과도하게 반복되지 않는다.
- [ ] 반복 경고가 있으면 변주 계획을 review 또는 revision_note에 기록한다.

### 적대 세력 단계 오류

- [ ] opposition_ladder의 현재 단계보다 적대 압박이 갑자기 과도해지지 않는다.
- [ ] 상위 적대자나 압박은 선행 단서와 unlock 조건을 가진다.

### 복선 누락 또는 모순

- [ ] 활성 복선이 `foreshadowing_ledger.json`과 맞다.
- [ ] 회수된 복선은 상태를 갱신할 계획이 있다.
- [ ] 새 복선은 회수 예정 또는 기능이 있다.

### 공간 설정 충돌

- [ ] 장소 구조와 거리감이 기존 설정과 맞다.
- [ ] 폐쇄된 장소, 금지 구역, 이동 제한이 갑자기 무시되지 않는다.
- [ ] 새 공간 설정은 canon 반영 필요 여부를 점검했다.

## final 저장 금지 조건

다음 중 하나라도 발견되면 final로 저장하지 않습니다.

- 능력 규칙 위반
- 갑작스러운 파워업
- canon 충돌
- 시간선 오류
- 인물 성격 붕괴
- 공간 설정 충돌
- 등장인물 과다 또는 역할 중복으로 회차 초점 붕괴
- 복선 누락 또는 모순
- 반복 패턴으로 독자 보상 약화
- 적대 세력의 단계적 확장 오류
- content/platform/real entity/sensitivity risk 미해결
- 사용자 승인 없는 canon 변경 필요

## 문제 발생 시 처리

1. final 저장을 중단한다.
2. 문제 항목과 관련 파일을 기록한다.
3. `halt_reason_code`를 작성한다.
4. `recovery_plan` 또는 `canon_change_request`를 작성한다.
5. 사용자 지시 전에는 확정 반영하지 않는다.
