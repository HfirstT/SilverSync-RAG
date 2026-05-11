# 🏥 SilverSync RAG System

**SilverSync**는 간호 현장에서 수집된 환자 데이터와 실시간 활력 징후(Vital Signs)를 기반으로, AI(Gemma 4b)가 적절한 응급 조치 및 진료 지침을 제공하는 의료 보조 RAG(Retrieval-Augmented Generation) 시스템입니다.

---

## 🚀 Key Features
- **Vector Search Optimization**: Supabase `pgvector`와 `HNSW` 인덱스 전략을 활용한 고속 벡터 검색.
- **Data Isolation Strategy**: 대용량 DUR 데이터를 배제하고 의료 지침(PDF/JSON)만 추출하는 `VIEW` 기반 검색 최적화.
- **Natural Language Query**: 사용자의 질문에 대해 로컬 LLM(Ollama: Gemma 4b)이 지침 기반의 신뢰도 높은 답변 생성.
- **MongoDB-Style Output**: 검색 결과를 익숙한 JSON 객체 형태로 가공하여 제공.

## 🛠 Tech Stack
- **Language**: Python 3.10+
- **Database**: Supabase (PostgreSQL + pgvector)
- **Embedding**: HuggingFace (`jhgan/ko-sroberta-multitask`)
- **LLM**: Ollama (`gemma:4b`)
- **Environment**: PyCharm, Windows PowerShell

## 📂 Project Structure
```text
SilverSync-RAG/
├── superbaseDB 설정/       # Supabase 초기화 및 임베딩 로직
├── mongoDB 설정/           # 기존 데이터 전환 및 테스트 스크립트
    └── ss_service_2.py           # 핵심 RAG 엔진 및 검색 함수
├── data_plus/              # 심부전 등 주요 진료지침 (JSON)
├── requirements.txt        # 의존성 패키지 목록
└── README.md               # 프로젝트 가이드
```
## ⚙️ How to Run
## 의존성 설치
- pip install -r requirements.txt

## .env 파일을 생성하고 아래 정보를 입력합니다.
- SUPABASE_URL=your_supabase_url
- SUPABASE_KEY=your_supabase_anon_key

## Ollama 실행
ollama run gemma:4b
 
## 서비스 가동
python ss_service.py
