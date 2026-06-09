# writerPM

`writerPM`은 Codex 안에서 자연어 지시를 통해 한국 웹소설을 기획, 작성, 검수, 수정하기 위한 문서 중심 workspace입니다.

## 목적

이 repository의 목적은 한국 웹소설 제작 과정을 파일 기반으로 관리하는 것입니다.

- 컨셉 후보 생성
- 작품 Bible 정리
- 1화 개요, 초안, 검수, 수정, final 작성
- 사용자 승인 후 3화 단위 추가 작성
- 회차별 설정, 문체, 재미, 복선, 시간선, 독창성 검수
- 사용자 피드백, revision note, run report 기록

모든 결과물은 repository 안의 문서 파일로 저장합니다.

## 사용 방식

사용자는 Codex 안에서 자연어로 계속 지시합니다. 예시는 다음과 같습니다.

- “새 작품 컨셉 후보 3개 만들어줘.”
- “2번 컨셉으로 story bible 초안 작성해줘.”
- “1화 개요를 작성하고 검수까지 해줘.”
- “이 피드백을 바로 반영하지 말고 반영 계획부터 작성해줘.”
- “1화 final 승인. 2~4화 배치 개요를 작성해줘.”

Codex는 사용자의 한 번의 요청에서 명시된 작업 범위만 수행합니다. 다음 단계가 자연스럽게 이어지더라도 사용자 승인이나 지시 없이 임의로 진행하지 않습니다.

## API를 쓰지 않는다는 점

이 workspace는 외부 API 기반 자동 생성 프로그램이 아닙니다.

다음을 만들지 않습니다.

- OpenAI API 연결
- `OPENAI_API_KEY` 설정 또는 사용
- 실제 `LLMClient` 구현
- 서버
- 웹 UI
- FastAPI, Streamlit, React 등 외부 실행 앱
- 외부 자동 실행 파이프라인

Codex가 repository 안의 문서를 직접 생성, 수정, 검수하는 방식으로만 운영합니다.

## 운영 원칙

- 최초 작업은 컨셉부터 1화 final까지만 수행합니다.
- Codex는 사용자의 명시적 승인 없이 2화 이후를 작성하지 않습니다.
- 1화 승인 후 추가 작성은 기본 3화 단위로만 진행합니다.
- 배치 생성 후에는 반드시 사용자 검토 대기 상태로 정리합니다.
- 기존 final 파일은 덮어쓰지 않고 새 버전으로 저장합니다.
- 설정 충돌, 능력 규칙 위반, 인물 붕괴, 시간선 오류가 있으면 final로 저장하지 않습니다.

상세 규칙은 `AGENTS.md`, `CODEX_WORKFLOW.md`, `PROJECT_POLICY.md`, `REPORT_FORMAT.md`를 따릅니다.

## 주요 폴더 설명

현재 active workspace 구조는 `webnovel_pm_workspace/` 아래의 통제 문서와 5개 핵심 폴더를 기준으로 합니다. 자세한 구조 검토 결과는 `webnovel_pm_workspace/STRUCTURE_REVIEW.md`를 참고합니다.

### `webnovel_pm_workspace/AGENTS.md`

Codex가 이 workspace에서 반드시 따라야 하는 절대 규칙입니다. 외부 API, API key, 서버, 웹 UI, 외부 자동화 앱을 만들지 않는다는 원칙과 작업 범위 통제 규칙을 포함합니다.

### `webnovel_pm_workspace/CODEX_WORKFLOW.md`

새 작품 시작, 컨셉 후보, Bible 생성, 1화 작성/검수, 피드백 반영, 3화 단위 추가 작성, 중단/복구 절차를 정의합니다.

### `webnovel_pm_workspace/PROJECT_POLICY.md`

작업 범위 제한, 기본 컨셉 후보 수, 최초 1화 final 제한, 추가 작성 3화 단위, 자동 수정 제한, 사용자 승인 gate를 정의합니다.

### `webnovel_pm_workspace/REPORT_FORMAT.md`

Codex가 작업 완료 후 보고해야 하는 형식입니다. 수행한 작업, 생성/수정 파일, 검수 결과, 충돌 여부, 품질 이슈, 다음 가능한 작업을 정리합니다.

### `webnovel_pm_workspace/templates/`

작품별 기본 기억 파일과 회차/status/report/safety 문서 템플릿을 보관합니다. 실제 작품을 만들 때 `projects/{project_id}/` 아래로 복사해 사용합니다.

### `webnovel_pm_workspace/prompts/`

Codex에게 자연어로 반복 지시할 웹소설 제작용 프롬프트 템플릿을 보관합니다. 컨셉 후보, Bible, 캐릭터, 월드빌딩, 회차 개요, 원고, 검수, 수정, 독창성 점검 등을 포함합니다.

### `webnovel_pm_workspace/harness/`

작업 전후 검수 기준을 담은 문서형 harness를 보관합니다. workflow, memory, continuity, quality, originality, feedback, recovery, versioning 기준과 보조 체크리스트가 여기에 속합니다.

### `webnovel_pm_workspace/projects/`

실제 작품별 작업 공간입니다. 각 작품 폴더는 story bible, character bible, ability rules, timeline, canon log, rolling context, episode outputs, run reports, canon change requests, feedback plans, recovery plans를 보관합니다.

### `webnovel_pm_workspace/examples/`

active 작품이 아닌 예시와 legacy scaffold를 보관합니다. 기존 numbered scaffold(`00_control`~`10_exports`)는 active root 구조와 중복되므로 `examples/legacy_single_project_scaffold/`로 이동해 참조용으로만 남겼습니다.
