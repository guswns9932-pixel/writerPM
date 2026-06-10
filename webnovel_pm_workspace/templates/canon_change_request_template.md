# Canon Change Request Template

## 요청 정보

- request_id: canon_change_YYYYMMDD_001
- project_id: example_project
- requested_by: Codex / User
- status: pending_user_approval
- related_episode: episode_001

## 변경 요청 요약

-

## 기존 canon

- canon_id: CANON001
- current_value: 예시 - 능력 사용에는 하루 1회 제한이 있다.
- source_file: canon_log.json

## 제안 canon

- proposed_value: 예시 - 특정 대가를 지불하면 하루 2회까지 가능하다.
- reason:
- narrative_benefit:
- risk:

## 영향 범위

- story_bible.json:
- character_bible.json:
- ability_rules.json:
- power_progression.json:
- timeline.json:
- foreshadowing_ledger.json:
- affected_episodes:

## 승인 전 반영 금지 항목

- [ ] Bible 파일 수정
- [ ] canon_log 확정 변경
- [ ] final 원고 반영

## 사용자 결정 필요

- approve / reject / revise_request

## High-risk State Impact

- approval_state 영향:
- final_registry 영향:
- ability_usage_log 영향:
- payoff_schedule 영향:
- quality_trend_log 영향:
- reader_reward_ledger 영향:
- voice_samples 영향:

## 승인 전 직접 수정 금지 파일

- `story_bible.json`
- `character_bible.json`
- `ability_rules.json`
- `power_progression.json`
- `canon_log.json`
- 기존 final 파일
- `final_registry.json`의 승인 상태

## Canon Change Threshold

| 변경 유형 | canon_change_request 필요 여부 | 승인 전 직접 수정 가능 여부 |
|---|---|---|
| 오탈자/표현 정리 | no | 가능하나 final 덮어쓰기 금지 |
| 설명 보강, 모호성 해소 | maybe | 핵심 규칙 변화 없을 때만 |
| 능력 조건/한계/대가 변경 | yes | no |
| 주인공 욕망/결핍/선택 원칙 변경 | yes | no |
| 조직 목적/세계 규칙 변경 | yes | no |
| 기존 canon 폐기 또는 대체 | yes | no |

## 승인 후 적용 범위

- approved_patch_scope:
- forbidden_changes_even_if_approved:
- post_change_audit_required:
