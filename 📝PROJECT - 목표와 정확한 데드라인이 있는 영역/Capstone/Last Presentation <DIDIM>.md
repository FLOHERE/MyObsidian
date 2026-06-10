> ai 에게 바라는 요구사항 : 아래 목차 순서대로 ppt를 만들것. pdf에 있는 자료를 바탕으로 ppt를 만들것.
> 다이어그램은 누구나 이해 가능하도록 쉽게 그릴것. 사진이 있다면 반드시 순서대로 그 사진을 어떤 왜곡도 없이 그대로 사용 및 배치 할것.


- PPT 목차
	0. 멤버 소개 : 김건우, 민선규, 이다혜, 조소영
	1. 문제 정의
	2. 프로젝트 개요
	3. 기술 스택
	4. 전체적인 프로젝트 다이어그램
	5. User 플로우 및 어드민
	6. 핵심 기능 소개 - 실제 AI 면접 영상(유튜브 링크)
		1. AI 면접 후 피드백
	7. 추후 개선점 및 소감


# 0. 멤버 소개 : 김건우, 민선규, 이다혜, 조소영
- 김건우 : 프론트 UI/UX 디자인 설계 및 개발
- 민선규 : 프론트엔드 보조
- 이다혜 : PPT 제작 및 문서 작성
- 조소영 : 영상/음성 분석 ai 제작 및 백엔드 개발

# 1. 문제 정의
## 1. 개요 
- **기존 AI 면접 시스템에 대한 한계 극복** : 기존 AI 면접은 마땅한 피드백도 없고, AI 면접 대비시 비용을 내야하는 경우도 있음.
	
- **취업난 심화:** 2025년 기준 대졸 청년 실업률 지속 상승, 구직 활동 평균 기간 11개월. 스펙 준비 외에도 포트폴리오 정리 및 자소서 작성에 많은 시간 낭비.
    
- **기존 서비스의 한계:** 잡코리아, 사람인 등은 단순 공고 중개 수준. LMS 데이터 연동, AI 자소서 변환, 면접 시뮬레이션을 통합 제공하는 서비스 부재.
    
- **AI 기술 활용:** 학과 H100 서버의 Qwen2.5-32B 모델을 활용하여 고품질 AI 서비스를 무료 제공 (비용 절감 및 개인정보 보호).
    
- **LMS 연동 차별화:** 학교 LMS API 연동으로 학생이 별도 입력 없이 포트폴리오 자동 생성 (타 서비스 대비 강력한 핵심 차별점).

# 2. 프로젝트 개요 정보
## 2. 시장 조사 및 타겟 분석

### 2.1 시장 분석

- **AI 채용 시장 규모:** 2026년 약 7.3억 달러 → 2035년 약 11.5억 달러 전망 (CAGR 4.89%).
    
- **생성형 AI 취업 시장:** LinkedIn 등 글로벌 서비스가 생성형 AI 기능 도입. AI 취업 서비스가 메인스트림으로 진입.
    
- **국내 취업 시장:** 신입 채용 비중 감소로 취준생 1인당 평균 지원 기업 수 증가 → 자소서 작성 부담 가중.
    

### 2.2 타겟 고객 분석

|                    |                                                                        |
| ------------------ | ---------------------------------------------------------------------- |
| **구분**             | **상세 내용**                                                              |
| **1차 타겟 <br>(핵심)** | **대학교 3~4학년 취준생.** 포트폴리오 정리, 자소서 작성, 면접 준비를 동시에 해야 하며 디지털 서비스 친숙도가 높음. |
| **2차 타겟**          | 대학원생 및 졸업 후 1~2년 이내 구직자. 경력 정리 및 이직 준비 수요.                             |
| **3차 타겟 (B2B)**    | 채용 기업. AI 매칭으로 적합 후보자 탐색 비용 절감 수요.                                     |

### 2.3 고객 요구사항

1. **포트폴리오 자동화:** LMS에 흩어진 학점, 수상, 활동 이력 자동 정리
    
2. **자소서 효율화:** 기존 자소서를 목표 기업의 스타일 및 문항에 맞게 AI가 쾌속 변환
    
3. **면접 준비:** 실제 면접 환경과 유사한 AI 연습 및 즉각적인 피드백/점수 제공
    
4. **취업처 추천:** 내 스펙 기반 맞춤 기업 추천 및 기업의 먼저 연락(스카우트) 기능
    
5. 명확한 피드백이 있는 AI 면접

### 2.4 기대효과

- **학생:** 취업 준비(포트폴리오/자소서/면접) 시간 획기적 단축, 효율성 극대화.
    
