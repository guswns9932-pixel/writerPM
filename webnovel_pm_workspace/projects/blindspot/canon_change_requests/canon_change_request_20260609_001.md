# canon_change_request_20260609_001 - 시선 감지 핵심 판정 기준 명문화

## 요청 정보

- request_id: canon_change_request_20260609_001
- project_id: blindspot
- requested_by: User
- status: pending_user_approval
- source_context:
  - `webnovel_pm_workspace/projects/blindspot/run_reports/continuity_audit_001.md`
  - `webnovel_pm_workspace/projects/blindspot/recovery_plans/recovery_plan_20260609_001.md`
- requested_action: story_bible / ability_rules 직접 수정 없이 canon_change_request만 작성
- created_at: 2026-06-09

## 1. 변경 요청 내용

`시선 감지`의 핵심 canon에 다음 판정 기준을 명문화한다.

> 한서진의 능력은 “자신을 볼 가능성이 있는 모든 시선”을 감지하되, 감지 성립에는 `현재성`, `시야 경로`, `관측 가능성`, `감지 대가`가 필요하다. 녹화물·저장 기록·과거 영상은 현재 한서진을 보고 있지 않으므로 감지 대상이 아니다. 카메라·렌즈·거울·창문 같은 매개 시선은 실시간 관측 가능성이 있을 때만 희미하게 감지되며, 시선이 전혀 없는 물리 함정은 감지하지 못한다.

### 제안 canon 세부 항목

1. `현재성`
   - 감지 대상은 현재 한서진을 보거나 볼 가능성이 있는 시선이다.
   - 과거 녹화물, 삭제 영상, 저장 로그는 감지 대상이 아니다.
2. `시야 경로`
   - 사람 눈, 카메라 렌즈, 거울, 창문처럼 한서진에게 닿을 수 있는 관측 경로가 있어야 한다.
3. `관측 가능성`
   - 관측자가 한서진의 위치를 모르면 감지 강도는 약해진다.
   - 관측 가능성은 존재하지만 정체·생각·정확한 목적은 자동으로 알 수 없다.
4. `비시선 위험 제외`
   - 압력판, 소리, 발자국, 냄새, 저장된 기록처럼 시선이 아닌 위험은 능력으로 직접 감지하지 못한다.
5. `성장 제한`
   - 1~5화 구간은 stage_01_awareness로 유지한다.
   - 감시 루틴 예측, 광역 감시망 지도화, 정밀 역추적은 후속 성장 단계에서만 가능하다.

## 2. 변경 이유

현재 설정은 상업적 후킹을 위해 “자신을 볼 가능성이 있는 모든 시선”이라는 강한 문장을 사용한다. 이 문장은 매력적이지만 장기 연재에서는 다음 오해를 만들 수 있다.

- 모든 카메라 기록이나 저장 영상까지 감지하는 것처럼 읽힐 위험
- 시선이 없는 함정까지 감지할 수 있는 것처럼 확장될 위험
- 4화의 감시 루틴 활용이 stage_03 능력인 “감시 루틴 예측”으로 오해될 위험
- 매개 시선과 직접 시선의 차이가 불명확해질 위험

따라서 핵심 능력을 약화하지 않으면서도 “무엇을 감지하고, 무엇을 감지하지 못하는가”를 canon으로 고정해 향후 회차의 설정 안정성을 높인다.

## 3. 영향을 받는 파일

### 승인 후 수정 후보

- `webnovel_pm_workspace/projects/blindspot/story_bible.json`
  - `core_premise`와 `canon_boundaries`에 현재성/시야 경로/비시선 위험 제외 규칙 추가 후보
- `webnovel_pm_workspace/projects/blindspot/ability_rules.json`
  - `core_rule`, `activation_conditions`, `limits`, `growth_rules`, `forbidden_shortcuts` 보강 후보
- `webnovel_pm_workspace/projects/blindspot/power_progression.json`
  - stage_01과 stage_03의 경계 문구 명확화 후보
- `webnovel_pm_workspace/projects/blindspot/canon_log.json`
  - 승인 시 신규 canon entry 추가 후보
- `webnovel_pm_workspace/projects/blindspot/foreshadowing_ledger.json`
  - 비시선 위험/저장 기록 관련 복선 태그 정리 후보

### 참조만 필요한 파일

- `webnovel_pm_workspace/projects/blindspot/timeline.json`
- `webnovel_pm_workspace/projects/blindspot/location_registry.json`
- `webnovel_pm_workspace/projects/blindspot/rolling_context.md`
- `webnovel_pm_workspace/projects/blindspot/episodes/episode_001_final_v2.md`
- `webnovel_pm_workspace/projects/blindspot/episodes/episode_002_final_v2.md`
- `webnovel_pm_workspace/projects/blindspot/episodes/episode_003_final_v2.md`
- `webnovel_pm_workspace/projects/blindspot/episodes/episode_004_final_v2.md`

