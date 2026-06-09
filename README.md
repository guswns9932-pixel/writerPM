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

### `webnovel_pm_workspace/00_control/`

작업 범위, 승인 기록, 진행 상태, workflow를 관리합니다.

### `webnovel_pm_workspace/01_concept/`

장르, 로그라인, 핵심 재미, 후킹 요소, 컨셉 후보를 관리합니다.

### `webnovel_pm_workspace/02_worldbuilding/`

세계관 규칙, 능력 규칙, 시간선, 설정 충돌 방지 메모를 관리합니다.

### `webnovel_pm_workspace/03_plot/`

시놉시스, 회차 계획, 복선 장부를 관리합니다.

### `webnovel_pm_workspace/04_characters/`

인물 Bible, 인물 프로필, 관계, 욕망, 결핍, 말투를 관리합니다.

### `webnovel_pm_workspace/05_style/`

문체 가이드, 대사 톤, 금지 표현, 장면 전환 규칙, 회차 엔딩 규칙을 관리합니다.

### `webnovel_pm_workspace/06_episode_001/`

1화 개요, 초안, 검수, 수정본, final, 상태 파일을 관리합니다.

### `webnovel_pm_workspace/07_episode_batches/`

1화 final 승인 후 3화 단위 추가 작성 배치를 관리합니다.

### `webnovel_pm_workspace/08_review/`

회차별 검수 결과와 품질 점검 기록을 관리합니다.

### `webnovel_pm_workspace/09_revision/`

사용자 피드백, 수정 계획, 수정 기록, revision note를 관리합니다.

### `webnovel_pm_workspace/10_exports/`

사용자에게 전달할 final 원고와 정리본을 관리합니다.

### `webnovel_pm_workspace/templates/`

회차, 검수, 수정 기록 등 반복 사용 템플릿을 보관합니다.

### `webnovel_pm_workspace/checklists/`

작업 범위 통제와 회차 품질 검수 체크리스트를 보관합니다.

### `webnovel_pm_workspace/archive/`

폐기되었거나 보류된 아이디어, 이전 버전 메모를 보관합니다.
