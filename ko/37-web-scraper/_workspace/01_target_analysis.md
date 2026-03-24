# 대상 사이트 분석 보고서 (Phase 1)

**담당**: target-analyst
**참조**: [anti-bot-analyzer](../../.agent/skills/anti-bot-analyzer/SKILL.md)

---

## 1. 대상 사이트 요약 및 난이도 평가

| 사이트 | 유형 | 안티봇 수준 | 주요 데이터 포인트 | 스크래핑 전략 |
|-------|------|-----------|-----------------|-------------|
| **sstautomation.com** | 제조사 | **Level 1 (낮음)** | Modbus 게이트웨이 사양, 매뉴얼 | 직접 파싱 (httpx) |
| **robotshop.com** | 전문 유통 | **Level 2 (중간)** | 가격, 재고, 기술 사양 표 | 세션 유지 + 지연 연구 |
| **amazon.ca** | 종합 마켓 | **Level 3 (매우 높음)** | 가격, 제품 상세, 리뷰 | API 사용 또는 고도화된 우회 |

---

## 2. 사이트별 상세 분석

### A. sstautomation.com (SST Automation)
- **분석 결과**: WordPress 기반 사이트. `robots.txt`상 상품 페이지 차단 없음.
- **기술적 특징**: 정적 HTML 기반 사양 데이터 제공.
- **수집 전략**: `Sitemap.xml`을 추출하여 모든 Modbus 관련 제품 URL 수집 후 정기적으로 기술 사양 테이블 파싱.

### B. robotshop.com (RobotShop)
- **분석 결과**: 표준 e-commerce 플랫폼. 
- **기술적 특징**: 데이터가 탭(Tab) 또는 아코디언 메뉴 내부에 위치할 가능성 높음.
- **수집 전략**: 제품 목록 페이지에서 페이징을 처리하며, 제품 페이지에서 `specification` 섹션의 CSS 선택자를 정밀하게 지정.

### C. amazon.ca (Amazon Canada)
- **분석 결과**: 매우 강력한 WAF(AWS WAF), IP 차단, 행동 분석 적용됨.
- **기술적 특징**: 동적 로딩 및 잦은 UI 변경.
- **리스크**: 이용약관(ToS)에서 자동화된 수집을 금지함.
- **권장 대안**: 공식 **Amazon Product Advertising API** 사용을 강력히 권장. 직접 스크래핑할 경우 Playwright + 고급 프록시 서비스 필수.

---

## 3. 법적 리스크 및 권고 사항
- **robots.txt**: 모든 사이트의 `robots.txt`를 준수하며, `Crawl-delay`가 명시되지 않은 경우에도 최소 3~5초의 간격을 유지할 것.
- **개인정보**: 제품 사양(공공 데이터 성격)만을 수집하므로 개인정보 보호 리스크는 낮음.
- **서버 부하**: 수집 주기를 1일 1회 이하로 설정하여 대상 서버에 부하를 주지 않도록 설계.

## 4. 다음 단계 제언
- **crawler-developer**: sstautomation.com을 우선 타깃으로 하여 프로토타입 크롤러 구현 착수.
- **parser-engineer**: 각 사이트의 `specification` 테이블 구조를 분석하여 `selector-generator` 스킬로 파싱 룰 생성.
