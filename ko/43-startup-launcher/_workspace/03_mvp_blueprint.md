# MVP 설계 보고서 (Phase 2-3)

**담당**: mvp-architect
**참조**: [startup-launcher](../../.agent/skills/startup-launcher/SKILL.md)

---

## 1. MVP 핵심 기능 (Must-Have)

1. **Self-Hosted LLM Connector**: 기업 내부 서버에 Llama 3 / Mistral 등 오픈소스 모델을 원클릭으로 배포 및 구동.
2. **Secure RAG (Retrieval-Augmented Generation)**: 내부 문서(PDF, Markdown, Word)를 외부 유출 없이 벡터화하여 답변에 활용.
3. **Admin Dashboard**: 조직 내 AI 사용량 모니터링 및 데이터 접근 권한 관리.
4. **Agentic API**: 기존 레거시 시스템(ERP, CRM)과 연동하여 특정 업무를 자동 수행하는 에이전트 인터페이스.

## 2. 기술 스택 (Technical Stack)

- **AI Engine**: vLLM / Ollama (최적화된 추론 서비스)
- **Framework**: LangChain / LlamaIndex (RAG 구현)
- **Frontend**: Next.js (Dashboard 및 채팅 UI)
- **Backend**: FastAPI (고성능 요청 처리)
- **Vector DB**: Chroma / PGVector (On-premise 설치 가능)
- **Security**: Docker / Kubernetes (Air-gapped 환경 지원)

## 3. 로드맵 (8-Week MVP)

- **Week 1-2**: 핵심 AI 추론 엔진 및 내부 문서 파이프라인 구축.
- **Week 3-4**: 웹 기반 대시보드 및 채팅 인터페이스 개발.
- **Week 5-6**: 사용자 권한 및 데이터 보안 레이어 적용.
- **Week 7-8**: 폐쇄망 설치 테스트 및 품질 검증.

---

## 4. 결론
MVP 단계에서는 "데이터 보안"과 "RAG 성능"에 100% 집중하며, 복잡한 기능보다는 **"우리 데이터가 정말 안전하게 분석되는가?"**를 증명하는 데 주력함.
