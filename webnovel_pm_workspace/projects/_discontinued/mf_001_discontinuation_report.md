# mf_001 discontinuation report

`RECOVERY_HARNESS.md`의 "프로젝트 전체 중단 절차"에 따라 소급 작성한 보고서입니다. 중단 당시(2026-06-11) 이 절차가 아직 문서화되어 있지 않아 커밋 메시지("Remove project mf_001 - discontinued")만 남고 별도 보고서가 없었습니다. 이 문서는 git 이력을 근거로 그 공백을 메웁니다.

## 기본 정보

- project_id: `mf_001`
- title: 냄새로 본다 (모던 판타지)
- decision_date: 2026-06-11 (커밋 `4cca5c8`)
- discontinuation_reason: 아래 "중단 사유" 참고
- last_completed_stage: episode_001 final v6까지 작성, 그러나 `approval_state.json`상 정식 승인은 outline 단계(`outline_in_progress`)에 머물러 있었음
- user_confirmation: **레포 안에서 확인 불가.** 커밋 이력에는 사용자가 중단을 명시적으로 승인했다는 기록이 없다. 이 항목은 실제 확인이 필요하면 사용자에게 재확인해야 한다.

## 중단 사유

1화 원고가 "AI가 쓴 것 같다"는 문제를 반복적으로 재발시켰다. 커밋 이력상 같은 1화를 6번(v1~v6) 다시 썼다.

| 버전 | 커밋 | 시도한 수정 |
|---|---|---|
| v1 | `749c53c` | 초안 완료 |
| — | `988078b`, `e2f5a32` | 글자수 요건(4800~5200자) 재작성, 쉬운 한국어 문체로 v3 재작성 |
| — | `57fce93` | 한국어 문법/명료성 수정 |
| — | `84ef1ba`, `6c02cf1` | STYLE_HARNESS 도입 및 AI식 문장 제거, 자연스러운 웹소설 문체로 전면 개정 |
| v3 | `410a450` | "사람이 쓴 것 같은" 문체로 최종 개정 |
| v4 | `0702b7f` | 구조/문장 리듬 재정비 |
| v5 | `bcb46fb` | 7개 항목 정밀 수정 |
| v6 | `501f10c` | 5개 항목 정밀 수정, 캐릭터 동기 보강 |

이 과정에서 반복적으로 걸린 문제는 "의미 라벨링", "장면 제목식 문장", "감정 선언", "능력을 추상적으로 설명하는 표현", "신체 부위 의인화"였다. 같은 문제가 v3 이후에도 재발했다는 것은 문체 규칙이 harness 문서로 굳어 있지 않고 매번 즉흥적으로 지적·수정되었다는 뜻이다.

## salvaged_learnings (harness/prompt에 반영된 교훈)

프로젝트를 계속 밀어붙이는 대신, 반복된 문제를 구조적 규칙으로 추출하고 프로젝트를 중단했다.

- `harness/KOREAN_GRAMMAR_HARNESS.md` 신설 (문피아 스타일 한국어 문법 규칙)
- `harness/READABILITY_HARNESS.md` 신설 (중학생 수준 가독성 기준)
- `harness/STYLE_HARNESS.md`에 규칙 13(의인화 표현 금지), 14(능력 사용 시 신체 변화로만 표현) 추가
- 위 세 harness는 이번 평가 후속 조치로 `HARNESS_ROUTER.md`의 `episode_draft`/`revision` 라우팅과 `prompts/07_episode_draft.md`, `prompts/12_revision.md`에 실제로 연결 완료됨 (이전에는 STYLE_HARNESS만 연결되어 있었고 새 harness 2종은 어디에서도 참조되지 않는 상태였음)

## 별도로 발견된 프로세스 이슈 (참고용)

mf_001 자체의 `approval_state.json`은 "story_bible 승인" 이후 `pending_approvals`에 "draft/final 진행 전 사용자 승인 필요"라고 명시했지만, 실제로는 승인 기록 갱신 없이 draft v1부터 final v6까지 계속 작성되었다. 프로젝트가 삭제되어 소급 수정은 불가능하지만, 이는 `WORKFLOW_HARNESS.md`가 요구하는 "1화 승인 게이트"가 지켜지지 않은 사례로 남긴다.

## preserved_artifacts

- 삭제된 mf_001 전체 파일은 git 이력에 보존됨: `git show 4cca5c8^:webnovel_pm_workspace/projects/mf_001/...`
- 삭제 커밋: `4cca5c8` (부모 커밋 `501f10c`에 전체 상태 존재)
