# THEMATIC_HARNESS

수백 화에 걸쳐 이야기의 핵심 주제와 감정적 약속이 흔들리지 않도록 점검하는 harness입니다.

---

## 목적

개별 회차 품질 점검(QUALITY_HARNESS)은 단편적 오류를 잡지만, 수십 개 arc에 걸쳐 이야기가 무엇을 말하려는지가 서서히 달라지는 주제 drift는 포착하지 못합니다.

이 harness는 다음 세 가지를 정기적으로 점검합니다:
1. **주제 나침반 점검**: 이 arc/회차가 core_theme을 탐색하고 있는가, 아니면 배신하고 있는가?
2. **감정적 약속 점검**: 독자와의 감정 계약(emotional_promise_ledger)이 방치되고 있지 않은가?
3. **anti-theme 점검**: 이야기가 피해야 할 방향으로 수렴하고 있지 않은가?

---

## 실행 트리거

| 트리거 | 유형 | 설명 |
|---|---|---|
| arc 종료 시 | **필수** | arc 종료 후 다음 arc 시작 전에 실행 |
| 10화 단위 audit | **필수** | LONGFORM_HARNESS의 10화 audit에 포함. 미실행 시 audit 완료로 보고하지 않음 |
| 주제 점검이 불확실하게 느껴질 때 | **즉시** | 작업자 또는 사용자가 "이 방향이 맞는지 모르겠다"고 느낄 때 |
| 주인공이 2개 arc 이상 성장 없이 유사한 상황을 반복할 때 | **즉시** | 주제 희석 위험 신호 |

---

## 중요한 구분: 일시적 전복 vs. 주제 drift

**이것은 drift가 아니다**:
- 특정 회차에서 anti-theme처럼 보이는 사건이 발생함 (예: 주인공이 대가 없이 승리함)
- 하나의 arc에서 core_theme이 직접 탐색되지 않음
- 독자가 일시적으로 불쾌하거나 희망을 잃게 만드는 장면

**이것이 drift다**:
- 3개 이상의 arc에 걸쳐 anti-theme 방향이 지속됨
- thematic_questions 중 어느 것도 2개 arc 이상 탐색되지 않음
- emotional_promise가 10화 이상 진전 없이 방치됨
- 독자가 "이 이야기는 결국 아무것도 말하지 않는다"고 느낄 법한 흐름이 형성됨

---

## 점검 1 — 주제 나침반 점검

`thematic_compass.json`을 열고 다음 질문에 답한다.

### 1-A. Core Theme 탐색 여부

```
이번 arc/10화 구간에서 core_theme이 탐색된 장면 또는 선택이 최소 1개 있었는가?
```

- [ ] **있음** — 어떤 장면 또는 선택인가? (간략히 기록)
- [ ] **없음** — 다음 arc/구간에서 보완 계획 필요

### 1-B. Symbolic Motifs 등장 여부

```
symbolic_motifs 목록 중 최소 1개가 이번 구간에서 자연스럽게 등장했는가?
```

- [ ] **있음**
- [ ] **없음** — 3개 arc 이상 연속으로 없으면 주제 단절 경고. thematic_correction_note 작성.

### 1-C. Thematic Questions 연결 여부

```
thematic_questions 중 최소 1개가 이번 구간의 전개와 연결되는가?
```

- [ ] **있음**
- [ ] **없음** — 허용. 단 2개 arc 이상 연속으로 없으면 경고.

### 1-D. Emotional Center 유지 여부

```
이번 구간을 읽은 독자가 emotional_center에 기술된 감각을 느낄 수 있는가?
```

- [ ] **있음**
- [ ] **없음** — 긴급 점검. anti-theme 감지 여부 확인.

---

## 점검 2 — 감정적 약속 점검 (Emotional Promise)

`emotional_promise_ledger.json`을 열고 다음을 확인한다.

### 2-A. High-Investment 약속 방치 여부

```
reader_investment_level: "high"인 약속 중
last_progressed_episode가 현재 화수보다 10화 이상 오래된 것이 있는가?
```

- [ ] **없음** — 정상
- [ ] **있음** — 해당 약속의 `next_milestone_plan`을 작성하고 다음 배치에서 진전 확보

### 2-B. approaching_payoff 상태 약속의 실행 계획 여부

```
current_status: "approaching_payoff"인 약속이 있는가?
있다면 구체적 payoff 계획이 준비되어 있는가?
```

