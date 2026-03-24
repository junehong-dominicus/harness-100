---
name: selector-generator
description: "웹 페이지 데이터 추출을 위한 CSS/XPath 선택자를 체계적으로 생성하고 검증하는 스킬. '선택자 만들어줘', 'CSS 선택자', 'XPath 작성', '데이터 추출 패턴', '파싱 규칙' 등 선택자 설계 시 사용한다. 단, 브라우저 DevTools 직접 조작은 이 스킬의 범위가 아니다."
---

# Selector Generator — CSS/XPath 선택자 생성 + 검증

parser-engineer의 선택자 작성 역량을 강화하는 스킬.

... (중략: 이미 읽은 상세 내용) ...

## 선택자 전략 우선순위

1. **고유 ID**: `#product-price`
2. **data-* 속성**: `[data-testid="price"]`
3. **시맨틱 클래스**: `.product-price`
...