- **기업:** AI 매칭을 통한 적합 인재 쾌속 발굴, 채용 리소스 절감.
    
- **학교:** 취업률 향상, 학생 만족도 제고, LMS 데이터의 성공적인 실용화 사례 창출.
    
- **비즈니스 확장성:** 타 대학 확장이 용이한 SaaS 형태로 발전 가능 
  (국내 대학 430개, 잠재 사용자 215만 명).


# 3. 기술스택

### 3.1 기술 스택

| **구분**     | **기술 / 도구**                            |
| ---------- | -------------------------------------- |
| **AI 엔진**  | H100 서버 기반 Qwen2.5-32B (OpenAI SDK 호환) |
| **프론트엔드**  | React.js, HTML/CSS/JS (반응형 웹)          |
| **백엔드**    | Springboot(CRUD 서버)                    |
| **데이터베이스** | MySQL ((지금은 H2)학생 정보, 포트폴리오, 기업 DB)    |
| **외부 연동**  | 학교 LMS REST API                        |
| **배포 환경**  | 로컬 서버 또는 학과 서버                         |
| LocalAI    | FastAPI를 사용한 python 로컬 ai 가동(영상,음성 분석) |

#### 3.1.1 /Back (Springboot) 개발 핵심 기술 스택 요약


```

<해당 checklist.md를 참조하여 핵심 기술 스택 TOP3 뽑아서 가지고 올것>

 # 백엔드 개발 체크리스트 (Backend Implementation Checklist)

이 체크리스트는 `backend-design-plan.md` 및 `specification.md`를 바탕으로 백엔드 시스템을 성공적으로 구현하기 위한 단계별 작업 목록입니다.

## 1. 프로젝트 초기 설정 및 기반 구성 (Phase 1)
- [x] **Spring Boot 프로젝트 생성 및 설정**
  - [x] `application.properties` (또는 `application.yml`) 환경 변수 설정 (DB 커넥션, JWT 시크릿, AI API 키 등)
  - [x] CORS 설정 (프론트엔드 연동을 위한 전역 또는 컨트롤러별 설정)
- [x] **데이터베이스 및 JPA 설정**
  - [x] H2 인메모리 데이터베이스 연동 및 콘솔(`h2-console`) 활성화 확인
  - [x] 스키마를 바탕으로 한 Entity 클래스 작성 (`User`, `Portfolio`, `JobPosting`, `Resume`, `Interview`, `InterviewQa`, `MatchResult`)
  - [x] JSON 타입 컬럼을 처리하기 위한 JPA `@Converter` (AttributeConverter) 구현
- [x] **보안 및 인증 (Spring Security + JWT)**
  - [x] JWT 발급 및 검증 유틸리티 클래스 구현
  - [x] 로그인 API (`/api/auth/login`) 구현 (이메일/비밀번호 검증)
  - [x] Spring Security 필터 체인 구성 및 JWT 인증 필터 등록
  - [x] Role (Admin, Student) 기반 접근 권한 제어 설정
- [x] **공통 에러 처리 및 응답 구조**
  - [x] `GlobalExceptionHandler`를 통한 전역 예외 처리
  - [x] API 공통 응답 포맷 (Success, Error DTO) 정의

## 2. 외부 연동 및 데이터 파싱 로직 (Phase 2)
- [x] **LMS 시스템 연동 (더미 데이터 Mocking)**
  - [x] 실제 API 연동 전 테스트를 위한 Mock Service 클래스 생성
  - [x] 하드코딩된 더미 데이터(학점, 수상, 활동 등)를 반환하는 로직 구현
  - [x] 학생 로그인 시 포트폴리오 자동 갱신 API (`/api/portfolio/lms`) 구현 (Mock 데이터 연동)
- [x] **PDF 파싱 모듈 구현 (Apache PDFBox)**
  - [x] `PDFBox` 라이브러리 의존성 추가 (Phase 1 build.gradle에서 완료)
  - [x] PDF file 업로드 및 텍스트 추출 서비스 구현 (`PdfParsingService`)
  - [x] 추출된 텍스트에서 주요 항목(이력서: 학력/경력, 채용공고: 자격요건 등)을 파싱/분류하는 기본 로직 구현 (AI 연동)

## 3. 핵심 도메인 API 구현 (Phase 3)
- [x] **사용자 및 포트폴리오 관리**
  - [x] 학생 포트폴리오 CRUD API (PDF 업로드 연동 및 AI 구조화 포함)
  - [x] 관리자 및 학생 마이페이지 관련 API (포트폴리오 조회/수정/삭제)
  - [x] **추가 경험 PDF 다중 등록 및 텍스트 자동 추출/관리 기능 구현**
- [x] **채용 공고 (Job Posting)**
  - [x] 관리자 채용공고 등록 API (PDF 파싱 연동 및 AI 구조화 포함)
  - [x] 채용공고 목록 조회 (페이징/필터링) 및 상세 조회 API (학생/관리자 공용)
  - [x] 채용공고 수정 및 삭제 API (관리자 전용)
  - [x] 채용공고 등록 시 회사(Company) 정보 자동 연동 및 생성 로직 구현
- [x] **기업 정보 관리 (Company)**
  - [x] 관리자용 회사 정보 CRUD API (`/api/admin/companies/**`) 구현
  - [x] 기업별 인재상, 조직문화, 면접 유형 등 상세 관리 기반 마련
  - [x] 채용 공고 URL 크롤링(`Jsoup`) 및 AI 분석을 통한 기업 상세 정보 자동 추출 로직 구현
- [x] **AI 비동기 처리 기반 구축**
  - [x] `@EnableAsync` 설정 및 커스텀 스레드 풀(ThreadPoolTaskExecutor) 구성
  - [x] H100 서버(Qwen2.5-32B) 통신을 위한 AI API Client 구현 (LiteLLM/OpenAI 호환 API 연동 완료)

## 4. AI 기반 취업 지원 서비스 구현 (Phase 4)
- [x] **AI 자소서 생성 (Resume)**
  - [x] 자소서 생성 및 수정/삭제 CRUD API 구현
  - [x] 포트폴리오(LMS + PDF 추출 텍스트) + 채용공고 데이터를 결합한 최적화된 프롬프트 작성 및 AI 호출
- [x] **AI 면접 시뮬레이션 (Interview)**
  - [x] 면접 세션 생성 및 초기 질문(공통/AI) 세팅 API (`/api/interview/start`) 구현
  - [x] 텍스트 답변 제출 및 AI 평가(피드백, 점수) API (`/api/interview/answer`) 구현
  - [x] **음성 변환(STT/TTS) 연동 API 구현 (`/api/interview/stt`, `/api/interview/tts`)**
- [x] **취업 매칭 시스템 (Match)**
  - [x] 학생 포트폴리오와 공고 데이터를 기반으로 매칭 점수 산출 로직 구현
  - [x] 사용자 맞춤형 매칭 결과 조회 및 사유 분석 API 구현

## 5. 안정화 및 테스트 (Phase 5)
- [ ] **단위 테스트 및 통합 테스트**
  - [ ] 주요 비즈니스 로직(Service Layer) 단위 테스트 작성 (JUnit, Mockito)
  - [ ] 인증/인가 및 Controller API 통합 테스트 (MockMvc, REST Assured)
- [x] **API 문서화**
  - [x] Swagger(Springdoc) 또는 REST Docs를 이용한 API 명세서 자동화 적용
- [ ] **성능 및 오류 점검**
  - [ ] 비동기 처리(AI 통신) 시 타임아웃 및 재시도(Retry) 로직 검증
  - [ ] N+1 쿼리 문제 점검 및 JPA Fetch Join 최적화


```


#### 3.1.2 /AI (FastAPI) 핵심 기술 스택 요약

```

<해당 checklist.md를 참조하여 핵심 기술 스택 TOP3 뽑아서 가지고 올것>

# AI 면접 분석 서버 개발 체크리스트

본 체크리스트는 `specification.md`, `interviewer_persona.md`, `harness.md` 문서를 기반으로 AI 서버 개발에 필요한 모든 요구사항을 정리한 문서입니다.

---

## 1. 프로젝트 기획 및 목표

- **핵심 기능 (In-Scope)**
    - [x] LMS 연동 포트폴리오 자동화 (Spring Boot)
    - [x] AI 기반 맞춤형 자소서 변환 (AI)
    - [x] AI 면접 시뮬레이터 (AI) - 기본 흐름 구현 완료
        - [x] 음성/영상 기반 답변 분석 (STT 완료, 비언어적 분석은 더미)
        - [x] 실시간 피드백 및 점수 제공 (LLM 연동 완료)
        - [x] 꼬리 질문 생성 (LLM 연동 완료)
    - [x] 취업처 추천 매칭 시스템 (Spring Boot)

- **정량 목표**
    - [ ] AI 면접 피드백 정확도 85% 이상 달성 (향후 고도화 필요)

---

## 2. AI 서버 핵심 기능 구현 (FastAPI)

### 2.1. API 엔드포인트 (`POST /analyze-and-feedback`)
- [x] FastAPI 애플리케이션 기본 설정 (`main.py`)
- [x] `/analyze-and-feedback` 엔드포인트 생성
- [x] `multipart/form-data` 형식 요청 처리
    - [x] `video_file`: `UploadFile` 타입으로 수신
    - [x] `audio_file`: `UploadFile | None` 타입으로 수신 (선택 사항)
    - [x] `context_data`: `str` (JSON) 타입으로 수신
- [x] Health Check를 위한 `/` 엔드포인트 구현

### 2.2. 데이터 모델 (Pydantic V2)
- [x] `InterviewContext` 모델 정의 (`models.py`)
- [x] `BehaviorAnalysis` 모델 정의 (`models.py`)
- [x] `LLMFeedback` 모델 정의 (`models.py`)
- [x] 최종 응답을 위한 `AnalysisResult` 모델 정의 (`models.py`)

### 2.3. 데이터 처리 흐름 (Orchestration)
- [x] `services.py` 파일에 비즈니스 로직 분리
- [x] `context_data` 문자열을 `InterviewContext` 모델로 파싱 및 유효성 검사
- [x] 수신된 미디어 파일을 임시 디렉토리에 저장 (`temp_media/`)
- [x] `moviepy`를 활용한 오디오 스트림 추출 로직 실구현 (최신 v2.x 문법 적용)
- [x] `asyncio.gather`를 사용한 병렬 분석 태스크 실행
- [x] 분석 완료 후 `try-finally` 블록을 통해 임시 파일 반드시 삭제
- [x] 예상치 못한 서버 오류에 대한 예외 처리 (`main.py`)

---

## 3. AI 분석 모듈

### 3.1. 비언어적/언어적 요소 분석
- [x] **STT (음성 텍스트 변환)**
    - [x] OpenAI Whisper API 연동 (`transcribe_audio_with_whisper`)
    - [x] 비동기(`async`)로 API 호출
- [x] **영상 분석 (Vision Analysis)**
    - [x] `OpenCV`, `MediaPipe Tasks API`를 사용한 시선 처리, 자세 분석 로직 구현
    - [x] `face_landmarker.task`, `pose_landmarker.task` 모델 연동 완료
    - [x] CPU-Bound 작업을 위한 `run_in_executor` 적용
- [x] **음성 특징 분석 (Audio Feature Analysis)**
    - [x] `librosa`를 사용한 말하기 속도(SPM), 음량(dB) 분석 로직 구현

---

## 4. 로컬 STT (Whisper) 전환 완료 (성공)

OpenAI API 유료 결제 이슈를 해결하고 M4 맥북의 성능을 극대화하기 위해 로컬 환경에서 무료 STT를 구동하도록 전환을 완료했습니다.

### 4.1. 환경 구축
- [x] **필수 라이브러리 설치:** `openai-whisper`, `setuptools-rust`, `torch`, `torchaudio`
- [x] **시스템 의존성:** `ffmpeg` 설치 완료 (`brew install ffmpeg`)

### 4.2. 모델 최적화 및 가속
- [x] **모델 사이즈 선정:** `base` 모델 사용 (속도와 정확도의 최적 균형점)
- [x] **M4 하드웨어 가속:** `device="mps"` (Metal Performance Shaders) 옵션을 적용하여 M4 칩의 GPU/Neural Engine 활용 완료

### 4.3. 코드 리팩토링 (`ai_analyzer.py`)
- [x] `AsyncOpenAI` 기반의 STT 호출 로직 제거 및 로컬 호출로 교체
- [x] `whisper.load_model()`을 사용하여 로컬 모델 로드 로직 추가
- [x] 싱글톤(Singleton) 패턴을 적용하여 모델 중복 로드 방지 및 응답 속도 최적화

### 4.4. 검증 및 테스트
- [x] 기존 인터페이스 호환성 유지 (다른 소스 코드 수정 최소화)
- [x] 한국어(`language="ko"`) 고정 설정을 통한 인식률 향상

---

## 5. 코드 구조 및 환경

- [x] `main.py`, `services.py`, `ai_analyzer.py`, `models.py`로 코드 역할 분리
- [x] `requirements.txt`에 필요한 모든 라이브러리 명시
- [x] OpenAI API 키 등 민감 정보 환경 변수 처리 준비 (`.env`)
- [x] `uvicorn`을 사용한 서버 실행 환경 구성
- [x] **서버 안정화 조치 완료**
    - [x] 가상환경 중복 폴더(`venv`) 정리 및 개발 환경 최적화
    - [x] `uvicorn` 무한 재시작 방지를 위한 `temp_media` 무시 및 실행 옵션 최적화

    ---

    ## 5. 서버 API 테스트 가이드 (How to Test)

    구현이 완료된 FastAPI 서버를 실제로 테스트하기 위한 순차적인 방법입니다.

    ### Step 1. 환경 변수(`.env`) 설정
    - 프로젝트 루트 디렉토리에 `.env` 파일을 생성합니다.
    - STT 처리를 위한 OpenAI API 키와, 피드백 생성을 위한 LLM API 키를 입력합니다.
    ```env
    OPENAI_API_KEY="sk-your-openai-api-key"
    LLM_BASE_URL="http://your-h100-server-url/v1" # 학과 서버 미사용 시 생략 가능
    LLM_API_KEY="your-llm-api-key"
    ```

    ### Step 2. 테스트용 미디어 파일 준비
    - 테스트에 사용할 짧은 영상 파일(예: `test_video.mp4`)을 준비합니다. 가급적 얼굴이 잘 나오고 목소리가 포함된 10~20초 분량의 파일이 좋습니다.

    ### Step 3. FastAPI 서버 실행
    - 터미널에서 가상환경을 활성화한 후 아래 명령어로 서버를 실행합니다. (재시작 방지 옵션 포함)
    ```bash
    uvicorn main:app --reload --reload-dir . --reload-exclude ".venv" --reload-exclude "temp_media"
    ```

    ### Step 4. Swagger UI 접속 및 API 호출
    1. 웹 브라우저를 열고 `http://127.0.0.1:8000/docs` 에 접속합니다.
    2. `POST /analyze-and-feedback` 엔드포인트를 클릭하고 **Try it out** 버튼을 누릅니다.
    3. 데이터 입력:
    - **video_file**: Step 2에서 준비한 `test_video.mp4` 파일을 업로드합니다.
    - **audio_file**: (선택 사항) 비워두면 영상에서 자동으로 오디오를 추출합니다.
    - **context_data**: 아래와 같은 JSON 문자열을 그대로 복사하여 붙여넣습니다.
      ```json
      {
        "interview_type": "technical",
        "current_question": "Spring Boot의 장점에 대해 설명해주세요.",
        "student_portfolio": "Java 웹 개발 경험이 있는 4학년 학생입니다.",
        "company_info": "도전적이고 자기 주도적인 인재를 원합니다."
      }
      ```
    4. **Execute** 버튼을 눌러 요청을 전송합니다.

    ### Step 5. 응답 검증 (성공 기준)
    - **Status Code:** `200 OK`가 반환되어야 합니다.
    - **Response Body:** 다음과 같은 형태의 JSON이 반환되는지 확인합니다.
    - `behavior_analysis`: MediaPipe와 Librosa에 의해 분석된 숫자들 (`eye_contact_issues`, `posture_issues`, `speech_rate_spm`, `volume_db`)이 0이 아닌 실제 분석된 값으로 나와야 합니다.
    - `feedback`: LLM이 생성한 한국어 피드백 문자열이 존재해야 합니다.
    - `score`: 0~100 사이의 정수 점수가 나와야 합니다.
    - `next_question`: 이전 답변을 기반으로 한 한국어 꼬리 질문이 존재해야 합니다.

```


# 4 전체적인 프로젝트 다이어그램

## 📂 프로젝트 구조 (Project Structure)  
  
### 🗺 전체 프로젝트 트리  
```text  
DidimFinal/  
├── AI/                 # AI 분석 서버 (Python/FastAPI)  
├── Back/               # 백엔드 서버 (Java/Spring Boot)  
├── Front/              # 프론트엔드 (React/TypeScript/Vite)  
├── docs/               # 프로젝트 문서 및 체크리스트  
└── README.md           # 프로젝트 가이드 (현재 파일)  
```  
  
### 🖥 Front-end (React)  
```text  
Front/src/  
├── components/         # 공통 UI 컴포넌트 및 레이아웃  
├── pages/              # 주요 페이지 (Interview, CoverLetter, JobPostings 등)  
├── router/             # AppRouter 및 경로 설정  
├── state/              # 전역 상태 관리 (커스텀 훅/상태)  
├── styles/             # 전역 CSS 및 테마 설정  
├── types/              # TypeScript 인터페이스 정의  
├── utils/              # 날짜 포맷 등 공통 유틸리티  
└── main.tsx            # 엔트리 포인트  
```  
  
### ⚙️ Back-end (Spring Boot)  
```text  
Back/src/main/java/com/capstone/back/  
├── config/             # Security, Async, Swagger 등 설정  
├── controller/         # API 엔드포인트 제어  
├── domain/             # JPA 엔티티 정의 (User, Interview, Resume 등)  
├── dto/                # 데이터 전송 객체  
├── repository/         # DB 접근을 위한 Repository 인터페이스  
└── service/            # 비즈니스 로직 및 외부 API(AI 서버) 연동  
```  
  
### 🧠 AI Server (FastAPI)  
```text  
AI/  
├── main.py             # FastAPI 앱 엔트리 포인트  
├── services.py         # AI 분석 로직 (STT, LLM 연동 등)  
├── models.py           # Pydantic 데이터 모델  
├── ai_analyzer.py      # 미디어 분석 코어 로직  
├── models/             # MediaPipe 등 AI 모델 파일  
└── temp_media/         # 미디어 처리용 임시 저장소  
```  
  
---  
  
## 📊 시스템 아키텍처 및 흐름도 (Architecture & Flow)  
  
전체 시스템의 서버 간 통신 및 데이터 흐름은 다음과 같습니다.  

```

graph TD
    %% 클라이언트
    subgraph Client [Frontend]
        UI[React App]
    end

    %% 메인 서버
    subgraph Backend [Spring Boot Server]
        Auth[Security/JWT]
        Service[Business Logic]
        Proxy[AI Proxy/Client]
        DB[(H2/MySQL DB)]
    end

    %% AI 분석 서버
    subgraph AIServer [AI Server]
        FastAPI[FastAPI Endpoint]
        Analyzer[AI Analyzer / MediaPipe]
        STT[Whisper / STT]
    end

    %% 외부 API
    subgraph External [External APIs]
        LLM[School LLM API]
    end

    %% 흐름 연결
    UI -- "1. API Request (Multipart/JSON)" --> Service
    Service -- "2. User Auth & Data CRUD" --> DB
    Service -- "3. Media & Context Transfer" --> FastAPI
    
    FastAPI -- "4. Media Analysis (Vision/Voice)" --> Analyzer
    FastAPI -- "5. Voice to Text" --> STT
    
    FastAPI -- "6. Request Feedback/Question" --> LLM
    LLM -- "7. Response Result" --> FastAPI
    
    FastAPI -- "8. Analysis Result (JSON)" --> Service
    Service -- "9. Store Result" --> DB
    Service -- "10. Final Response" --> UI

```



### 🔄 핵심 시퀀스  
1.  **자소서 생성:** 사용자가 공고를 선택하면 Backend가 AI 서버에 분석을 요청하고, LLM을 통해 생성된 자소서를 DB에 저장 후 프론트로 반환합니다.  
2.  **AI 면접:**   
*   사용자가 캠을 켜고 답변을 녹화합니다.  
    *   프론트엔드는 비디오/음성 파일을 Backend로 전송합니다.  
    *   Backend는 해당 파일을 AI 서버로 전달하여 감정, 시선 처리, 답변 내용을 분석합니다.  
    *   AI 서버는 분석 결과와 '꼬리 질문'을 생성하여 Backend를 통해 프론트로 즉시 전달합니다.  
    *   면접 종료 시 전체 피드백과 점수를 합산하여 보여줍니다.

# 5. User 플로우 및 어드민


# 📑 Didim 사용자 서비스 플로우 (User Flow)  
  
이 문서는 학생(사용자)과 관리자가 **Didim** 플랫폼을 이용하는 전체 과정을 역할별 화면 흐름 중심으로 정리한 가이드입니다.  
  
---  
  
## 👨‍🎓 학생 서비스 플로우 (Student User Flow)  
  
### 1. 로그인 (Login)  
*   사용자는 대학교 계정(학번/비밀번호)을 통해 서비스에 접속합니다.  
*   관리자(`admin@didim.com`) 또는 학생(`student@didim.com`) 더미 계정을 사용하여 기능을 즉시 테스트할 수 있습니다.  

<로그인 화면>


<로그인 후 메인페이지>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.44.30.png)

<아래로 내렸을시>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.45.15.png)


### 2. 포트폴리오 구축 (Portfolio & LMS Sync)  
*   **LMS 동기화:** 버튼 클릭 한 번으로 대학 LMS(뉴칼라 등)에 기록된 학점, 수상 내역, 활동 이력을 자동으로 가져와 포트폴리오를 구성합니다.  
*   **추가 이력 관리:** 사용자는 자동으로 불러온 데이터 외에도 본인의 프로젝트, 수상 경력, 자격증 등을 **PDF 파일 형식**으로 추가 업로드하여 포트폴리오를 보강할 수 있습니다.  

<포트폴리오 화면>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.46.17.png)

<'업로드' 버튼 클릭 시>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.49.16.png)


<수상내역>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.46.58.png)

<자격증>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.47.24.png)

<활동/동아리/장학금>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.47.46.png)

<프로젝트 - 선택, 전체 삭제 가능>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.48.12.png)



### 3. 공고 확인 및 매칭률 분석 (Job Matching)  
*   시스템에 등록된 채용 공고 목록을 탐색합니다.  
*   사용자의 전체 역량(포트폴리오)과 각 채용 공고의 요구 조건을 AI가 비교 분석하여 **개인별 맞춤 매칭률(%)**을 제공합니다.  

<채용공고 - 본인의 직무와 관련된 회사는 '추천'으로 표시>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.50.01.png)

<해당 공고의 자세히 보기 클릭시 나타나는 화면>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.50.58.png)

![](Attached_file/스크린샷%202026-06-10%20오전%2011.52.06.png)


### 4. AI 자기소개서 생성 (AI Cover Letter Generation)  
*   사용자가 원하는 기업과 직무 공고를 선택합니다.  
*   AI가 해당 기업의 요구 조건과 사용자의 포트폴리오 데이터를 바탕으로 최적화된 **맞춤형 자기소개서**를 자동으로 초안 작성해줍니다.  


![](Attached_file/스크린샷%202026-06-10%20오전%2011.53.11.png)

![](Attached_file/스크린샷%202026-06-10%20오전%2011.53.32.png)

![](Attached_file/스크린샷%202026-06-10%20오전%2011.54.06.png)

### 5. 자기소개서 및 프로필 관리 (Management)  
*   **수정 및 삭제:** 생성된 자기소개서를 직접 확인하고, 본인의 의도에 맞게 수정하거나 불필요한 초안은 삭제할 수 있습니다.  
*   **추가 정보 업데이트:** 필요한 경우 자신의 정보를 PDF 형식으로 추가 입력하여 AI가 더 정확한 분석을 할 수 있도록 지원합니다.

<재첨삭 버튼 클릭시 명령어입력 가능>
![](Attached_file/스크린샷%202026-06-10%20오전%2011.58.11.png)

  
### 6. AI 면접 설정 (AI Interview Setup)  
*   사용자는 면접 연습을 위해 **3가지 페르소나** 중 하나를 선택할 수 있습니다:  
    1.  **인성 면접관:** 가치관과 조직 적합성 중심  
    2.  **기술 면접관:** 직무 역량 및 기술적 깊이 검증 중심  
    3.  **PT/직무 면접관:** 논리적 사고 및 실무 해결 능력 중심  

![](Attached_file/스크린샷%202026-06-10%20오전%2011.59.55.png)


  
### 7. AI 면접 진행 및 꼬리 질문 (Interview Session)  
*   선택한 페르소나의 AI 면접관(인성,기술,직무 중 택 1)과 실시간 시뮬레이션을 진행합니다.  
*   AI는 지원자의 모든 스펙(포트폴리오)과 제출한 자기소개서 내용을 실시간으로 분석하여, 답변에 대한 **날카로운 꼬리 질문**을 던지며 실제 면접과 유사한 긴장감을 제공합니다.  

![](Attached_file/스크린샷%202026-06-10%20오후%2012.00.27.png)


### 8. 결과 및 피드백 확인 (Feedback)  
*   면접이 종료되면 AI가 답변의 논리성, 구체성 등을 평가하여 점수를 산출합니다.  
*   잘한 점(Good Point)과 보완할 점(Bad Point)에 대한 상세한 피드백을 확인하고, 다음 연습을 위한 가이드를 제공받습니다.

  
---  
  
## 👨‍💼 관리자 서비스 플로우 (Admin User Flow)  
  
### 1. 채용 공고 원천 데이터 업로드 (Job Data Upload)  
*   관리자는 기업으로부터 받은 채용 공고 PDF 파일들을 서버에 대량 또는 개별적으로 업로드합니다.

![](Attached_file/스크린샷%202026-06-10%20오후%2012.10.09.png)

![](Attached_file/스크린샷%202026-06-10%20오후%2012.10.53.png)


### 2. AI 기반 자동 데이터 파싱 (AI-Driven Parsing)  
*   업로드된 PDF 파일을 AI가 실시간으로 분석합니다.
*   AI는 비정형 텍스트에서 **직무(Job Role), 자격 요건(Requirements), 우대 사항, 마감일, 기업 정보** 등을 자동으로 추출하여 정형화된 데이터로 변환한 뒤 DB에 저장합니다.

![](Attached_file/스크린샷%202026-06-10%20오후%2012.08.59.png)

![](Attached_file/스크린샷%202026-06-10%20오후%2012.09.15.png)

### 3. 채용 공고 통합 관리 (Job Posting CRUD)  
*   관리자 대시보드에서 시스템에 등록된 모든 채용 공고를 한눈에 관리합니다.  
*   **생성(Create):** 직접 정보를 입력하여 새 공고를 생성하거나 AI 파싱 결과를 최종 승인합니다.  
*   **조회(Read):** 등록된 공고의 상세 정보와 매칭 현황을 모니터링합니다.  
*   **수정(Update):** AI가 잘못 추출했거나 변경된 공고 내용을 즉시 수정합니다.  
*   **삭제(Delete):** 마감되었거나 잘못된 공고를 시스템에서 제거합니다.

![](Attached_file/스크린샷%202026-06-10%20오후%2012.04.33.png)




# 6. 핵심 기능 소개 - 실제 AI 면접 영상(유튜브 링크)

- 실제 이동해야 하는 유튜브 링크 : https://www.youtube.com/watch?v=XJdUCcRXj88

## 1. AI 면접 후 피드백

![](Attached_file/스크린샷%202026-06-10%20오전%208.48.51.png)


![](Attached_file/스크린샷%202026-06-10%20오전%208.49.18.png)

![](Attached_file/스크린샷%202026-06-10%20오전%208.49.03.png)


# 7. 결론 및 향후 계획

## 7.1 결론

 이 프로젝트의 결론은 단순한 웹 서비스를 넘어, "취업 준비생의 경험(Portfolio)과 기업의 요구사항(Job Posting)을 AI로 정교하게 연결하여 실전 경쟁력을 높여주는 통합 커리어 케어
  솔루션"의 완성입니다.

  기술적, 서비스적 관점에서 정리한 결론은 다음과 같습니다.

  1. 기술적 결론: 안정적인 멀티 서버 아키텍처 구현
   * 완전한 통합: React(프론트), Spring Boot(메인 백엔드), FastAPI(AI 분석)라는 서로 다른 기술 스택을 하나의 유기적인 시스템으로 결합하는 데 성공했습니다.
   * 고성능 미디어 처리: 고용량(50MB 이상) 비디오/음성 데이터를 안정적으로 주고받으며, 실시간에 가까운 AI 분석 피드백 루프를 구축했습니다.
   * 데이터 정합성 및 견고함: 중복 데이터 방지 로직과 상세 에러 핸들링을 통해 실제 운영 환경에서도 견딜 수 있는 수준의 백엔드 안정성을 확보했습니다.

  2. 서비스적 결론: 몰입감 있는 실전 면접 환경 제공
   * 사용자 중심 Re-design: 기존의 단편적인 UI를 개선하여, 60초 타이머와 끊김 없는 꼬리 질문이 이어지는 '진짜 면접장'과 같은 몰입감을 구현했습니다.
   * 개인화된 AI 가이드: 단순히 자소서를 대신 써주는 것이 아니라, 사용자의 실제 포트폴리오 근거를 바탕으로 논리적인 자소서를 생성하고 면접에서 날카로운 질문을 던짐으로써
     사용자의 성장을 돕습니다.
   * 효율적인 프로세스: 공고 탐색 → 매칭 분석 → 자소서 생성 → AI 면접 연습으로 이어지는 취업 준비의 전 과정을 하나의 플랫폼 안에서 해결할 수 있도록 동선을 최적화했습니다.

  🏁 최종 요약
  결국 이 프로젝트는 "기술이 어떻게 취업이라는 현실적인 문제를 가장 효율적으로 해결할 수 있는가?"에 대한 해답입니다. 이제 사용자는 DIDIM을 통해 자신의 강점을 데이터로
  증명하고, AI 면접관과 연습하며 가장 완벽한 상태로 실전 면접에 임할 수 있게 되었습니다.


## 7.2 향후 계획
1. 자소서 첨삭 페이지의 '교수님께 첨삭' 버튼 실제 해당 학생의 전공 교수님의 이메일로 전송
2. 관리자 페이지 개발
3. 실제 LMS 연동
4. SaaS 확장
5. 실제 연암공과대학교 전산실과 협업