## 4. 영향을 받는 회차

- direct_rewrite_required: 없음
- direct_setting_reference:
  - episode_001: 시선 방향, 카메라/사람 시선 구분, 사각지대 감지
  - episode_002: 녹화 기록 자체는 감지하지 못한다는 한계
  - episode_003: 다수 시선/반사면 혼선과 stage_01 한계
  - episode_004: 시선이 없는 압력판 함정과 감시 루틴 정보 활용
- future_impact:
  - episode_005 이후 모든 능력 운용 장면
  - stage_02_filtering 진입 시점
  - stage_03_counter_watch 진입 시점

## 5. 기존 canon과 충돌 여부

- conflict_status: no_direct_conflict
- reason:
  - 기존 canon의 “시선 감지는 마음 읽기나 완전한 미래 예지가 아니다”와 일치한다.
  - 기존 canon의 “감지 대상은 주인공을 볼 가능성이 있는 시선이다”를 폐기하지 않고 판정 조건을 세분화한다.
  - 기존 canon의 “카메라·거울·렌즈는 매개 시선으로 조건부 감지된다”를 더 명확히 한다.
  - 1~4화 final에서 이미 사용된 “기록은 감지하지 못함”, “시선 없는 함정은 감지하지 못함”과 충돌하지 않는다.
- caution:
  - “모든 시선”이라는 표현의 강한 후킹은 유지하되, 본문/설정 파일에서는 “현재 한서진을 볼 가능성이 있는 관측 경로”라는 제한을 함께 써야 한다.

## 6. 반영 시 장점

1. 능력의 만능화를 막아 장기 연재의 긴장감을 유지한다.
2. 2화의 저장 기록 한계와 4화의 압력판 함정이 명확한 능력 한계로 강화된다.
3. stage_01과 stage_03의 경계가 선명해져 갑작스러운 파워업 오해를 줄인다.
4. 향후 잠입/조직전에서 “시선은 피했지만 다른 위험은 남아 있다”는 장면 설계가 쉬워진다.
5. 독자에게 공정한 룰을 제공해 위기 해결의 납득도를 높인다.

## 7. 반영 시 위험

1. `모든 시선 감지`라는 초기 후킹이 약해 보일 수 있다.
2. 제한 조건이 과도하게 설명되면 장면보다 설정 설명이 앞설 수 있다.
3. 매개 시선 조건을 너무 엄격하게 쓰면 카메라/렌즈를 활용한 현대 판타지 재미가 줄어들 수 있다.
4. 이미 작성된 1~4화 final 문장 중 일부 표현이 향후 수정 대상처럼 보일 수 있다.
5. 능력 경계를 너무 일찍 고정하면 후반 성장 변주의 여지가 줄어들 수 있다.

## 8. 반영하지 않을 경우 대안

1. `story_bible.json`과 `ability_rules.json`은 그대로 두고, 회차별 review에서만 “기록/비시선 위험 감지 금지”를 계속 점검한다.
2. `power_progression.json`의 `last_verified_episode`와 character status metadata만 정리하고, 핵심 능력 canon은 변경하지 않는다.
3. 5~7화 배치 작성 전 별도 `continuity_audit_002.md`를 먼저 작성해 실제 충돌이 발생하는지 재검사한다.
4. 독자에게 설명하지 않고 장면 반복으로 한계를 체감시키되, 내부 작업용 `rolling_context.md`에만 운영 메모를 남긴다.

## 9. 사용자 승인 필요 여부

- required: yes
- reason:
  - 이 요청은 `story_bible.json`과 `ability_rules.json`의 핵심 능력 정의에 영향을 줄 수 있다.
  - repository 규칙상 새 canon 변경은 `canon_change_request` 작성 후 사용자 승인 전에는 반영하지 않는다.
  - 승인 전에는 story_bible, ability_rules, canon_log, final 원고를 수정하지 않는다.
- approval_options:
  1. approve: 위 canon을 승인하고 관련 Bible/규칙 파일 반영 작업을 별도 요청한다.
  2. revise_request: 현재성/시야 경로/비시선 위험 제외 중 일부만 수정해 재요청한다.
  3. reject: 핵심 설정 변경 없이 기존 canon을 유지한다.

## 승인 전 반영 금지 항목

- [x] `story_bible.json` 직접 수정 금지
- [x] `ability_rules.json` 직접 수정 금지
- [x] `power_progression.json` 직접 수정 금지
- [x] `canon_log.json` 확정 변경 금지
- [x] 1~4화 final 원고 수정 금지
