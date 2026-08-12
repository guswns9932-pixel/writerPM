# CONTEXT_COMPRESSION_HARNESS

수백 화에 걸친 장기 연재에서 rolling_context.md를 계층적으로 관리해 AI가 항상 적절한 메모리를 유지하도록 하는 harness입니다.

---

## 목적

세션마다 AI가 이전 수백 화의 원고 전체를 컨텍스트 창에 올리는 것은 불가능합니다. 이 harness는 그 한계를 체계적으로 극복하기 위한 계층적 메모리 구조와 압축 프로토콜을 정의합니다.

- rolling_context.md가 무한히 커지는 것을 방지한다
- arc 경계마다 깨끗한 상태 스냅샷을 보존한다
- 세션 재시작 시 반드시 읽어야 할 파일의 순서를 명확히 한다
- 설정 drift의 가장 큰 원인인 메모리 부실을 구조적으로 차단한다

---

## 계층적 메모리 구조 (Tiered Memory)

### Tier 1 — Hot (rolling_context.md)

**무엇을 담는가**: 현재 arc의 화별 상세 요약 + 주요 인물 현재 상태 + 활성 갈등 + critical 미회수 복선

**최대 권장 크기**: 15,000자 (약 30화 분량 상세 내용)

**포함 항목**:
1. 시리즈 전체 요약 (3문장. arc 요약을 대체하지 않는 초압축)
2. 완료된 arc 목록 (arc_id + 1줄 요약 + arc_summary 파일 경로)
3. 현재 arc 화별 상세 요약
4. 주요 인물 현재 상태 (능력, 감정, 관계, 위치)
5. 활성 갈등 목록
6. critical 미회수 복선 (critical 등급만)
7. 직전 화 감정선 및 다음 화 유지 정보

**포함하지 않는 항목**:
- 완료된 arc의 화별 상세 내용
- 해소된 갈등
- 회수 완료된 복선
- 삭제/dormant 인물의 상세 히스토리

---

### Tier 2 — Warm (arc_XXX_summary.md)

**무엇을 담는가**: 완료된 arc 하나당 하나의 파일. arc 전체의 핵심만 약 500자 이내로.

**포함 항목**:
1. arc 기간과 에피소드 범위
2. arc 핵심 사건 (3~5개)
3. 주인공 상태 변화 (arc 시작 → arc 종료)
4. 확정된 주요 canon (3~5개)
5. 회수된 복선
6. arc 종료 시 열린 질문 (다음 arc로 넘어간 것)
7. 관련 스냅샷 파일 참조: `arc_XXX_canon_snapshot.json`

**읽는 시점**: Cold Start 시 전부 읽지 않고 필요 시 참조. rolling_context.md의 1줄 요약에서 파일 경로로 접근.

---

### Tier 3 — Cold (개별 화 원고 아카이브)

**무엇을 담는가**: 각 화의 실제 원고 파일

**읽는 시점**: 세밀한 검수, 표현 재확인, 독자 경험 deep-dive 시에만. 평소 세션에서는 로딩 금지.

---

### Tier 4 — Permanent (항상 신선하게 읽는 파일)

세션 시작 시 반드시 읽는 파일. 압축 대상이 아님. 항상 최신본을 읽어야 한다.

| 파일 | 이유 |
|---|---|
| `AGENTS.md` | 절대 규칙 확인 |
| `story_bible.json` | 세계관 전제와 장르 약속 |
| `character_bible.json` | 인물 성격, 욕망, 결핍 |
| `ability_rules.json` | 능력 규칙 위반 방지 |
| `thematic_compass.json` | 주제 나침반 |
| `arc_canon_snapshot` (최신본) | arc 경계 이후의 ground-truth |
| `rolling_context.md` | 현재 컨텍스트 |
| `approval_state.json` | 승인 상태 확인 |
| `final_registry.json` | final 보호 상태 확인 |

---

## 압축 트리거 조건

다음 중 하나에 해당하면 원고 작성 전 압축을 먼저 실행한다.

| 트리거 | 유형 | 설명 |
|---|---|---|
| arc 종료 | **필수** | arc가 완료될 때마다 의무 실행 |
| rolling_context.md 15,000자 초과 | **소프트 트리거** | 초과 시 즉시 또는 현재 arc 종료 전에 실행 |
| 세션 gap 후 재시작 | **권장** | 오랜 공백 후 새 세션 시작 시 점검 및 필요 시 실행 |
| 2개 arc 이상 미압축 | **강제** | 원고 작성 전 압축 완료 필수. 미이행 시 halt |

---

## 압축 프로토콜 (단계별)

arc 종료 시 또는 소프트 트리거 발생 시 아래 순서대로 실행한다.

### 1단계 — 현재 rolling_context.md 저장

1. 현재 rolling_context.md 전체를 `arc_XXX_summary.md` 형식으로 저장한다.
   - 파일명: `projects/{{project_id}}/arc_{{arc_id}}_summary.md`
   - 내용: arc 핵심 사건 3~5개, 주인공 상태 변화, 주요 canon, 회수 복선, 열린 질문, 스냅샷 파일 참조
   - 분량: 약 400~600자

2. 저장 전 체크:
   - [ ] arc 번호가 정확한가?
   - [ ] arc의 핵심 사건이 누락 없이 포함되었는가?
   - [ ] 열린 질문(다음 arc로 넘어가는 것)이 명확히 기록되었는가?

