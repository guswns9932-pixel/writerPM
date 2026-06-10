# context_compression_log

프로젝트에서 rolling_context.md가 압축될 때마다 기록하는 이력 파일.
세션 재시작 시 압축 상태를 확인해 Cold Start 프로토콜 실행 여부를 판단한다.

---

## 기본 정보

- **project_id**: {{project_id}}
- **마지막 업데이트**: YYYY-MM-DD
- **관련 harness**: CONTEXT_COMPRESSION_HARNESS.md

---

## 압축 이력 표

| compression_id | triggered_at_episode | arc_compressed | what_was_preserved | what_was_summarized | what_was_dropped | compressed_by | verified_by |
|---|---|---|---|---|---|---|---|
| COMP001 | EP000 | ARC000 | 시리즈 요약 3문장, 현재 arc 상세, 캐릭터 현재 상태, 열린 갈등, 미회수 복선 | EP001~EP020 상세 내용 → arc_000_summary.md로 이동 | 해소된 갈등, 완료된 복선, 배경 설명 반복분 | AI | 미확인 |

---

## 현재 활성 컨텍스트 계층 (Current Active Context Tier)

### Tier 1 — Hot (rolling_context.md에 현재 포함된 내용)

- **현재 arc**: {{arc_id}}
- **포함 화수 범위**: EP{{시작}} ~ EP{{현재}}
- **파일 크기 추정**: 약 {{N}}자
- **마지막 압축 이후 경과 화수**: {{N}}화

#### rolling_context.md 현재 포함 항목

- [ ] 시리즈 전체 요약 (3문장)
- [ ] 완료된 arc 목록 (arc별 1줄 요약 + arc_summary 파일 참조)
- [ ] 현재 arc 회차별 상세 요약
- [ ] 주요 인물 현재 상태
- [ ] 활성 갈등 목록
- [ ] 미회수 복선 (critical 한정)
- [ ] 직전 화 감정선 및 다음 화 유지 정보

### Tier 2 — Warm (arc 요약 파일 목록)

완료된 arc의 요약 파일. 필요 시 참조. 평소 전문 로딩 불필요.

| arc_id | arc_name | 에피소드 범위 | 요약 파일 경로 |
|---|---|---|---|
| ARC001 | {{arc_name}} | EP001~EP020 | `projects/{{project_id}}/arc_001_summary.md` |

### Tier 3 — Cold (원고 파일 아카이브)

개별 화 원고. 정밀 검수, 표현 재확인, deep-dive 시에만 참조.

- 위치: `projects/{{project_id}}/episodes/`
- 평소 세션에서 전체 로딩 금지

### Tier 4 — Permanent (항상 신선하게 읽는 파일)

세션 시작 시 반드시 읽는 파일. 압축 대상 아님.

- `AGENTS.md`
- `story_bible.json`
- `character_bible.json`
- `ability_rules.json`
- `thematic_compass.json`
- `arc_canon_snapshot` (최신본)
- `rolling_context.md`
- `approval_state.json`
- `final_registry.json`

---

## 압축 후 검증 체크리스트

압축 완료 후 다음 항목을 반드시 확인한다. 미확인 시 다음 원고 작성 진행 금지.

### 필수 사실 spot-check (3개 이상)

압축 전 rolling_context에서 랜덤으로 3개 이상의 canon 사실을 선택해 압축 후 컨텍스트에서 여전히 접근 가능한지 확인한다.

| 확인 사실 | 압축 전 출처 | 압축 후 접근 경로 | 확인 여부 |
|---|---|---|---|
| {{canon 사실 1}} | rolling_context EP{{N}} | arc_summary 또는 Tier4 파일 | ☐ |
| {{canon 사실 2}} | rolling_context EP{{N}} | arc_summary 또는 Tier4 파일 | ☐ |
| {{canon 사실 3}} | rolling_context EP{{N}} | arc_summary 또는 Tier4 파일 | ☐ |

### 체크리스트

- [ ] arc_XXX_summary.md 생성 완료
- [ ] arc_canon_snapshot.json 생성 완료
- [ ] rolling_context.md가 새 구조(시리즈 요약 + arc 1줄 목록 + 현재 arc 상세)로 갱신됨
- [ ] arc_state.json 업데이트 완료
- [ ] foreshadowing_ledger.json 상태 동기화 확인
- [ ] canon 사실 3개 이상 spot-check 통과
- [ ] 이 압축 이력 표에 신규 행 추가 완료

---

## 경고 조건 (Warning Conditions)

다음 중 하나에 해당하면 즉시 압축 또는 사용자 보고 필요:

- rolling_context.md가 15,000자를 초과했다
- 마지막 압축 이후 2개 arc 이상 경과했다
- 세션 재시작 후 Cold Start 프로토콜 없이 작업을 시작하려 한다
- rolling_context.md에 현재 arc 외 이전 arc의 상세 내용이 여전히 포함되어 있다

---

## 메모

{{프로젝트 특이사항, 압축 시 주의점, 특수 구조 등}}
