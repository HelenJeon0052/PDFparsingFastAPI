# PDF Query Session API

**FastAPI-based PDF Query/Response Session Demo for Colab and Jupyter Notebook**
**FastAPI 기반 PDF 질의/응답 세션 데모 (Colab / Jupyter Notebook 전용)**

---

## English

### 1. Overview

This project is a lightweight FastAPI-based query/response session API built for demonstration purposes.
It processes extracted PDF text, generates a short response or summary, and stores session history in memory.

The primary goal of this project is to show a minimal but working backend flow:

* PDF text extraction
* Query/response API serving with FastAPI
* Session history tracking
* Simple latency and cache logging
* Notebook-friendly execution

This project is intended to run **only in Google Colab or local Jupyter Notebook / JupyterLab environments**.

---

### 2. Features

* Simple FastAPI server
* Query/response session endpoint
* In-memory session history
* PDF-derived text summary flow
* CSV-based intermediate text handling
* Lightweight benchmark logging
* Notebook-compatible execution

---

### 3. Project Structure

```text
.
├── genai_processors(o).ipynb
├── README.md
```

---

### 4. Requirements

Install the required packages in Colab or Jupyter Notebook:

```bash
pip install fastapi uvicorn pydantic nest-asyncio pyngrok requests
```

If you want to connect a Gemini model:

```bash
pip install google-generativeai
```

---

### 5. Running in Colab / Jupyter Notebook

### 6. Optional: Public Access with ngrok

If you want to expose the notebook-hosted FastAPI server externally in Colab:

```python
from pyngrok import ngrok
public_url = ngrok.connect(8000)
print(public_url)
```

---

### 6. PDF Processing Flow

A typical demo flow is:

1. Extract text from the PDF
2. Save extracted text rows into `PDF_text_only.csv`
3. Read the CSV preview
4. Send a summary prompt
5. Return the generated response through `/query`
6. Store the response in session history

---

### 7. Benchmark Logging

This project can also record simple benchmark information such as:

* cache hit
* latency in milliseconds
* prompt token count
* output token count
* preview of request/response

Example benchmark CSV columns:

```text
id, cache_hit, lat_ms, prompts_tok, out_tok, total_tok, prompt, preview
```

---

### 8. Notes

* This project is designed for **Colab / Jupyter Notebook only**
* Session history is stored **in memory**, so it resets when the runtime restarts
* PDF summaries may become expensive if the prompt is too long
* For demo purposes, use a short preview instead of the full extracted text
* Keeping prompt length small reduces both latency and API cost

---

### 9. Motivation

* basic FastAPI API design
* session-based response handling
* lightweight PDF-to-summary pipeline
* minimal backend logging and observability
* ReportLab : https://github.com/google-gemini/genai-processors/blob/main/notebooks/create_your_own_processor.ipynb

---

## 한국어

### 1. 개요

이 프로젝트는 데모 목적의 **FastAPI 기반 query/response session API**입니다.
PDF에서 추출한 텍스트를 바탕으로 간단한 응답 또는 요약을 생성하고, 세션 이력을 메모리에 저장합니다.

이 프로젝트의 핵심 목적은 다음과 같은 최소한의 백엔드 흐름을 보여주는 것입니다.

* PDF 텍스트 추출
* FastAPI 기반 API 서빙
* 세션 이력 저장
* 간단한 latency / cache 로그 기록
* Notebook 환경 친화적 실행

이 프로젝트는 **Google Colab 또는 로컬 Jupyter Notebook / JupyterLab에서만 실행하는 것을 전제**로 합니다.

---

### 2. 주요 기능

* 간단한 FastAPI 서버
* query/response 세션 엔드포인트
* 메모리 기반 세션 저장
* PDF 텍스트 기반 요약 흐름
* CSV 기반 중간 텍스트 처리
* 가벼운 벤치마크 로그 기록
* Notebook 환경 실행 지원

---

### 3. 프로젝트 구조

```text
.
├── genai_processors(o).ipynb
├── README.md
```

---

### 4. 설치

Colab 또는 Jupyter Notebook에서 아래 패키지를 설치합니다.

```bash
pip install fastapi uvicorn pydantic nest-asyncio pyngrok requests
```

Gemini 모델까지 연결할 경우:

```bash
pip install google-generativeai
```

---

### 5. Colab / Jupyter Notebook 실행 방법

### 6. PDF 처리 흐름

1. PDF에서 텍스트 추출
2. 추출한 텍스트를 `PDF_text_only.csv`에 저장
3. CSV preview 읽기
4. 요약 프롬프트 생성
5. `/query`를 통해 응답 반환
6. 세션 히스토리에 저장

---

### 7. 벤치마크 로그

* cache hit 여부
* 밀리초 단위 latency
* prompt token 수
* output token 수
* 요청/응답 preview

예시 CSV 컬럼:

```text
id, cache_hit, lat_ms, prompts_tok, out_tok, total_tok, prompt, preview
```

---

### 8. 참고 사항

* 이 프로젝트는 **Colab / Jupyter Notebook 전용**입니다
* 세션 이력은 **메모리 저장**이므로 런타임 재시작 시 초기화됩니다
* PDF 요약은 프롬프트가 길어질수록 비용이 커질 수 있습니다
* 데모 목적이라면 전체 텍스트 대신 짧은 preview를 사용하는 것이 좋습니다
* 프롬프트 길이를 줄이면 latency와 API 비용을 함께 줄일 수 있습니다

---

### 9. 제작 의도

* FastAPI 기반 기본 API 설계
* 세션 기반 응답 처리
* 간단한 PDF-to-summary 파이프라인
* 최소한의 백엔드 로깅 / 관측 가능성 확보
* ReportLab : https://github.com/google-gemini/genai-processors/blob/main/notebooks/create_your_own_processor.ipynb
