# MEMORY_HARNESS

원고 작성 전 필수 기억 파일을 확인하기 위한 문서형 harness입니다.

## 목적

원고 작성 전 프로젝트의 확정 설정, 인물, 능력 규칙, 시간선, 복선, 문체, 직전 맥락을 확인해 설정 충돌과 연속성 오류를 방지합니다.

## 필수 기억 파일 목록

원고 작성 전 다음 파일을 모두 확인해야 합니다.

- [ ] `story_bible.json`
- [ ] `character_bible.json`
- [ ] `ability_rules.json`
- [ ] `power_progression.json`
- [ ] `timeline.json`
- [ ] `canon_log.json`
- [ ] `foreshadowing_ledger.json`
- [ ] `style_guide.json`
- [ ] `rolling_context.md`

## 확인 기준

각 파일에서 최소한 다음 항목을 확인합니다.

### `story_bible.json`

- 작품 핵심 전제
- 장르 약속
- 핵심 갈등
- 금지 설정

### `character_bible.json`

- 주요 인물 성격
- 욕망과 결핍
- 말투
- 관계 변화

### `ability_rules.json`

- 능력 사용 조건
- 능력 한계
- 비용과 대가
- 금지된 사용 방식

### `power_progression.json`

- 현재 성장 단계
- 허용된 강화 범위
- 갑작스러운 파워업 금지 조건

### `timeline.json`

- 사건 순서
- 이동 시간
- 회복 시간
- 정보 전달 시점

### `canon_log.json`

- 확정 canon
- canon 변경 이력
- 사용자 승인 여부

### `foreshadowing_ledger.json`

- 활성 복선
- 회수 예정 복선
- 아직 공개하면 안 되는 정보

### `style_guide.json`

- 문체
- 대사 톤
- 금지 표현
- 모바일 가독성 기준

### `rolling_context.md`

- 직전 회차 요약
- 현재 감정선
- 미해결 갈등
- 다음 회차에 유지해야 할 정보

## 누락 시 작업 중단

필수 파일이 하나라도 누락되면 다음을 수행합니다.

1. 원고 작성과 final 저장을 중단한다.
2. 누락된 파일 목록을 기록한다.
3. `halt_reason_code: MEMORY_FILE_MISSING`을 기록한다.
4. 누락 파일 생성 또는 보강을 위한 `recovery_plan`을 작성한다.
5. 사용자 승인 또는 지시 전에는 원고 작성을 진행하지 않는다.
