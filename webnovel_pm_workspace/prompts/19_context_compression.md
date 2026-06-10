# 19_context_compression

## 사용 목적

rolling_context.md가 지나치게 커지거나 arc가 완료되었을 때 컨텍스트를 계층적으로 압축하는 작업입니다. 장기 연재에서 설정 drift의 가장 큰 원인인 메모리 비대화를 해소합니다.

---

## 이 프롬프트를 실행해야 하는 조건 (Trigger Conditions)

다음 중 하나라도 해당하면 원고 작성 전에 먼저 이 프롬프트를 실행한다.

- [ ] arc가 완료되었다 **(필수)**
- [ ] rolling_context.md가 15,000자를 초과했다 **(소프트 필수)**
- [ ] 마지막 압축 이후 2개 이상의 arc가 경과했다 **(강제)**
- [ ] 오랜 공백 후 새 세션이 시작되었다 **(권장)**

---

## 실행 전 확인 파일

이 프롬프트 실행 전 다음 파일을 반드시 확인한다.

- [ ] `rolling_context.md` (현재 컨텍스트 전문)
- [ ] `arc_state.json` (arc 번호, 에피소드 범위)
- [ ] `foreshadowing_ledger.json` (미회수 복선 현황)
- [ ] `arc_canon_snapshot` 이전 파일 (있다면)
- [ ] `context_compression_log.md` (이전 압축 이력)

---

## 실행 단계 (Step-by-Step)

### 단계 1 — arc_XXX_summary.md 작성

현재 rolling_context.md에서 완료된 arc의 내용을 추출해 아래 형식으로 요약 파일을 작성한다.

**파일명**: `projects/{{project_id}}/arc_{{arc_id}}_summary.md`

**포함 내용**:
1. arc 기간: EP{{시작}} ~ EP{{종료}}
2. arc 핵심 사건 (3~5개)
3. 주인공 상태 변화: arc 시작 상태 → arc 종료 상태
4. 이번 arc에서 확정된 주요 canon (3~5개)
5. 회수된 복선 목록
6. arc 종료 시 열린 질문 (다음 arc로 넘어간 미해결 사안)
7. 관련 스냅샷 참조: `arc_{{arc_id}}_canon_snapshot.json`

**분량**: 400~600자 이내. 과도한 상세 금지. 핵심만 압축.

---

### 단계 2 — arc_canon_snapshot.json 작성

`arc_canon_snapshot_template.json` 기준으로 arc 종료 시점의 clean-state 스냅샷을 작성한다.

**파일명**: `projects/{{project_id}}/arc_{{arc_id}}_canon_snapshot.json`

**필수 포함 항목**:
- `snapshot_id`, `arc_id`, `snapshot_episode`, `created_date`
- `world_state`: 세계 상태 요약
- `protagonist_state`: 주인공 현재 능력/감정/관계
- `active_characters`: 활성 named character 전체 목록
- `confirmed_canon_summary`: 이번 arc에서 확정된 canon
- `changed_from_previous_snapshot`: 이전 스냅샷 대비 변경사항
- `foreshadowing_state`: 미회수 복선 현황
- `this_snapshot_is_ground_truth_for_arcs_after`: true

**작성 후**:
- [ ] verification_checklist의 각 항목을 확인한다
- [ ] 특히 ability_state가 ability_rules.json과 일치하는지 확인

---

### 단계 3 — arc_state.json 업데이트

- 완료된 arc의 상태를 `completed`로 변경
- 다음 arc 기본 정보 추가
- `last_completed_arc`, `current_arc`, `next_arc_start_episode` 갱신

---

### 단계 4 — rolling_context.md 재구성

기존 rolling_context.md를 다음 구조로 전면 재작성한다.

