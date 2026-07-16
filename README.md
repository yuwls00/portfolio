# 📜 정유진 포트폴리오

> AI가 지식노동을 대체하는 흐름을 직접 체감하고, 변화를 만드는 쪽으로 방향을 튼 6개월의 기록

## 👋 Intro

안녕하세요, 정유진입니다.

변리사 시험을 준비하며 신청서·보정서 등 정형화된 문서를 작성하는 과정에서,
AI가 이런 지식노동의 상당 부분을 대체할 수 있다는 걸 직접 체감했습니다.
시장이 바뀌기를 기다리기보다 그 변화를 만드는 쪽에 서기로 결정해,
**AI Agent를 활용한 디지털 미디어 콘텐츠 Innovator** 과정(2025.12.31 ~ 2026.07.13)을
수료하며 FastAPI · LangGraph · Supabase · React를 아우르는 풀스택 AI 서비스 개발
역량을 쌓았습니다.

5일 → 3주 → 6주로 이어진 세 번의 팀 프로젝트를 거치며,
매 프로젝트마다 백엔드 핵심 로직부터 AI 파이프라인, 프론트엔드까지
직접 부딪히며 해결한 과정을 아래에 정리했습니다.

---

## 📝 Projects

### 1. 🐍 LAST.PY Studio (YouTube Shorts Script Generator)

> AI 기반 유튜브 쇼츠 대본 자동 생성기 *(KDT 과정 - 7인 팀 프로젝트)*

- 개발기간: 2026.01.29 ~ 02.04 (5일)
- 핵심 역할: Backend / 한-영-한(KO-EN-KO), 한-한(KO-KO) 듀얼 파이프라인 구현
- Language: Python
- Skill: Streamlit, Ollama(Gemma3), Tavily API

**담당 파이프라인**

사용자의 한국어 주제를 영문 키워드로 변환해 글로벌 트렌드 데이터를 수집하고,
UI에는 한국어 제목을, 내부 로직에는 영어 원문을 별도로 유지하는 이원화 구조(표준모델)를
설계·구현했습니다. 이후 단일 LLM이 국내 신조어 처리 시 기존 영어 맥락과 충돌하는 한계를
발견해, 번역 단계를 제거한 한-한 직통형 모델(A모델)의 코드 구현을 맡아 진행했습니다.

**트러블슈팅**

'두쫀쿠', '시고르자브종' 같은 국내 신조어 키워드가 영어 초안과 충돌하며 처리 한계를 보이는 문제를,
표준모델(글로벌 정보량)과 A모델(국내 트렌드 정확도) 듀얼 엔진 구조로 분리해 해결했습니다.

