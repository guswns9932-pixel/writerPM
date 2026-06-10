# AGENTS.md

이 파일은 이 repository에서 작업하는 Codex가 항상 따라야 하는 절대 규칙입니다. 이 규칙은 repository 전체에 적용됩니다.

## Repository 정체성

1. 이 repository는 한국 웹소설 제작용 Codex workspace다.
2. 사용자는 Codex 안에서 자연어로 계속 지시한다.
3. 이 repository의 산출물은 문서, 템플릿, 원고, 검수 기록, 수정 기록, 진행 보고서 중심으로 관리한다.

## 만들지 않는 것

4. 외부 API 기반 자동 생성 프로그램을 만들지 않는다.
5. OpenAI API 연결을 만들지 않는다.
6. `OPENAI_API_KEY` 설정이나 사용을 만들지 않는다.
7. 실제 `LLMClient` 구현을 만들지 않는다.
8. 서버를 만들지 않는다.
9. 웹 UI를 만들지 않는다.
10. FastAPI, Streamlit, React 등 외부 실행 앱 구조를 만들지 않는다.

## 작업 범위 통제

11. Codex는 한 번의 사용자 요청에서 명시된 작업 범위만 수행한다.
12. 사용자가 요청하지 않은 다음 회차, 다음 배치, 추가 수정, 설정 변경을 임의로 진행하지 않는다.
13. 최초 작업은 컨셉부터 1화 final까지만 수행한다.
14. Codex는 사용자의 명시적 승인 없이 2화 이후를 작성하지 않는다.
15. 1화 이후 추가 생성은 기본 3화 단위로만 진행한다.
16. 배치 생성 후 반드시 사용자 검토 대기 상태로 정리한다.
17. Codex는 작업 후 변경 파일 목록과 다음 가능한 작업을 보고한다.

## 원고 작성 전 필수 확인 파일

18. 원고 작성 전 반드시 다음 파일 또는 해당 역할의 문서를 확인한다.
    - `story_bible`
    - `character_bible`
    - `ability_rules`
    - `canon_log`
    - `timeline`
    - `foreshadowing_ledger`
    - `style_guide`
    - `rolling_context`
19. 위 문서가 아직 없다면, Codex는 원고를 final로 저장하기 전에 누락 사실을 보고하고 필요한 문서 생성 또는 보강을 사용자에게 제안한다.

## Canon, 설정, 시간선 관리

20. 설정 충돌, 능력 규칙 위반, 인물 붕괴, 시간선 오류가 있으면 final로 저장하지 않는다.
21. 새 canon 변경이 필요하면 `canon_change_request`를 작성하고 사용자 승인 전에는 반영하지 않는다.
22. 사용자 피드백은 `user_feedback_log`에 기록한다.
23. 사용자가 "바로 반영"이라고 명시하지 않은 피드백은 `feedback_application_plan`을 먼저 작성한다.

## 독창성 및 모방 금지

24. 특정 기존 작품의 고유 설정, 고유 용어, 대표 장면, 특정 작가 문체를 모방하지 않는다.
25. 장르 문법은 활용하되 고유 조합과 표현은 새롭게 만든다.

## 회차 품질 기준

26. 각 회차는 후킹, 주인공 선택, 독자 보상, 클리프행어를 포함해야 한다.
27. 각 회차마다 `episode_XXX_status.md`를 작성한다.
28. 생성 후에는 반드시 `review`, `revision_note`, `run_report`를 남긴다.

## 파일 버전 관리

29. 기존 final 파일은 덮어쓰지 않는다.
30. final 수정본은 `v3`, `v4`처럼 새 버전으로 저장한다.
31. 초안, 검수본, 수정본, final, 상태 파일은 역할이 드러나도록 파일명을 명확히 작성한다.

## 중단 및 복구

32. critical issue 발생 시 `halt_reason_code`를 기록하고 `recovery_plan`을 작성한다.
33. critical issue의 예시는 다음과 같다.
    - 설정 충돌
    - 능력 규칙 위반
    - 인물 붕괴
    - 시간선 오류
    - 사용자 승인 없는 작업 범위 초과
    - 기존 final 파일 덮어쓰기 위험

## 승인 상태, registry, 누적 로그 강화

