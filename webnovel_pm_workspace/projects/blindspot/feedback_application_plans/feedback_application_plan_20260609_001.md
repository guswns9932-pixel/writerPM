# Feedback Application Plan - 20260609_001

## 기본 정보

- plan_id: feedback_plan_20260609_001
- feedback_id: feedback_20260609_001
- project_id: blindspot
- target_episode: episode_001
- target_current_final: `webnovel_pm_workspace/projects/blindspot/episodes/episode_001_final_v2.md`
- status: pending_user_approval
- created_at: 2026-06-09

## 1. 사용자 피드백 원문

> 1화는 좋은데 주인공 말투가 조금 가볍다.
> 더 건조하고 짧은 말투로 바꾸고 싶다.
>
> 바로 수정하지 말고 먼저 feedback_application_plan을 작성해줘.

## 2. Codex가 해석한 의미

- 사용자는 1화의 전체 구성, 사건, 후킹 자체는 유지해도 된다고 판단한 것으로 해석한다.
- 핵심 요청은 주인공 한서진의 대사와 내면 서술 톤을 더 건조하고 짧게 조정하는 것이다.
- “가볍다”는 표현은 다음 요소를 줄이라는 의미로 해석한다.
  - 감정 설명이 길어지는 문장
  - 농담처럼 읽힐 수 있는 자기반응
  - 과하게 설명적인 내면 독백
  - 긴 호흡의 회상성 문장
- “더 건조하고 짧은 말투”는 다음 방향으로 해석한다.
  - 대사는 짧고 단호하게 유지
  - 내면 독백은 판단 중심으로 압축
  - 감정은 직접 설명보다 신체 반응과 행동으로 처리
  - 주인공이 스스로를 과하게 해설하지 않게 조정

## 3. 반영 대상 파일

### 직접 수정 대상 후보

- `webnovel_pm_workspace/projects/blindspot/episodes/episode_001_final_v2.md`

### 새로 생성할 수정본 후보

- `webnovel_pm_workspace/projects/blindspot/episodes/episode_001_final_v3.md`
- `webnovel_pm_workspace/projects/blindspot/episodes/episode_001_revision_note_v3.md`
- `webnovel_pm_workspace/projects/blindspot/episodes/episode_001_style_check_v3.md` 또는 기존 style check 보강본

### 상태 갱신 후보

- `webnovel_pm_workspace/projects/blindspot/episodes/episode_001_status.md`
- `webnovel_pm_workspace/projects/blindspot/rolling_context.md`
- `webnovel_pm_workspace/projects/blindspot/run_reports/run_report_20260609_002.md`

## 4. 수정 범위

- 분류: `TEXT_ONLY`, `STYLE_ADJUSTMENT`
- 회차 구조 변경: 없음
- 장면 순서 변경: 없음
- 사건 결과 변경: 없음
- canon 변경: 없음
- 능력 규칙 변경: 없음
- 복선 변경: 없음
- 주요 수정 범위:
  - 한서진의 직접 대사
  - 한서진의 내면 독백 중 길거나 감정 설명이 많은 문장
  - “능력”을 받아들이는 자기반응 문단
  - 큰길 대신 사각지대를 선택하는 후반부 판단 문장

## 5. canon 변경 필요 여부

- canon 변경 필요 여부: 없음
- 이유:
  - 주인공의 성격 핵심은 이미 `character_bible.json`에서 “짧고 긴장감 있는 내면 독백. 대사는 필요한 만큼만 한다”로 설정되어 있다.
  - `style_guide.json`에도 한서진의 말투가 “말수는 적지만 선택 순간에는 단호하다”로 설정되어 있어, 이번 피드백은 기존 canon과 충돌하지 않고 오히려 강화한다.
- `canon_change_request` 작성 필요: 없음

## 6. 영향받는 회차

- 직접 영향:
  - `episode_001`
- 간접 영향:
  - 이후 회차의 한서진 대사/내면 서술 톤 기준
- 2화 이후 본문 영향:
  - 현재는 2화 이후 본문을 작성하지 않는다.
  - 1화 승인 후 2~4화 배치를 진행할 때 한서진 말투 기준으로 반영 가능하다.

## 7. 바로 적용 가능한지 여부

- 현재 요청에서 바로 적용: 아니오
- 이유:
  - 사용자가 “바로 수정하지 말고 먼저 feedback_application_plan을 작성”하라고 명시했다.
- 기술적 적용 가능성: 가능
- 적용 조건:
  - 사용자가 “이 계획대로 반영해줘” 또는 “바로 반영”이라고 명시해야 한다.
  - 기존 `episode_001_final_v2.md`는 덮어쓰지 않는다.
  - 수정본은 `episode_001_final_v3.md`로 새로 저장한다.

## 8. 추천 적용 방식

1. `episode_001_final_v2.md`를 기준으로 본문 구조와 사건은 유지한다.
2. 한서진의 말투와 내면 독백만 건조하고 짧게 조정한다.
3. 다음 유형의 문장을 우선 수정한다.
   - 감정 설명이 긴 문장
   - 회상이나 자기해석이 길어지는 문장
   - 위기 중 주인공의 판단을 늦추는 문장
4. 수정 후 `episode_001_final_v3.md`로 저장한다.
5. `episode_001_revision_note_v3.md`에 다음을 기록한다.
   - 반영한 문체 조정 원칙
   - 변경하지 않은 사건/설정
   - canon 변경 없음
6. `episode_001_status.md`의 `current_final`은 사용자 승인 전에는 `episode_001_final_v3.md` 후보로만 갱신하고, 승인 상태는 `pending`으로 유지한다.
7. 수정 후 style check와 짧은 quality re-check를 수행한다.

## 적용 예시 방향

### 현재 톤 예시

- “능력이라기엔 너무 아팠다. 너무 늦게 알려줬고, 너무 불친절했다.”

### 수정 방향 예시

- “능력이라 부르기엔 아팠다. 늦었고, 불친절했다.”

### 현재 톤 예시

- “처음으로 그는 숨기 위해서가 아니라, 선택하기 위해 사각지대로 들어갔다.”

### 수정 방향 예시

- “숨는 게 아니었다. 선택이었다.”

## 사용자 승인 필요 사항

- 위 방식으로 `episode_001_final_v3.md`를 생성해도 되는지 확인 필요.
- 승인 전에는 1화 본문을 수정하지 않는다.
