# Feedback Application Plan Template

## 기본 정보

- plan_id: feedback_plan_YYYYMMDD_001
- project_id: example_project
- related_feedback_id: feedback_YYYYMMDD_001
- target_episode: episode_001
- status: pending_user_approval

## 피드백 원문 요약

-

## 피드백 해석

- 원하는 감정 변화:
- 줄거리 변경 여부:
- 인물 변경 여부:
- 문체 변경 여부:
- canon 변경 여부:
- 불명확한 부분:

## 반영 대상 분류

- [ ] TEXT_ONLY
- [ ] SCENE_REWRITE
- [ ] EPISODE_OUTLINE_REWRITE
- [ ] CONTINUITY_REPAIR
- [ ] BIBLE_CHANGE_REQUIRED
- [ ] STYLE_ADJUSTMENT
- [ ] PENDING_CLARIFICATION

## 변경 예정 파일

-

## 예상 변경 범위

-

## 위험 요소

- final 덮어쓰기 위험: no / yes
- canon 변경 필요: no / yes
- 추가 사용자 확인 필요: no / yes

## 사용자 승인 필요 사항

-

## Feedback Impact Matrix

- TEXT_ONLY:
- STYLE_ADJUSTMENT:
- CHARACTER_VOICE:
- SCENE_REWRITE:
- CONTINUITY_REPAIR:
- BIBLE_CHANGE_REQUIRED:
- SCOPE_EXPANSION_RISK:

## High-risk State Updates If Approved

- approval_state.json:
- final_registry.json:
- ability_usage_log.json:
- payoff_schedule.json:
- quality_trend_log.json:
- reader_reward_ledger.json:
- voice_samples.md:
- user_feedback_log.json:

## 영향도 판정 기준

| 분류 | 적용 가능 예 | 확대 금지선 | 필요한 후속 파일 |
|---|---|---|---|
| TEXT_ONLY | 오탈자, 문장 압축 | 사건 결과 변경 | revision_note |
| STYLE_ADJUSTMENT | 건조한 문체, 문단 호흡 | 성격/욕망 변경 | style_check, revision_note |
| CHARACTER_VOICE | 대사/내면 독백 조정 | character_bible 변경 | voice_samples, revision_note |
| SCENE_REWRITE | 특정 장면 재작성 | 회차 목표 변경 | review, status |
| CONTINUITY_REPAIR | 시간선/설정 보정 | 새 canon 확정 | recovery_plan 또는 canon_change_request |
| BIBLE_CHANGE_REQUIRED | 능력 규칙/세계 규칙 변경 | 승인 전 반영 | canon_change_request |
| SCOPE_EXPANSION_RISK | 다음 회차/배치로 확장 | 사용자 승인 없는 진행 | 사용자 확인 필요 |
