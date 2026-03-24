# 데이터 저장 설계 보고서 (Phase 3)

**담당**: data-manager

---

## 1. 저장 매체 선정
- **파일 포맷**: `JSONL` (JSON Lines) - 대용량 데이터 스트리밍 저장 용이.
- **최종 데이터베이스**: `SQLite` - 모니터링 애플리케이션 및 검색 인덱싱에 적합한 가벼운 관계형 DB.

## 2. 데이터베이스 스키마 (`modbus_specs.db`)
- **Table: `products`**
  - `id`: INTEGER PRIMARY KEY
  - `name`: TEXT
  - `brand`: TEXT (SST, Amazon, RobotShop 등)
  - `category`: TEXT
  - `source_url`: TEXT UNIQUE
  - `collected_at`: TIMESTAMP
- **Table: `spec_details`**
  - `product_id`: INTEGER (FK)
  - `spec_key`: TEXT
  - `spec_value`: TEXT

## 3. 내보내기 전략 (Export)
- 정기적으로 `CSV` 및 `Excel` 형식으로 변환하여 보고서 활용도 제고.
- `MarketMirror_Report_YYYYMMDD.csv` 형식으로 저장.

## 4. 데이터 정합성 검사
- `source_url` 기반 중복 수집 방지 (Upsert 로직 적용).
- 필수 필드(`name`, `source_url`) 누락 시 경고 발생.