- [ ] **해당 약속 없음**
- [ ] **있음 + 계획 있음** — 정상
- [ ] **있음 + 계획 없음** — payoff 계획을 다음 arc 계획에 반드시 포함

### 2-C. 조용한 파기 여부 (Silent Break)

```
delivered나 broken으로 기록되지 않았는데, 사실상 이 약속이 더 이상 실현되기 어려운 방향으로 전개가 진행되고 있지 않은가?
```

- [ ] **없음** — 정상
- [ ] **의심됨** — 사용자에게 보고 후 deliberate_subversion 처리 또는 방향 수정

---

## 점검 3 — Anti-Theme 점검

`thematic_compass.json`의 `anti_themes`와 `theme_drift_warnings`를 확인한다.

### 3-A. Anti-Theme 수렴 여부

각 anti_theme에 대해:

```
이번 arc/구간에서 이 anti_theme 방향으로 전개가 수렴하는 흐름이 있었는가?
```

| anti_theme | 수렴 여부 | 근거 |
|---|---|---|
| {{AT001 label}} | 없음 / 주의 / 경고 | {{근거}} |
| {{AT002 label}} | 없음 / 주의 / 경고 | {{근거}} |

### 3-B. Theme Drift Warning 신호 확인

`theme_drift_warnings`의 각 신호를 확인한다.

| 경고 ID | 신호 | 해당 여부 | 조치 |
|---|---|---|---|
| TDW001 | 주인공이 대가 없이 3화 이상 연속 승리 | ☐ | THEMATIC_HARNESS 실행 + thematic_correction_note |
| TDW002 | 희망적 해소 없이 고통만 5화 이상 | ☐ | 독자 보상 계획 필수 |
| TDW003 | symbolic_motifs 3개 arc 미등장 | ☐ | 다음 arc 계획에 motif 재도입 |
| TDW004 | thematic_questions 미탐색 2개 arc 이상 | ☐ | arc 계획에 주제 연결 장면 확보 |

---

## 조치 (Corrective Action)

### 경미한 주의 (1개 항목 미충족)

- 해당 항목을 `run_report`에 기록
- 다음 arc/배치 계획에서 보완 방법 제시

### 중간 경고 (2~3개 항목 미충족)

- `thematic_correction_note` 작성
- 다음 arc 시작 전 사용자에게 보고
- 사용자 확인 전 다음 arc 진행 보류 권장

### 심각한 경고 (anti_theme 수렴 확인 또는 3개 이상 미충족)

- `thematic_correction_note` 즉시 작성
- 다음 arc 시작 전 사용자 승인 필수
- `halt_reason_code: THEMATIC_DRIFT_CRITICAL` 기록
- recovery_plan 작성

---

## thematic_correction_note 작성 형식

```
[THEMATIC_CORRECTION_NOTE — EP{{N}}]

점검 트리거: {{arc 종료 / 10화 audit / 즉시 감지}}
감지된 문제:
1. {{문제 1: 구체적으로}}
2. {{문제 2}}

분류:
- [ ] 일시적 전복 (허용)
- [ ] 주제 drift (수정 필요)

제안 조치:
- {{조치 1: 다음 arc 계획에서 할 것}}
- {{조치 2}}

사용자 확인 필요 여부: 예 / 아니요
```

---

## 보고 형식

Thematic Harness 실행 후 다음 형식으로 보고한다.

```
[THEMATIC_CHECK — EP{{N}} / ARC{{N}}]
점검 1 (주제 나침반):
  - core_theme 탐색: 있음/없음
  - symbolic_motifs 등장: 있음/없음
  - thematic_questions 연결: 있음/없음
  - emotional_center 유지: 있음/없음

점검 2 (감정적 약속):
  - high-investment 약속 방치: 있음/없음 (있으면 어떤 약속)
  - approaching_payoff 계획: 준비됨/필요
  - 조용한 파기 의심: 있음/없음

점검 3 (anti-theme):
  - anti_theme 수렴: 없음/{{AT ID}}
  - drift 경고 신호: 없음/{{TDW ID}}

종합 판정: 정상 / 주의 / 경고 / 심각
조치: {{없음 / correction_note 작성 / halt}}
```

---

## 관련 파일

- `thematic_compass.json` (주제 나침반 기준)
- `emotional_promise_ledger.json` (감정적 약속 원장)
- `LONGFORM_HARNESS.md` (10화 audit 연계)
- `PACING_HARNESS.md` (pacing과 주제 연계)
- `CONTEXT_COMPRESSION_HARNESS.md` (arc 종료 시 함께 실행)
