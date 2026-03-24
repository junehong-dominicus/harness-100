# 크롤러 설계 보고서 (Phase 2-a)

**담당**: crawler-developer
**참조**: [anti-bot-analyzer](../../.agent/skills/anti-bot-analyzer/SKILL.md)

---

## 1. 크롤러 아키텍처 (SST Automation)
- **Engine**: Python 3.x + `httpx` (비동기 처리)
- **Concurrency**: `asyncio` 기반 동시 요청 (최대 3개 동시 연결 제한)
- **Retry Strategy**: 
  - 429 (Too Many Requests): 5분 대기 후 3회 재시도
  - 5xx (Server Error): 지수 백오프 적용
- **User-Agent**: 표준 브라우저 UA 활용하여 차단 방지

## 2. 작업 흐름 (Crawl Flow)
1. **Discovery**: `https://www.sstautomation.com/` 메인 페이지에서 'Products' 메뉴 섹션 파싱.
2. **Filtering**: URL 중 `modbus` 또는 `gateway` 키워드가 포함된 카테고리 페이지 수집.
3. **Product Listing**: 카테고리별 제품 상세 페이지 URL 목록화.
4. **Extraction**: 각 상세 페이지에서 HTML 원본 수집 후 `parser-engineer`에게 전달.

## 3. 구현 사양 (`sst_crawler.py`)
```python
import httpx
import asyncio
from bs4 import BeautifulSoup

class SSTCrawler:
    def __init__(self):
        self.base_url = "https://www.sstautomation.com"
        self.headers = {"User-Agent": "Mozilla/5.0 ..."}
    
    async def fetch_product_urls(self):
        # 제품 목록 수집 로직
        pass

    async def fetch_product_detail(self, url):
        # 제품 상세 HTML 수집 로직
        pass
```

## 4. 안티봇 대응 세부 내역
- **Rate Limit**: 요청 간 `random.uniform(2.0, 5.0)` 초 간격 유지.
- **Header**: `Referer`, `Accept-Language` 헤더 추가하여 실제 브라우저 행동 모사.
