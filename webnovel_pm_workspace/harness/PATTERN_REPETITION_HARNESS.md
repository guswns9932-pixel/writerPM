# PATTERN_REPETITION_HARNESS

AI 작성 시 발생하기 쉬운 반복 전개, 반복 보상, 반복 클리프행어를 방지하기 위한 문서형 harness입니다.

## 목적

- 회차 전개 패턴 반복 방지
- 추격/도주/파일 발견/정체 공개형 cliffhanger 남발 방지
- 독자 보상 유형 다양화
- 장면 구조와 갈등 방식의 변주 유지

## 필수 확인 파일

- `episode_pattern_log.json`
- `rolling_context.md`
- `arc_state.json`
- `foreshadowing_ledger.json`
- `quality_review` 또는 `QUALITY_HARNESS.md` 기준 검수 기록

## 패턴 기록 항목

각 회차 후 `episode_pattern_log.json`에 다음을 기록합니다.

- opening_pattern
- main_conflict_pattern
- reward_type
- cliffhanger_type
- protagonist_choice_type
- antagonist_pressure_type
- variation_note

## 반복 경고 기준

- 같은 opening pattern이 2회 연속 반복되면 warning을 기록한다.
- 같은 cliffhanger type이 2회 연속 반복되면 변주 계획을 세운다.
- 같은 독자 보상 유형이 3회 이상 반복되면 다음 회차에서 다른 보상 유형을 우선한다.
- 추격/도주 패턴이 반복되면 정보전, 협상, 함정 설계, 잠입, 역추적 중 하나로 변주한다.

## final 저장 전 점검

- [ ] 직전 3화와 opening pattern이 지나치게 유사하지 않다.
- [ ] 직전 3화와 cliffhanger type이 지나치게 유사하지 않다.
- [ ] 독자 보상이 새로운 정보, 감정, 승리, 반전, 성장 중 최소 하나를 제공한다.
- [ ] 주인공 선택 방식이 매번 도주 또는 회피만 반복되지 않는다.
- [ ] 적대 압박 방식이 단순 추격만 반복되지 않는다.

## 중단 조건

- 같은 회차 구조가 3회 이상 반복되어 독자 보상이 약화된다.
- cliffhanger가 이름/파일/좌표 공개만 반복된다.
- 주인공이 2개 배치 이상 능동적 선택 없이 반응만 한다.
- 반복 패턴 경고가 있는데 revision_note 없이 final 저장하려 한다.

## 보고 항목

- 직전 3화 패턴 요약
- 이번 회차 패턴
- 반복 경고 여부
- 다음 회차 변주 계획
- episode_pattern_log 업데이트 여부