34. 회차 작성, 배치 작성, final 수정, canon 변경 전에는 `approval_state.json` 또는 해당 역할의 승인 상태 문서를 확인한다.
35. 승인 상태가 불명확하면 원고, 다음 회차, 다음 배치, final 수정, canon 변경을 진행하지 않고 사용자 확인 필요 사항으로 보고한다.
36. 사용자가 3화를 초과하는 회차 생성을 요청하더라도 Codex는 기본 3화 단위까지만 수행하고 나머지는 다음 가능한 작업으로 보고한다.
37. 사용자가 "검토만", "리뷰만", "제안만", "아직 수정하지 말고"라고 명시하면 파일을 생성하거나 수정하지 않는다.
38. final 후보 또는 승인본을 생성하거나 수정본을 만들 때는 `final_registry.json` 또는 해당 역할 문서를 갱신한다.
39. 기존 final 파일은 읽기 전용으로만 참조하며 직접 편집하지 않는다.
40. 승인된 final과 승인 대기 final 후보를 명확히 구분한다.
41. `episode_XXX_status.md`와 `final_registry`가 충돌하면 final 저장을 중단하고 `recovery_plan`을 작성한다.
42. 능력 사용이 포함된 회차는 `ability_usage_log.json` 또는 해당 역할 문서에 실제 사용 장면, 허용 단계, 대가/한계, 위반 여부를 기록한다.
43. 새 복선, 복선 회수, 회수 지연은 `foreshadowing_ledger.json`과 `payoff_schedule.json` 또는 해당 역할 문서에 기록한다.
44. 주요 인물의 대사나 내면 독백을 작성 또는 수정할 때는 `voice_samples.md` 또는 해당 역할 문서를 확인한다.
45. 회차 품질과 독자 보상은 `quality_trend_log.json`, `reader_reward_ledger.json` 또는 해당 역할 문서에 누적한다.
46. 작업 유형별 필수 harness는 `HARNESS_ROUTER.md` 또는 해당 역할 문서를 기준으로 확인한다.

## 피드백, 독창성, 보고 완료 조건 강화

47. 사용자 피드백은 `TEXT_ONLY`, `STYLE_ADJUSTMENT`, `CHARACTER_VOICE`, `SCENE_REWRITE`, `CONTINUITY_REPAIR`, `BIBLE_CHANGE_REQUIRED`, `SCOPE_EXPANSION_RISK` 중 하나 이상으로 분류한다.
48. 말투나 문체 피드백은 기본적으로 대사/문장 수정 범위로 제한하며, 인물 성격·욕망·결핍·canon 변경으로 확대하지 않는다.
49. 피드백 반영 범위가 불명확하면 적용하지 않고 `feedback_application_plan`에 사용자 확인 필요 사항으로 기록한다.
50. 특정 작품명이 사용자 요청에 등장하더라도 Codex는 고유 설정, 고유 용어, 대표 장면, 문체를 재현하지 않고 장르적 기대나 추상적 기능만 참고한다.
51. 기존 작품과 유사성 우려가 발견되면 `originality_review` 또는 `originality_ledger` 역할 문서에 기록하고, 차별화 조치 전 final 저장을 중단한다.
52. 작업 완료 보고는 반드시 `REPORT_FORMAT.md` 형식을 따른다.
53. 원고, 검수, 수정, 배치 작업에서 `run_report`가 없으면 작업을 완료한 것으로 보고하지 않는다.
54. `run_report_index.json` 또는 해당 역할 문서가 있으면 작업 후 보고서 색인을 갱신한다.
55. “다음 가능한 작업”에는 작업 후보만 적고, 사용자 지시 전 실제 장면, 대사, 설정, 다음 회차 내용을 작성하지 않는다.
56. 작업 시작 전 이번 요청에서 생성 또는 수정할 수 있는 파일 범위를 확인하고, 사용자 요청 범위와 직접 관련 없는 파일은 수정하지 않는다.

## 확장된 critical issue

57. critical issue에는 독창성/표절성 유사성 위험, 권리/플랫폼 리스크, 승인 상태 불일치, final registry/status 불일치, 등장인물 과다, 복선 회수 불능, 반복 패턴으로 인한 독자 보상 약화, 작업 범위 밖 파일 수정도 포함한다.
58. critical issue가 하나라도 있으면 final, packaging, export, 다음 배치 진행을 중단하고 `halt_reason_code`와 `recovery_plan`을 작성한다.
