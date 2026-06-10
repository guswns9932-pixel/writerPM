# LONGFORM_HARNESS

1화부터 완결까지 장기 연재를 진행할 때 설정 흔들림, 복선 누락, 보상 약화, AI식 반복 패턴을 줄이기 위한 문서형 harness입니다.

## 목적

- 완결 목표 기준 장기 구조 유지
- 3화 배치 누적에 따른 설정 drift 방지
- 10화 단위 audit 고정
- arc별 목표와 보상 유지
- 복선 회수 누락 방지
- 후반부 급전개와 즉석 canon 변경 방지

## 장기 계획 파일

프로젝트가 20화 이상 목표라면 다음 파일 또는 해당 역할의 문서를 유지하는 것을 권장합니다.

- `arc_state.json`
- `timeline.json`
- `foreshadowing_ledger.json`
- `canon_log.json`
- `rolling_context.md`
- `roadmap_20.md`
- `roadmap_80.md` 또는 전체 회차 목표에 맞춘 장기 roadmap
- `open_threads_register.json` 또는 미해결 갈등 목록
- `payoff_schedule.json` 또는 복선 회수 계획

## 3화 배치 운영 규칙

각 3화 배치마다 다음 순서를 지킵니다.

1. memory check
2. cast pressure check
3. continuity check
4. batch outline
5. episode outline
6. v1 draft
7. review
8. revision_note
9. v2 final candidate
10. canon/timeline/foreshadowing/rolling_context 업데이트
11. episode_status 업데이트
12. run_report 작성
13. `awaiting_user_review`로 정리

## 10화 단위 audit 규칙

매 10화 완료 또는 arc 종료 시 다음 audit을 작성합니다.

- `continuity_audit_XXX.md`
- `cast_audit_XXX.md`
- `foreshadowing_audit_XXX.md`
- `quality_trend_audit_XXX.md`
- 필요 시 `recovery_plan_XXX.md`

## arc gate

### arc 시작 전

- [ ] arc 목표가 명확하다.
- [ ] 주인공 상태 변화의 시작점과 끝점이 있다.
- [ ] 핵심 독자 보상 3개 이상이 있다.
- [ ] 새 인물/조직/장소 추가 계획이 통제되어 있다.
- [ ] 회수할 복선과 새로 심을 복선이 구분되어 있다.

### arc 종료 후

- [ ] 주인공이 실제로 선택 또는 성장했다.
- [ ] 독자 보상이 최소 1개 이상 명확히 회수되었다.
- [ ] 미회수 복선이 ledger에 남아 있다.
- [ ] 더 이상 active가 아닌 인물을 dormant/removed/merged로 정리했다.
- [ ] 다음 arc로 넘길 질문이 1~3개로 압축되었다.

## 반복 패턴 방지

다음 패턴이 2회 이상 반복되면 review에 기록하고 변주 계획을 세웁니다.

- 추격으로 시작해 도주로 끝나는 회차
- 새 정보 브로커가 정보를 던지고 사라지는 회차
- 주인공이 능력 과부하로만 위기를 넘기는 회차
- 조직이 강하다고만 말하고 실질 보상이 없는 회차
- 클리프행어가 이름/파일/좌표 공개만 반복되는 회차

## final arc lock

마지막 20~25% 구간에 들어가면 다음을 잠급니다.

- 신규 핵심 인물 추가 금지
- 신규 핵심 능력 추가 금지
- 신규 장기 복선 추가 금지
- 기존 복선 회수 우선
- 주인공 최종 선택과 대가 유지
- canon_change_request 없이 결말 구조 변경 금지

## 중단 조건

다음 중 하나라도 발생하면 장기 진행을 멈추고 audit 또는 recovery_plan을 작성합니다.

- 10화 이상 복선이 쌓였지만 회수 계획이 없다.
- active cast가 arc 상한을 계속 초과한다.
- 주인공 목표가 2개 배치 이상 불명확하다.
- 같은 유형의 회차 보상이 3회 이상 반복된다.
- 후반부에 신규 canon이 결말 해결용으로 갑자기 필요해진다.

## 보고 항목

장기 배치 또는 audit 후 보고에 다음을 포함합니다.

- 현재 회차 범위
- 현재 arc
- active cast 수
- 신규 named character 수
- 열린 복선 수
- 회수된 복선 수
- 독자 보상 유형
- 다음 audit 예정 시점