```markdown
## 시리즈 전체 요약
[전체 이야기를 3문장 이내로 초압축. arc 요약을 나열하지 말 것.]

## 완료된 arc 목록
- ARC001: [1줄 핵심 요약] → arc_001_summary.md
- ARC002: [1줄 핵심 요약] → arc_002_summary.md
(완료된 arc 추가)

## 현재 arc: ARC{{N}} (EP{{시작}} ~ 진행 중)
[현재 arc의 화별 상세 요약]
[포함 항목: 각 화 사건, 감정선, 결정, 결과]

## 주요 인물 현재 상태
### {{주인공명}}
- 현재 능력 단계: {{tier}}
- 현재 감정/심리 상태: {{요약}}
- 현재 위치: {{}}
- 핵심 관계 변화: {{}}

### {{조연명}}
- 현재 상태: {{}}

## 활성 갈등
1. {{갈등 1: 설명 + 현재 상태}}
2. {{갈등 2}}

## Critical 미회수 복선 (critical 등급만)
- {{복선 ID}}: {{복선 내용}} (EP{{심은 화}}, 예상 회수 구간: {{}})

## 직전 화 요약 및 다음 화 유지 정보
- 직전 화: EP{{N}} 요약
- 현재 감정선: {{}}
- 다음 화에서 반드시 이어야 할 것: {{}}
```

**중요**: 이전 arc의 화별 상세 내용은 이 파일에서 제거. arc_summary 파일로 이미 이동됨.

---

### 단계 5 — 압축 검증 (Spot-Check)

압축 전 rolling_context에서 랜덤으로 3개 이상의 canon 사실을 선택해 압축 후에도 접근 가능한지 확인한다.

| 확인 사실 | 압축 전 출처 | 압축 후 접근 경로 | 확인 |
|---|---|---|---|
| {{canon 사실 1}} | rolling_context EP{{N}} | {{Tier 4 파일 또는 arc_summary}} | ☐ |
| {{canon 사실 2}} | rolling_context EP{{N}} | {{}} | ☐ |
| {{canon 사실 3}} | rolling_context EP{{N}} | {{}} | ☐ |

**모든 사실이 접근 가능해야 통과**. 접근 불가 사실이 있으면 arc_summary 또는 Tier 4 파일에 보완 후 재확인.

---

### 단계 6 — context_compression_log.md 업데이트

`context_compression_log.md`의 압축 이력 표에 새 행을 추가한다.

| compression_id | triggered_at_episode | arc_compressed | what_was_preserved | what_was_summarized | what_was_dropped | compressed_by | verified_by |
|---|---|---|---|---|---|---|---|
| COMP{{N}} | EP{{N}} | ARC{{N}} | [보존된 내용] | [arc_summary로 이동된 내용] | [삭제된 내용] | AI | ☐ 미확인 |

---

## 실행 후 체크리스트

- [ ] `arc_{{arc_id}}_summary.md` 생성 완료
- [ ] `arc_{{arc_id}}_canon_snapshot.json` 생성 완료
- [ ] `arc_state.json` 업데이트 완료
- [ ] `rolling_context.md` 재구성 완료 (이전 arc 상세 제거 확인)
- [ ] 압축 후 rolling_context.md 크기가 15,000자 이하인지 확인
- [ ] Spot-check 3개 이상 통과
- [ ] `context_compression_log.md` 업데이트 완료
- [ ] 사용자에게 압축 완료 보고

---

## 보고 형식

```
[CONTEXT_COMPRESSION — EP{{N}}]

압축 트리거: {{arc 종료 / 15,000자 초과 / 세션 재시작}}
압축된 arc: ARC{{N}} (EP{{시작}} ~ EP{{종료}})

생성 파일:
- arc_{{arc_id}}_summary.md
- arc_{{arc_id}}_canon_snapshot.json

rolling_context.md:
- 압축 전 크기: 약 {{N}}자
- 압축 후 크기: 약 {{N}}자

Spot-check: {{N}}개 canon 사실 모두 접근 가능 확인

다음 작업 가능:
- 새 arc 시작 또는 현재 arc 계속 작성 가능
- 다음 회차 outline 전 approval_state 확인 필요
```

---

## 관련 harness

- `CONTEXT_COMPRESSION_HARNESS.md` (전체 프로토콜 기준)
- `LONGFORM_HARNESS.md` (arc 종료 게이트)
- `THEMATIC_HARNESS.md` (arc 종료 시 함께 실행)
- `PACING_HARNESS.md` (arc 종료 시 함께 실행)
- `VOICE_DRIFT_HARNESS.md` (arc 종료 시 함께 실행)
