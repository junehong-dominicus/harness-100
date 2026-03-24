---
name: web-scraper
description: "웹 스크래핑 시스템을 에이전트 팀이 협업하여 구축하는 풀 파이프라인. '웹 스크래핑 만들어줘', '크롤러 개발해줘', '사이트 데이터 수집', '웹 크롤링 시스템', '스크래퍼 구축', '데이터 수집 자동화', '사이트 파싱', '웹 데이터 추출' 등 웹 스크래핑 시스템 구축 전반에 이 스킬을 사용한다. 특정 사이트 분석만 필요한 경우에도 대상분석 모드로 지원한다. 단, 실시간 스트리밍 데이터 처리(Kafka/Flink), 브라우저 자동화 테스트(Selenium 테스트), 웹사이트 성능 모니터링은 이 스킬의 범위가 아니다."
---

# Web Scraper — 웹 스크래핑 시스템 구축 파이프라인

웹 스크래핑 시스템의 대상분석→크롤러설계→파싱→저장→모니터링을 에이전트 팀이 협업하여 구축한다.

## 에이전트 구성

| 에이전트 | 파일 | 역할 | 타입 |
|---------|------|------|------|
| target-analyst | `./agents/target-analyst.md` | 대상 사이트 분석, 리스크 평가 | general-purpose |
| crawler-developer | `./agents/crawler-developer.md` | 크롤러 아키텍처 및 구현 | general-purpose |
| parser-engineer | `./agents/parser-engineer.md` | 파싱 로직 설계 및 구현 | general-purpose |
| data-manager | `./agents/data-manager.md` | 데이터 저장·검증·내보내기 | general-purpose |
| monitor-operator | `./agents/monitor-operator.md` | 모니터링·알림·스케줄링 | general-purpose |

... (중략) ...

## 에이전트별 확장 스킬

에이전트의 도메인 전문성을 강화하는 확장 스킬:

| 스킬 | 파일 | 대상 에이전트 | 역할 |
|------|------|-------------|------|
| anti-bot-analyzer | `../anti-bot-analyzer/SKILL.md` | target-analyst, crawler-developer | 안티봇 방어 계층 분류, 감지 플로우, Rate Limit 공식, 법적 리스크 체크 |
| selector-generator | `../selector-generator/SKILL.md` | parser-engineer, monitor-operator | CSS/XPath 선택자 생성, 견고성 점수, 변경 감지 패턴, 데이터 정제 |
