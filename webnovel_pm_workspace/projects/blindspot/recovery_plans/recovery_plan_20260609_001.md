# recovery_plan_20260609_001 - continuity_audit_001 후속 복구 계획

## 기본 정보

- recovery_id: recovery_plan_20260609_001
- project_id: blindspot
- source_report: `webnovel_pm_workspace/projects/blindspot/run_reports/continuity_audit_001.md`
- related_episode_range: episode_001 ~ episode_004
- status: pending_user_decision
- created_at: 2026-06-09
- requested_action: 원고 수정 없이 recovery_plan만 작성

## 1. 문제 요약

`continuity_audit_001.md`는 1~4화 final 원고 기준으로 critical issue를 발견하지 않았다.

- critical_issue: 없음
- final 저장 금지 조건: 발견되지 않음
- canon_change_request: 불필요
- recovery_plan: 불필요
- 1~4화 final 기준 설정 안정성: 안정적

다만 장기 운영 전에 정리하면 좋은 경미한 metadata warning 2개가 있다.

1. `power_progression.json`의 `last_verified_episode`가 아직 `episode_001`로 남아 있어 2~4화 검수 완료 상태를 반영하지 않는다.
2. `character_bible.json`의 인물 status가 최신 회차 진행을 완전히 반영하지 않는다.
   - 윤하라: `planned` 상태이지만 2화 음성, 3~4화 직접 등장 완료
   - 마경태: `active_ep001` 상태이지만 2~4화에서도 추적/압박 지속

따라서 이 recovery_plan은 실제 critical issue 복구안이 아니라, `continuity_audit_001.md`의 minor metadata warning을 기준으로 한 예방적 복구 계획이다.

## 2. halt_reason_code

- halt_reason_code: `NO_CRITICAL_ISSUE_METADATA_WARNING`
- halt_required: no
- reason: audit 결과 critical issue가 없으므로 원고 작성/검수 흐름을 강제 중단할 필요는 없다. 단, 다음 회차 작성 전 metadata 정합성을 맞추면 운영 안정성이 높아진다.

## 3. 영향받은 회차

- direct_manuscript_impact: 없음
- metadata_reference_impact:
  - episode_002
  - episode_003
  - episode_004
- note: 1~4화 final 원고 자체의 사건, 능력 사용, 시간선, canon은 유지 가능하다.

## 4. 영향받은 설정 파일

- `webnovel_pm_workspace/projects/blindspot/power_progression.json`
  - `last_verified_episode` metadata 최신화 후보
- `webnovel_pm_workspace/projects/blindspot/character_bible.json`
  - 윤하라 status 최신화 후보
  - 마경태 status 최신화 후보
- reference_only:
  - `webnovel_pm_workspace/projects/blindspot/cast_registry.json`
  - `webnovel_pm_workspace/projects/blindspot/timeline.json`
  - `webnovel_pm_workspace/projects/blindspot/canon_log.json`

## 5. 수정 범위

- [ ] TEXT_ONLY
- [ ] SCENE_REWRITE
- [ ] EPISODE_OUTLINE_REWRITE
- [x] CONTINUITY_REPAIR
- [x] BIBLE_CHANGE_REQUIRED

### 범위 판단

- 원고 문장, 장면, outline 수정은 필요하지 않다.
- 실제 복구가 진행된다면 `power_progression.json`과 `character_bible.json`의 metadata를 최신화하는 continuity repair가 된다.
- `character_bible.json`은 작품 Bible 계열 파일이므로, 변경 전 사용자 승인이 필요하다.

## 6. canon_change_request 필요 여부

- required: no
- reason: 새 설정을 추가하거나 기존 canon을 변경하지 않는다. 이미 2~4화 final과 `cast_registry.json`, `timeline.json`, `canon_log.json`에 반영된 진행 상태를 Bible metadata와 검수 metadata에 맞추는 작업이다.
- caveat: 만약 윤하라/마경태의 역할, 소속, 목적 자체를 바꾸는 방향으로 확대한다면 별도의 `canon_change_request`가 필요하다.

## 7. 추천 복구안 3개

