# Project Discontinuation Report Template

`RECOVERY_HARNESS.md`의 "프로젝트 전체 중단 절차"에 따라 프로젝트를 완전히 중단할 때 작성합니다. 개별 회차 issue는 이 템플릿이 아니라 `recovery_plan_template.md`를 사용합니다.

## 기본 정보

- project_id: example_project
- title:
- decision_date: YYYY-MM-DD
- last_completed_stage:
- user_confirmation: confirmed / not_recorded / pending

## 중단 사유

- discontinuation_reason:
- 관련 근거(run_report, quality_trend_log, 사용자 발언 등):

## salvaged_learnings

이번 프로젝트에서 얻어 harness/prompt/template에 실제로 반영한 규칙이나 교훈을 적습니다. 없으면 "없음"으로 표시합니다.

-

## 별도로 발견된 프로세스 이슈 (있는 경우)

-

## preserved_artifacts

- git 커밋 참조:
- 그 외 보존 위치:

## 완료 조건

- [ ] 위 salvaged_learnings에 적은 harness/prompt 변경이 실제 파일에 반영되었다.
- [ ] 이 보고서를 프로젝트 폴더 삭제/정리 전에 커밋했다.
