---
name: anti-bot-analyzer
description: "웹사이트의 안티봇 방어 메커니즘을 분석하고 합법적 우회 전략을 수립하는 스킬. '안티봇 분석해줘', '봇 차단 우회', 'Cloudflare 대응', '캡차 감지', 'rate limit 확인' 등 안티봇 분석 시 사용한다. 단, 불법적 우회 도구 개발, CAPTCHA 자동 풀이 서비스, 개인정보 침해 스크래핑은 이 스킬의 범위가 아니다."
---

# Anti-Bot Analyzer — 안티봇 방어 분석 + 합법적 대응

target-analyst와 crawler-developer의 안티봇 분석 역량을 강화하는 스킬.

... (중략: 이미 읽은 상세 내용) ...

## 안티봇 방어 계층 분류

| 방어 | 감지 방법 | 대응 전략 |
|------|----------|----------|
| robots.txt | `GET /robots.txt` | 규칙 준수 (Crawl-delay, Disallow) |
| User-Agent 필터 | 403/429 응답 | 실제 브라우저 UA 헤더 설정 |
...
