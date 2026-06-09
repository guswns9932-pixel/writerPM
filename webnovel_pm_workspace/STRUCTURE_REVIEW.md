# workspace structure review

## 검토 기준

사용자가 제시한 운영 기준은 다음 active structure로 해석한다.

1. 운영 전제: API 사용 없음, `OPENAI_API_KEY` 없음, 외부 자동화 앱 없음, Codex 안 자연어 지시
2. 통제 문서: `AGENTS.md`, `CODEX_WORKFLOW.md`, `PROJECT_POLICY.md`, `REPORT_FORMAT.md`
3. Harness 문서: workflow, memory, continuity, quality, originality, feedback, recovery, versioning, cast, longform
4. 작품 기억: `projects/{project_id}/` 아래 Bible, 규칙, 시간선, 로그, context, 취향, format policy
5. 회차 산출물: `projects/{project_id}/episodes/` 아래 outline, v1 draft, review, revision note, v2 final, status
6. 안전장치: `canon_change_requests/`, `feedback_application_plans/`, `recovery_plans/`, halt reason code, final versioning, 3화 단위 제한, 사용자 승인 gate

## 현재 active root 구조

`webnovel_pm_workspace/`의 active root는 아래 구조로 정리한다.

```text
webnovel_pm_workspace/
├─ AGENTS.md
├─ README.md
├─ CODEX_WORKFLOW.md
├─ PROJECT_POLICY.md
├─ REPORT_FORMAT.md
├─ STRUCTURE_REVIEW.md
├─ templates/
├─ prompts/
├─ harness/
├─ projects/
└─ examples/
```

## 구조 검토 결과

### 유지

- `templates/`: 작품별 기본 JSON/Markdown 템플릿 보관에 필요하다.
- `prompts/`: Codex 자연어 작업 지시 패턴을 문서화하는 데 필요하다.
- `harness/`: 품질, 연속성, memory, recovery, versioning, cast, longform 등 검수 기준이므로 필요하다.
- `projects/`: 실제 작품별 기억 파일, 회차 산출물, run report, 안전장치를 보관하는 핵심 위치다.
- `examples/`: 실제 active 프로젝트가 아닌 예시 구조를 보존하는 위치다.

### 이동

다음 폴더들은 active project-centric 구조와 중복되므로 workspace root에서 제거하고 예시로 이동했다.

- `00_control/`
- `01_concept/`
- `02_worldbuilding/`
- `03_plot/`
- `04_characters/`
- `05_style/`
- `06_episode_001/`
- `07_episode_batches/`
- `08_review/`
- `09_revision/`
- `10_exports/`

새 위치:

```text
webnovel_pm_workspace/examples/legacy_single_project_scaffold/
```

이들은 지금 active 운영에는 필수는 아니지만, 초기 단일 작품 scaffold 예시로는 가치가 있으므로 삭제하지 않고 `examples/`로 보존한다.

### 재분류

`checklists/`는 독립 active root 폴더로 두기보다 harness의 일부로 보는 것이 구조상 자연스럽다.

새 위치:

```text
webnovel_pm_workspace/harness/checklists/
```

### 제거

`archive/`는 현재 별도 보존 대상이 없고, legacy scaffold는 `examples/`로 이동했으므로 active root에서 제거했다.

## blindspot 프로젝트 구조 확인

`webnovel_pm_workspace/projects/blindspot/`는 다음 기준을 충족한다.

### 작품 기억 파일

- `story_bible.json`
- `character_bible.json`
- `ability_rules.json`
- `power_progression.json`
- `timeline.json`
- `arc_state.json`
- `cast_registry.json`
- `location_registry.json`
- `foreshadowing_ledger.json`
- `style_guide.json`
- `canon_log.json`
- `rolling_context.md`
- `user_feedback_log.json`
- `user_taste_profile.json`
- `episode_format_policy.json`

### 회차 산출물

`episodes/` 아래에 회차별 outline, draft, review, revision note, final, status 파일을 둔다.

### 안전장치

- `canon_change_requests/`
- `feedback_application_plans/`
- `recovery_plans/`
- `run_reports/`
- `episode_XXX_status.md` 안 halt/review/final 상태 기록
- 기존 final 덮어쓰기 금지 규칙 유지

## 결론

현재 workspace는 project-centric 구조로 정리되었다. active root에는 통제 문서와 5개 핵심 폴더만 남기고, 과거 단일 작품용 numbered scaffold는 예시로 이동했다. 작품 운영은 `projects/{project_id}/` 아래 기억 파일, 회차 산출물, 안전장치 중심으로 진행한다.
