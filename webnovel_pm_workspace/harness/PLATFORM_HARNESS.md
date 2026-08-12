# PLATFORM_HARNESS

투고 전 플랫폼 약관, AI 생성물 정책, 연령/콘텐츠 정책을 확인하기 위한 문서형 harness입니다.

## 목적

- 플랫폼 정책 확인 누락 방지
- AI 보조 창작물 고지 필요 여부 확인
- 폭력성, 선정성, 혐오 표현, 실제 인물/기관 묘사 리스크 점검
- 투고 전 packaging 단계에서 사용자 확인 사항 정리

## 필수 확인 파일

- `platform_policy_check.md`
- `ai_usage_disclosure_note.md`
- `content_risk_check.md`
- `real_entity_risk_check.md`
- `sensitivity_check.md`
- `rights_log.md`

## 운영 전제

- 이 workspace는 외부 API나 외부 자동화 앱이 아니다.
- Codex는 최신 플랫폼 정책을 임의로 확정하지 않는다.
- 정책은 변할 수 있으므로 실제 투고 전 사용자가 최신 약관을 확인해야 한다.
- Codex는 확인 항목과 리스크를 문서로 정리한다.

## 투고 전 체크리스트

- [ ] 플랫폼 최신 약관 확인 필요 여부를 보고했다.
- [ ] AI 사용 고지 필요 여부를 확인 대상으로 표시했다.
- [ ] 연령 등급 또는 성인물 제한 위험을 확인했다.
- [ ] 폭력성/선정성/혐오 표현 리스크를 확인했다.
- [ ] 실존 인물/기관 유사성 리스크를 확인했다.
- [ ] 표지/소개글/키워드/태그가 플랫폼 리스크를 키우지 않는지 확인했다.

## 중단 조건

- 플랫폼 약관 확인 없이 공개용 최종 packaging을 요구한다.
- AI 고지 필요 여부가 불명확한데 고지 문구 없이 투고본을 확정하려 한다.
- content risk가 높지만 사용자 확인 없이 final packaging을 진행하려 한다.

## 보고 항목

- 확인한 플랫폼
- 확인이 필요한 정책 영역
- AI usage disclosure 필요 여부
- content/platform risk
- 사용자 확인 필요 사항
