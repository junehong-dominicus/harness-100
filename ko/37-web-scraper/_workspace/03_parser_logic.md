# 파싱 로직 설계 보고서 (Phase 2-b)

**담당**: parser-engineer
**참조**: [selector-generator](../../.agent/skills/selector-generator/SKILL.md)

---

## 1. 타깃 데이터 구조 (Schema)
모든 사이트에서 공통적으로 추출할 데이터 스키마를 정의합니다.

- `product_name`: 제품명 (String)
- `protocol`: 변환 프로토콜 (e.g., Modbus TCP, RTU, CANopen) (List)
- `specifications`: 기술 사양 (Dictionary - Key: Value)
- `manual_url`: 매뉴얼 다운로드 링크 (URL)
- `source_url`: 데이터 출처 (URL)

## 2. SST Automation 파싱 규칙
- **제품명**: `.product-detail-title` 또는 `h1` 태그
- **사양 테이블**: `div.product-spec-table`, `table` 태그 내의 `tr` 순회
- **선택자 견고성 점수**: 85점 (ID 혹은 명확한 클래스 구조 사용 지점 발견)

## 3. 구현 로직 (`parser_utils.py`)
```python
import re
from bs4 import BeautifulSoup

def parse_sst_spec(html_content):
    soup = BeautifulSoup(html_content, 'html.parser')
    specs = {}
    table = soup.find('table', class_='spec-table')
    if table:
        for row in table.find_all('tr'):
            cols = row.find_all('td')
            if len(cols) == 2:
                key = cols[0].text.strip()
                val = cols[1].text.strip()
                specs[key] = val
    return specs
```

## 4. 데이터 정제 (Data Cleaning)
- **단위 통일**: 전압(24VDC), 온도(-40~85°C) 등 단위 기호 표준화.
- **결측치 처리**: 정보가 없는 필드는 `null` 또는 `N/A`로 기록.
