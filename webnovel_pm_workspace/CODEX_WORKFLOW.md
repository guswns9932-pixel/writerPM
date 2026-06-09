# CODEX_WORKFLOW.md

이 문서는 Codex가 이 repository에서 한국 웹소설 제작 작업을 수행할 때 따라야 하는 표준 workflow입니다.

## 공통 원칙

- Codex는 사용자가 명시한 범위만 수행합니다.
- Codex는 사용자 승인 없이 다음 회차, 다음 배치, 추가 수정, 설정 변경을 진행하지 않습니다.
- 모든 결과물은 파일로 저장합니다.
- 작업 후에는 반드시 수행 내용, 변경 파일, 검수 결과, 사용자 확인 필요 사항, 다음 가능한 작업을 보고합니다.
- 원고 작성 전에는 `story_bible`, `character_bible`, `ability_rules`, `canon_log`, `timeline`, `foreshadowing_ledger`, `style_guide`, `rolling_context` 역할의 문서를 확인합니다.

## 1. 새 작품 시작 절차

1. 사용자 요청 범위를 확인합니다.
2. `webnovel_pm_workspace/projects/{project_id}/brief.md`에 작품 목표, 장르, 타깃 독자, 금지 요소를 정리합니다.
3. 필요한 경우 `webnovel_pm_workspace/projects/{project_id}/story_bible.json`의 `current_stage`와 회차별 `episode_XXX_status.md`에 사용자 승인 필요 여부를 기록합니다.
4. 아직 원고를 작성하지 않습니다.
5. 다음 가능한 작업을 보고합니다.

## 2. 컨셉 후보 생성 절차

1. 사용자가 별도 개수를 지정하지 않으면 컨셉 후보는 기본 3개만 생성합니다.
2. 각 후보에는 다음 항목을 포함합니다.
   - 임시 제목
   - 장르
   - 로그라인
   - 핵심 재미
   - 차별점
   - 1화 후킹 방향
   - 장기 연재 가능성
   - 모방 위험 점검
3. 후보는 `webnovel_pm_workspace/projects/{project_id}/episodes/concept_candidates.md` 또는 프로젝트별 concept 파일에 저장합니다.
4. Codex는 사용자가 선택하거나 추가 지시하기 전까지 특정 후보로 작품 Bible을 확정하지 않습니다.

## 3. 작품 Bible 생성 절차

사용자가 컨셉을 선택하거나 작품 Bible 생성을 지시하면 다음 문서를 생성 또는 보강합니다.

1. `story_bible`
   - 작품 핵심 전제
   - 장르 약속
   - 핵심 갈등
   - 장기 목표
2. `character_bible`
   - 주요 인물 프로필
   - 욕망과 결핍
   - 관계 변화
   - 말투와 행동 원칙
3. `ability_rules`
   - 능력, 시스템, 직업, 조직 규칙
   - 가능/불가능 범위
   - 대가와 제약
4. `canon_log`
   - 확정 설정
   - 변경 이력
   - 사용자 승인 여부
5. `timeline`
   - 본편 이전 사건
   - 회차별 사건 순서
6. `foreshadowing_ledger`
   - 복선 ID
   - 첫 등장 회차
   - 회수 예정
   - 상태
7. `style_guide`
   - 문체
   - 대사 톤
   - 금지 표현
   - 회차 엔딩 규칙
8. `rolling_context`
   - 현재까지의 줄거리
   - 미해결 갈등
   - 유지해야 할 감정선

작품 Bible 생성 후에는 사용자 검토 대기 상태로 정리합니다.

## 4. 1화 작성 절차

1. 사용자 요청이 1화 작성 범위를 포함하는지 확인합니다.
2. 원고 작성 전 필수 확인 문서를 검토합니다.
3. 누락된 필수 문서가 있으면 원고를 final로 저장하지 않고 누락 사항을 보고합니다.
4. `webnovel_pm_workspace/projects/{project_id}/episodes/episode_001_outline.md`에 1화 개요를 정리합니다.
5. 1화 초안을 작성합니다.
6. 각 장면에 다음 요소가 있는지 확인합니다.
   - 초반 후킹
   - 주인공의 선택
   - 독자 보상
   - 클리프행어
7. 초안은 draft 파일로 저장합니다.
8. final 저장 전 반드시 1화 검수 절차를 수행합니다.

## 5. 1화 검수 절차