### 복구안 A: 최소 metadata sync

- 수정 대상:
  - `power_progression.json`
  - `character_bible.json`
- 작업 내용:
  1. `power_progression.json`의 `last_verified_episode`를 `episode_004`로 갱신한다.
  2. 윤하라 status를 `planned`에서 `active` 또는 `active_conditional_ally`로 갱신한다.
  3. 마경태 status를 `active_ep001`에서 `active_recurring_pursuer`로 갱신한다.
- 장점: 원고와 canon을 건드리지 않고 가장 작은 범위로 정합성을 맞춘다.
- 단점: 상태 metadata만 정리하므로 장기 플롯 메모까지 확장되지는 않는다.
- 사용자 승인 필요: yes

### 복구안 B: 5화 작성 전 deferred maintenance

- 수정 대상:
  - 다음 회차 작성 직전 위 metadata만 일괄 점검
- 작업 내용:
  1. 현재 파일은 그대로 둔다.
  2. 5~7화 배치 또는 다음 사용자 요청 전, metadata warning을 다시 확인한다.
  3. 사용자가 승인하면 그때 `power_progression.json`과 `character_bible.json`을 갱신한다.
- 장점: 지금은 파일 수정 없이 현재 상태를 보존한다.
- 단점: 다음 작업자가 warning을 놓치면 5화 이후 reference drift가 누적될 수 있다.
- 사용자 승인 필요: yes, 실제 수정 시점에 필요

### 복구안 C: 전체 continuity maintenance pass

- 수정 대상:
  - `power_progression.json`
  - `character_bible.json`
  - `cast_registry.json`
  - `timeline.json`
  - `canon_log.json`
  - `foreshadowing_ledger.json`
  - `rolling_context.md`
- 작업 내용:
  1. 1~4화 기준으로 모든 상태/검수/등장 정보 metadata를 재동기화한다.
  2. 각 파일의 `last_updated_episode`, `last_verified_episode`, pending/review status를 통일한다.
  3. 필요하면 별도 maintenance run_report를 작성한다.
- 장점: 장기 운영 안정성이 가장 높다.
- 단점: 이번 warning에 비해 수정 범위가 크고, canon 변경은 아니더라도 Bible/ledger/status 파일을 다수 건드린다.
- 사용자 승인 필요: yes

## 8. 가장 안전한 복구안

- selected_recovery_option: 복구안 A - 최소 metadata sync
- reason:
  - audit에서 원고 critical issue가 발견되지 않았다.
  - 원고 final, outline, scene, canon 사건을 바꾸지 않는다.
  - 실제 어긋난 부분은 검수 완료 회차와 인물 status metadata이므로 최소 설정 파일만 갱신하면 된다.
  - canon_change_request 없이 처리 가능하다.

## 9. 수정 시 예상 영향

- manuscript_impact: 없음
- episode_outline_impact: 없음
- canon_impact: 없음
- power_rule_impact: 없음
- character_continuity_impact: 낮음. 기존 등장 사실을 metadata에 반영하는 수준이다.
- future_episode_planning_impact: 중간. 다음 배치에서 윤하라/마경태를 이미 active 인물로 참조할 수 있어 혼선이 줄어든다.
- risk_if_not_fixed: 낮음~중간. 현재 원고 안정성은 유지되지만, 장기 배치 작성 시 `character_bible.json`의 stale status를 근거로 인물 활용이 어긋날 수 있다.

## 10. 사용자 승인 필요 여부

- required: yes
- reason:
  - 현재 요청은 recovery_plan 작성만이며 원고/설정 수정 금지 조건이 있다.
  - 추천 복구안 A도 `character_bible.json`과 `power_progression.json`을 수정하므로 사용자 승인 후 진행해야 한다.
- approval_prompt:
  - "복구안 A대로 `power_progression.json`과 `character_bible.json` metadata만 갱신해줘."

## 현재 작업에서 하지 않은 것

- 1~4화 final 원고 수정 없음
- outline 수정 없음
- scene rewrite 없음
- canon 변경 없음
- `canon_change_request` 작성 없음
- 설정 파일 직접 수정 없음