### 2단계 — arc_canon_snapshot 작성

`arc_canon_snapshot_template.json` 기준으로 이 arc의 종료 시점 상태 스냅샷을 작성한다.

- 파일명: `projects/{{project_id}}/arc_{{arc_id}}_canon_snapshot.json`
- 포함 항목: world_state, protagonist_state, active_characters, confirmed_canon, changed_from_previous_snapshot, foreshadowing_state, ability_state, emotional_promise_state, pacing_state, thematic_state

### 3단계 — arc_state.json 업데이트

- 현재 arc를 completed로 변경
- 다음 arc 정보 추가
- next_arc_start_episode 기록

### 4단계 — rolling_context.md 재구성

기존 rolling_context.md를 다음 구조로 새로 작성한다:

```
## 시리즈 전체 요약 (3문장)
[전체 이야기를 3문장 이내로 초압축]

## 완료된 arc 목록
- ARC001: [1줄 요약] → arc_001_summary.md 참조
- ARC002: [1줄 요약] → arc_002_summary.md 참조
...

## 현재 arc: ARC{{N}}
[현재 arc의 화별 상세 요약]

## 주요 인물 현재 상태
[인물별 현재 능력/감정/위치/관계]

## 활성 갈등
[현재 진행 중인 갈등]

## Critical 미회수 복선
[critical 등급 복선만]

## 직전 화 요약 및 다음 화 유지 정보
[직전 화 감정선, 다음 화에 반드시 유지해야 할 정보]
```

### 5단계 — 압축 검증 (Spot-check)

랜덤으로 3개 이상의 canon 사실을 선택해 압축 후 컨텍스트에서 여전히 접근 가능한지 확인한다.

- [ ] canon 사실 1: {{사실}} → 접근 경로: {{Tier 4 파일 또는 arc_summary}}
- [ ] canon 사실 2: {{사실}} → 접근 경로: {{}}
- [ ] canon 사실 3: {{사실}} → 접근 경로: {{}}

모든 사실이 접근 가능하면 통과. 접근 불가한 사실이 있으면 arc_summary 또는 Tier 4 파일에 추가 후 재확인.

### 6단계 — 압축 이력 기록

`context_compression_log.md`에 아래 항목을 추가한다:

| compression_id | triggered_at_episode | arc_compressed | what_was_preserved | what_was_summarized | what_was_dropped | compressed_by | verified_by |
|---|---|---|---|---|---|---|---|
| COMP{{N}} | EP{{N}} | ARC{{N}} | [보존 목록] | [요약 이동 목록] | [삭제 목록] | AI | ☐ 미확인 |

---

## Cold Start 프로토콜 (세션 재시작 시 필독 순서)

세션에 이전 기억이 없는 상태에서 시작할 때 반드시 아래 순서대로 읽는다.

**이 순서를 건너뛰면 설정 drift 위험이 급증한다.**

```
1단계 — 규칙 확인
  ① AGENTS.md

2단계 — 세계관 기반
  ② story_bible.json
  ③ character_bible.json
  ④ ability_rules.json

3단계 — 주제 나침반
  ⑤ thematic_compass.json

4단계 — 현재 상태 확인
  ⑥ arc_canon_snapshot (가장 최근 파일)
  ⑦ rolling_context.md

5단계 — 작업 범위 확인
  ⑧ approval_state.json
  ⑨ final_registry.json
```

### Cold Start 후 검증 체크리스트

- [ ] 현재 arc와 화수를 정확히 파악했는가?
- [ ] 주인공 현재 능력 단계가 ability_rules와 일치하는가?
- [ ] 직전 화 감정선이 파악되었는가?
- [ ] 승인된 작업 범위를 확인했는가?
- [ ] final 보호 상태를 확인했는가?
- [ ] 미회수 critical 복선을 파악했는가?
- [ ] emotional_promise_ledger의 high-investment 약속 현황을 파악했는가?

위 체크리스트를 통과하지 못하면 원고 작성을 시작하지 않는다.

---

## 경고 조건 (압축이 지연되고 있다는 신호)

다음 중 하나에 해당하면 즉시 사용자에게 보고하고 압축을 권고한다.

- rolling_context.md가 15,000자를 초과했다
- rolling_context.md에 완료된 arc의 화별 상세 내용이 아직 포함되어 있다
- 마지막 arc 이후 2개 이상의 arc가 지나도록 arc_summary 파일이 없다
- arc_canon_snapshot의 최신 파일이 현재 arc보다 2개 이상 오래되었다
- 세션 재시작 후 Cold Start 프로토콜 없이 바로 원고 작성을 요청받았다

---

## 관련 파일

- `rolling_context.md` (Tier 1)
- `arc_XXX_summary.md` (Tier 2)
- `arc_XXX_canon_snapshot.json` (arc별 clean-state)
- `context_compression_log.md` (압축 이력)
- `arc_state.json` (arc 상태)

---

## 중단 조건

압축 없이 원고 작성을 진행하면 안 되는 경우:

- rolling_context.md가 2개 arc 이상 미압축 상태
- Cold Start 프로토콜 미실행 상태에서 원고 작성 요청
- arc_canon_snapshot이 없는 상태에서 arc 경계를 넘어 작성 요청

발생 시: `halt_reason_code: CONTEXT_COMPRESSION_OVERDUE` 기록 후 압축 완료 전 작성 금지.
