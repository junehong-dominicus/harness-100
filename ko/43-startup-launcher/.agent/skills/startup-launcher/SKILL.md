---
name: startup-launcher
description: "스타트업 런칭의 아이디어 검증, 비즈니스 모델 설계, MVP 기획, 피치덱 작성을 에이전트 팀이 협업하여 한 번에 생성하는 풀 런칭 파이프라인. '스타트업 기획해줘', '사업 아이디어 검증', '비즈니스 모델 만들어줘', '피치덱 작성해줘', 'MVP 설계해줘', '투자 유치 준비', '창업 준비', '사업계획서 작성', '스타트업 런칭 전략', 'BM 설계' 등 스타트업 런칭 전반에 이 스킬을 사용한다. 기존 비즈니스 모델이나 MVP가 있는 경우에도 피치덱 작성이나 시장 검증을 지원한다. 단, 법인 설립 절차, 실제 투자 계약서 작성, 코드 개발, 회계/세무 처리는 이 스킬의 범위가 아니다."
---

# Startup Launcher — 스타트업 런칭 풀 파이프라인

아이디어 검증→비즈니스 모델→MVP→피칭→투자 유치를 에이전트 팀이 협업하여 한 번에 생성한다.

## 에이전트 구성

| 에이전트 | 파일 | 역할 | 타입 |
|---------|------|------|------|
| market-analyst | `./agents/market-analyst.md` | 시장 검증, TAM/SAM/SOM, 경쟁 분석 | general-purpose |
| business-modeler | `./agents/business-modeler.md` | BMC, 수익 모델, 유닛 이코노믹스 | general-purpose |
| mvp-architect | `./agents/mvp-architect.md` | 기능 우선순위, 기술 스택, 로드맵 | general-purpose |
| pitch-creator | `./agents/pitch-creator.md` | 피치덱, 스토리라인, Q&A 대비 | general-purpose |
| launch-reviewer | `./agents/launch-reviewer.md` | 일관성 검증, 투자 준비도 평가 | general-purpose |

... (중략) ...

## 에이전트별 확장 스킬

에이전트의 도메인 전문성을 강화하는 확장 스킬:

| 스킬 | 파일 | 대상 에이전트 | 역할 |
|------|------|-------------|------|
| unit-economics-calculator | `../unit-economics-calculator/SKILL.md` | business-modeler, pitch-creator | LTV/CAC/BEP 공식, 비즈니스 모델별 벤치마크, 3개년 예측 프레임워크 |
| pitch-deck-framework | `../pitch-deck-framework/SKILL.md` | pitch-creator, launch-reviewer | 10-슬라이드 구조, 슬라이드별 작성 가이드, Q&A TOP 10, 품질 체크리스트 |
