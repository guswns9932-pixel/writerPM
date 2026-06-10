# change_log - 사각지대

설정, 문체, 원고, canon 변경 이력을 기록한다. 사용자가 승인하지 않은 변경은 `proposed` 또는 `pending_user_approval` 상태로만 남긴다.

## 기록 규칙

- 원고 final 파일은 덮어쓰지 않는다.
- canon 변경은 승인 전 `canon_change_request`에 먼저 기록한다.
- 문체/설정/원고 변경은 변경 이유와 영향 범위를 함께 기록한다.
- 사용자 요청 범위 밖의 다음 회차 또는 설정 변경을 임의로 진행하지 않는다.

## 변경 이력

| date | change_id | category | target_file | summary | reason | approval_status | related_request |
|---|---|---|---|---|---|---|---|
| 2026-06-09 | CHG-001 | project_setup | `projects/blindspot/*` | 사각지대 프로젝트 기본 기억 파일 및 1~4화 예시 산출물 구성 | workspace 샘플 프로젝트 운영 | recorded | initial workspace setup |
| 2026-06-09 | CHG-002 | canon_request | `canon_change_requests/canon_change_request_20260609_001.md` | 시선 감지 핵심 판정 기준 명문화 요청 | 능력 만능화/오해 방지 | pending_user_approval | canon change request |
