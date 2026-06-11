# 독자 반응 시뮬레이션 프롬프트 템플릿

## 목적

목표 독자의 시선에서 회차의 몰입, 보상, 이탈 위험, 다음 화 클릭 욕구를 점검한다.

## 입력 파일

- 검수 대상 원고
- `story_bible.json`
- `style_guide.json`
- `QUALITY_HARNESS.md`

## 출력 파일

- `episode_XXX_reader_simulation.md`
- `quality_review.md`

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

| 독자 유형 | 긍정 반응 | 이탈 위험 | 클릭 유도 요소 | 개선 제안 |
|---|---|---|---|---|

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

## High-risk 공통 게이트

### 추가 입력 파일

- `webnovel_pm_workspace/AGENTS.md`
- `webnovel_pm_workspace/harness/HARNESS_ROUTER.md`
- `webnovel_pm_workspace/harness/REQUEST_TYPE_CLASSIFIER.md`
- `webnovel_pm_workspace/harness/REQUIRED_OUTPUTS_MATRIX.md`
- `webnovel_pm_workspace/projects/{project_id}/approval_state.json`
- `webnovel_pm_workspace/projects/{project_id}/final_registry.json`
- `webnovel_pm_workspace/projects/{project_id}/ability_usage_log.json` (능력 사용 또는 검수 관련 작업인 경우)
- `webnovel_pm_workspace/projects/{project_id}/payoff_schedule.json` (복선, 장기 보상, 회차 작업인 경우)
- `webnovel_pm_workspace/projects/{project_id}/voice_samples.md` (대사, 내면 독백, 말투 수정이 있는 경우)
- `webnovel_pm_workspace/projects/{project_id}/run_reports/run_report_index.json` (작업 완료 보고가 필요한 경우)

### 추가 금지사항

- `audit_only`, `review_only`, `proposal_only`, `plan_only` 요청에서 사용자가 파일 생성을 명시하지 않았으면 파일을 만들거나 수정하지 않는다.
- `approval_state.json`이 허용하지 않은 회차 outline, draft, final, batch를 작성하지 않는다.
- 3화를 초과하는 생성 요청은 기본 3화까지만 수행하고 초과분의 장면, 대사, 설정 초안을 작성하지 않는다.
- 기존 final 파일을 직접 편집하지 않는다.
- `final_registry.json`과 `episode_XXX_status.md`가 충돌하면 final 저장을 중단한다.
- `story_bible.json`, `character_bible.json`, `ability_rules.json`, `power_progression.json`의 핵심 변경은 승인된 `canon_change_request` 없이는 반영하지 않는다.

### 추가 업데이트 파일

- request_type 및 승인 상태가 관련되면 `approval_state.json` 확인 결과를 run_report에 기록한다.
- final 후보 또는 수정본이 관련되면 `final_registry.json`과 `episode_XXX_status.md`를 함께 갱신한다.
- 능력 사용이 관련되면 outline/draft/review 단계별로 `ability_usage_log.json`를 갱신한다.
- 복선 추가, 회수, 지연이 관련되면 `foreshadowing_ledger.json`과 `payoff_schedule.json`을 함께 갱신한다.
- 피드백이 관련되면 `feedback_application_plan`의 영향도 매트릭스를 작성하거나 확인한다.
- 작업 완료 시 `run_report`와 필요 시 `run_report_index.json`를 갱신한다.
