# 회차 개요 프롬프트 템플릿

## 목적

요청된 회차의 장면 흐름, 후킹, 갈등, 주인공 선택, 독자 보상, 클리프행어를 설계한다.

## 입력 파일

- `story_bible.json`
- `character_bible.json`
- `ability_rules.json`
- `power_progression.json`
- `timeline.json`
- `canon_log.json`
- `foreshadowing_ledger.json`
- `style_guide.json`
- `rolling_context.md`

## 출력 파일

- `episode_XXX_outline.md`
- `episode_XXX_status.md`
- `rolling_context.md`

## 반드시 지켜야 할 규칙

- 한국 웹소설 독자의 기대와 모바일 연재 가독성을 기준으로 작성한다.
- 첫 500자 안에 후킹 질문, 위험, 욕망, 비밀, 이상 징후 중 하나를 배치한다.
- 주인공의 욕망과 선택을 반드시 드러낸다.
- 회차 단위 작업이라면 독자 보상을 반드시 포함한다.
- 회차 단위 작업이라면 마지막에 클리프행어를 둔다.
- 설명보다 장면, 행동, 대사, 갈등으로 정보를 전달한다.
- 기존 canon, timeline, foreshadowing, style_guide와 충돌하지 않는다.
- 사용자가 명시한 작업 범위만 수행하고 다음 단계로 임의 진행하지 않는다.
- 기존 final 파일은 덮어쓰지 않고 새 버전으로 저장한다.

## 금지사항

- 설정 설명으로 시작하지 않는다.
- 주인공을 수동적으로 사건에 끌려가기만 하게 두지 않는다.
- 특정 기존 작품의 고유 설정, 고유 용어, 대표 장면을 모방하지 않는다.
- 특정 작가 문체를 모방하지 않는다.
- 사용자 승인 없이 2화 이후 본문이나 다음 배치를 작성하지 않는다.
- 사용자 요청 없는 canon 변경을 확정 반영하지 않는다.
- 기존 final 파일을 덮어쓰지 않는다.
- 서버, 웹 UI, 외부 API, 실제 LLMClient, OPENAI_API_KEY 관련 산출물을 만들지 않는다.

## 출력 형식

| 장면 | 목적 | 장소 | 등장인물 | 갈등 | 주인공 선택 | 독자 보상 | 복선/회수 | 다음 장면 연결 |
|---|---|---|---|---|---|---|---|---|

## 작업 후 업데이트해야 할 파일

- `episode_XXX_status.md` 또는 해당 작업 상태 파일
- `rolling_context.md`
- `canon_log.json` 또는 `canon_change_request.md`가 필요한 경우 해당 파일
- `foreshadowing_ledger.json`에 복선 추가 또는 회수 변화가 있는 경우 해당 파일
- `user_feedback_log` 또는 `feedback_application_plan`이 필요한 경우 해당 파일
- `run_report.md`

## 작업 완료 보고

작업 후 `REPORT_FORMAT.md` 형식에 맞춰 다음을 보고한다.

- 수행한 작업
- 생성한 파일
- 수정한 파일
- 검수 결과
- 설정 충돌 여부
- 품질 이슈 여부
- 사용자 확인 필요 사항
- 다음 가능한 작업

## High-risk 보완 규칙

- 작성 전 `approval_state.json`에서 해당 회차가 허용 범위인지 확인한다.
- 입력 파일에 `arc_state.json`, `cast_registry.json`, `location_registry.json`, `episode_pattern_log.json`, `opposition_ladder.json`, `payoff_schedule.json`, `reader_reward_ledger.json`, `voice_samples.md`를 포함한다.
- 승인되지 않은 회차 outline은 작성하지 않는다.
- 새 복선, 능력 사용, 독자 보상, 클리프행어 유형을 outline 단계에서 표시한다.
- 작업 후 `episode_pattern_log.json`, `payoff_schedule.json`, `reader_reward_ledger.json` 갱신 필요 여부를 보고한다.