1. 설정 충돌 여부를 확인합니다.
2. 능력 규칙 위반 여부를 확인합니다.
3. 인물 붕괴 여부를 확인합니다.
4. 시간선 오류 여부를 확인합니다.
5. 문체가 `style_guide`와 일치하는지 확인합니다.
6. 후킹, 주인공 선택, 독자 보상, 클리프행어가 포함되었는지 확인합니다.
7. 특정 기존 작품의 고유 설정, 고유 용어, 대표 장면, 특정 작가 문체를 모방하지 않았는지 확인합니다.
8. 검수 결과를 review 파일에 저장합니다.
9. 문제가 있으면 revision_note를 남기고 수정 가능 범위를 보고합니다.
10. critical issue가 있으면 final로 저장하지 않고 중단 절차를 따릅니다.

## 6. 사용자 피드백 반영 절차

1. 사용자 피드백을 `user_feedback_log`에 기록합니다.
2. 사용자가 "바로 반영"이라고 명시했는지 확인합니다.
3. "바로 반영"이 명시되지 않았다면 `feedback_application_plan`을 먼저 작성합니다.
4. 피드백이 canon 변경을 요구하는지 확인합니다.
5. canon 변경이 필요하면 `canon_change_request`를 작성하고 사용자 승인 전에는 반영하지 않습니다.
6. 피드백 반영 후 revision_note와 run_report를 남깁니다.
7. 한 회차 자동 수정은 기본 1회만 수행합니다.
8. 추가 수정이 필요하면 revision_note를 남기고 사용자 지시를 기다립니다.

## 7. 1화 승인 후 3화 단위 추가 작성 절차

1. `APPROVAL_LOG.md`에서 1화 final 승인 여부를 확인합니다.
2. 승인 기록이 없으면 2화 이후 본문을 작성하지 않습니다.
3. 사용자가 요청한 배치 범위를 확인합니다.
4. 기본 배치 단위는 3화입니다.
5. 예시 배치:
   - 2~4화
   - 5~7화
   - 8~10화
6. 각 회차마다 outline, draft, review, revision_note, run_report, episode_XXX_status.md를 작성합니다.
7. 배치 완료 후 다음 배치로 넘어가지 않습니다.
8. 반드시 사용자 검토 대기 상태로 정리합니다.

## 8. 설정 충돌 발생 시 중단 절차

설정 충돌, 능력 규칙 위반, 인물 붕괴, 시간선 오류가 발견되면 다음 순서로 중단합니다.

1. final 저장을 중단합니다.
2. 문제 유형을 기록합니다.
3. 관련 파일과 충돌 지점을 기록합니다.
4. `halt_reason_code`를 작성합니다.
5. `recovery_plan`을 작성합니다.
6. 사용자에게 승인 또는 방향 선택을 요청할 항목을 정리합니다.
7. 사용자 승인 전에는 충돌 해결을 canon에 반영하지 않습니다.

## 9. canon 변경 요청 절차

1. 변경하려는 canon 내용을 식별합니다.
2. 기존 canon과 충돌하는 지점을 기록합니다.
3. 변경 이유와 장단점을 정리합니다.
4. `canon_change_request`를 작성합니다.
5. 사용자 승인 전에는 원고, Bible, canon_log에 변경을 확정 반영하지 않습니다.
6. 사용자가 승인하면 canon_log에 승인 일자와 변경 내용을 기록합니다.
7. 관련 Bible, timeline, foreshadowing_ledger, rolling_context를 갱신합니다.

## 10. critical issue 발생 시 recovery plan 작성 절차

critical issue 예시는 다음과 같습니다.

- 사용자 승인 없는 작업 범위 초과
- 기존 final 파일 덮어쓰기 위험
- 설정 충돌
- 능력 규칙 위반
- 인물 붕괴
- 시간선 오류
- 특정 작품 또는 작가 문체 모방 위험

발생 시 다음 항목을 포함해 recovery plan을 작성합니다.

1. `halt_reason_code`
2. 문제 요약
3. 영향 범위
4. 관련 파일
5. 안전하게 되돌릴 수 있는 방법
6. 사용자에게 필요한 결정
7. 재개 가능한 최소 작업 단위

## 11. 각 작업 후 Codex가 보고해야 할 내용

작업 완료 후 Codex는 `REPORT_FORMAT.md` 형식에 맞춰 다음 내용을 보고합니다.

- 수행한 작업
- 생성한 파일
- 수정한 파일
- 검수 결과
- 설정 충돌 여부
- 품질 이슈 여부
- 사용자 확인 필요 사항
- 다음 가능한 작업
