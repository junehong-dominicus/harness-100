# 모니터링 및 운영 설정 보고서 (Phase 4)

**담당**: monitor-operator
**참조**: [selector-generator](../../.agent/skills/selector-generator/SKILL.md)

---

## 1. 수집 스케줄링 (Scheduling)
- **주기**: 매주 월요일 오전 02:00 (KST)
- **방식**: `cron` 작업 등록 또는 Python `schedule` 팝업 라이브러리 활용.

## 2. 상태 모니터링 (Health Check)
- **성공률 지표**: (수집 시도 횟수 / 실제 데이터 추출 성공 횟수)
- **임계값**: 성공률 90% 미만 시 경고 알림.

## 3. 사이트 구조 변경 감지 (`Change Detection`)
- 핵심 데이터(예: 제품 사양 테이블)의 CSS 선택자가 데이터를 찾지 못할 경우 이메일/Slack 알림 발송.
- `selector_health` 리포트 정기 생성.

## 4. 통합 실행 가이드 (`main.py`)
- 모든 컴포넌트(Crawler -> Parser -> Storage)를 순차적으로 실행하는 파이프라인 스크립트 구축.
- `python _workspace/src/main.py --target sst` 명령어로 개별 실행 지원.