- [코드 저장소](https://github.com/yuwls00/LAST.PY-STUDIO)
- [기획서/발표자료](https://drive.google.com/drive/folders/1NabFtlnwVmDnkEerd8WlIdXDiRrxPwu4?usp=sharing)
- [데모 영상 (YouTube)](https://youtu.be/U1tPd7Vfxj8)

---

### 2. 📰 덜읽더알: K-ENT 뉴스 브리핑

> K-엔터테인먼트 뉴스 요약·분석 브리핑 시스템 *(KDT 과정 - 8인 팀 프로젝트)*

- 개발기간: 2026.04.07 ~ 04.28 (3주)
- 핵심 역할: RAG 기반 인사이트 분석 · 타임라인 · TTS 음성 브리핑(STEP2 전 영역) 단독 구현,
  최종 PDF 보고서 생성 기능 메인 개발
- Language: Python
- Skill: LangGraph, ChromaDB, Ollama(Gemma3), Naver API, Edge-TTS, ReportLab

**담당 기능**

수집·정제된 뉴스 데이터를 벡터화(ChromaDB)해 LangGraph 기반 RAG 파이프라인을 구축하고,
과거-현재 뉴스를 연결하는 인사이트와 아티스트별 타임라인(네이버 API 연동)을 생성했습니다.
이후 완성된 분석 결과를 텍스트 브리핑 및 Edge-TTS 음성 파일로 변환하는 기능까지 전체를
단독으로 구현했으며, 최종 산출물인 PDF 보고서 생성 기능도 메인으로 개발했습니다.

**트러블슈팅**

ChromaDB 임베딩 기반 유사 기사 추천 기능 개발 중, 유사도가 100%에 가까울수록
좋은 추천일 것이라는 초기 가정과 달리 유사도가 지나치게 높으면 단순 중복 기사만
검색되는 문제를 발견했습니다. 유사도 30~75% 구간으로 타겟팅 범위를 재조정해,
단순 반복이 아닌 맥락이 연결되는 과거 뉴스를 발굴하도록 다수 수정했습니다.

- [팀 프로젝트 저장소 (Fork)](https://github.com/yuwls00/RLKM)
- [기획서/발표자료](https://drive.google.com/drive/folders/1RgAi3Oeoco-01-0M1hCUmqHnFfWQjZR-?usp=sharing)
- [데모 영상 (YouTube)](https://youtu.be/g4QdUihR5gs)

---

### 3. 🏭 FactoFit (팩토핏)

> 제조업 설비투자 의사결정 지원 AI 플랫폼 *(KDT 과정 - 5인 팀 프로젝트, 산업통상자원부 공공데이터 활용 공모전)*

- 개발기간: 2026.06.01 ~ 07.13 (약 6주)
- 핵심 역할: ROI·정책 매칭·신청서 작성 핵심 로직 초기 구현, AI 어드바이저 탭 및
  안전점검 기능 UI/백엔드 풀스택 개발
- Language: Python, TypeScript
- Skill: FastAPI, LangGraph, Supabase, React

**담당 기능**

- **핵심 로직 초기 구현**: ROI 분석, 정책 매칭, 신청서 작성 관련 핵심 함수의 초기 버전을
  직접 설계·구현했습니다.
- **AI 어드바이저 탭**: LangGraph 기반 AI 에이전트가 사용자 요청에 따라 기능을 실행하는
  화면을 UI부터 백엔드까지 전체 구현했습니다.
- **안전점검 관리 기능**: 안전점검 PDF 등록, 향후 관리계획 코멘트 작성·저장 기능을 만들고,
  저장된 내용이 최종 신청서 PDF 보고서에 자동 반영되도록 UI부터 백엔드(Supabase 기반
  CRUD 7개 엔드포인트)까지 전체 흐름을 완성했습니다.

**트러블슈팅**

- *법적 리스크 판단*: 초기에는 법정점검 항목 전체를 시스템이 직접 체크하는 방향이었으나,
  항목이 방대하고 설비 관련 법적 문제 발생 시 시스템이 이를 법적으로 커버하기 어렵다고
  판단했습니다. 사용자가 직접 점검 자료를 업로드·저장하고, 신청서 작성 시 코멘트를
  남기는 방식으로 방향을 전환해 법적 리스크를 줄였습니다.
- *에이전트 구현 난이도*: LangGraph 기반 AI 에이전트 구현 자체의 난이도가 높아,
  LLM의 응답 범위를 팩토핏 관련 내용으로 제한(스코프 축소)해 구현 복잡도를 낮췄습니다.

- [팀 프로젝트 저장소 (Fork)](https://github.com/yuwls00/facto-fit)
- [배포 사이트](https://www.facto-fit.co.kr/)
- [기획서/발표자료](https://drive.google.com/drive/folders/1a51VqiXfIl4Lu6Tj7uGLcYebAA-KkQyh?usp=sharing)
- [데모 영상 (YouTube)](https://www.youtube.com/watch?v=wtUz1oLxWTY)

---

## 🏆 그 외 도전 이력

코드 구현 없이 기획서로 참여한 공모전/해커톤입니다.

- **드림릴레이 (기브아이즈)** — 제8회 KDT 해커톤 *(예선 결과 대기 중)*
  AI Vision·QR·해시체인 기반 기부물품 배송 투명성 검증 서비스 기획

- **우성(牛星)** — 농림축산식품부 공공데이터 활용 창업경진대회
  한우 농가 출하 의사결정 지원 AI 플랫폼 기획
  [자료 보기](https://oosungai-4napsqbt.manus.space/)

- **충북채움** — 충북 지역 공모전
  유휴공간(폐가·창고 등) 활용 AI 시뮬레이션 및 지자체 대시보드 서비스 기획

---

## 📞 Contact

- 이메일: yuwls098@gmail.com
- GitHub: https://github.com/yuwls00
