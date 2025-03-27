
# H<img width="225" alt="해커톤 메인" src="https://github.com/user-attachments/assets/a6a3f244-3fe8-4ace-9a1f-bfb689e25e12" />
airPower_AI
아래는 **HairPower** 프로젝트의 README 파일입니다. 프로젝트 개요, 주요 기능, API 명세, 설치 방법 등을 포함하여 작성하였습니다.

--- 

# 🚀 HairPower - 맞춤형 헤어스타일 추천 서비스

### ✨ **사용자의 얼굴 특징을 분석하여 최적의 헤어스타일을 추천합니다!**  
💇‍♂️ **헤어스타일이 고민되시나요?**  
HairPower는 AI 기반으로 **사용자의 얼굴형을 분석**하고, **개인 맞춤형 헤어스타일**을 추천해주는 서비스입니다.  
사진을 업로드하면 AI가 얼굴 특징을 분석하고, 그에 맞는 최적의 스타일을 제안합니다.  

---

## 📌 **프로젝트 개요**
🔍 **HairPower**는 AI 기반의 CNN과 LLM (Large Language Model)을 활용한 **헤어스타일 추천 서비스**입니다.

✔️ **EfficientNet**을 사용하여 턱 모양 예측  
✔️ **Mediapipe**로 이목구비 비율 분석  
✔️ **OpenAI API**를 이용해 사용자 맞춤 최적의 헤어스타일 추천  
✔️ **FastAPI 기반 API 서버 구축, ngrok배포**  
✔️ **SQLite DB를 활용한 데이터 저장 및 대화 내역 관리**  

---

## 🛠 **기술 스택**
| 카테고리 | 기술 |
|----------|-------------|
| **Backend** | Python, FastAPI |
| **AI 모델** | EfficientNet, Mediapipe |
| **LLM** | OpenAI GPT-4o |
| **Database** | SQLite |
| **Storage** | Amazon S3 |
| **Server Deployment** | Ngrok, Uvicorn |
| **Version Control** | Git, GitHub |

---

## 🔥 **주요 기능**
### 1️⃣ **사용자 얼굴 분석**
📸 **사진 업로드 → AI가 얼굴형 분석**  
✔️ EfficientNet을 사용하여 턱 모양 예측  
✔️ Mediapipe를 사용해 얼굴 특징 추출  
✔️ 턱, 코, 이마, 미간 등의 비율 분석  

### 2️⃣ **맞춤형 헤어스타일 추천**
💇‍♀️ **AI가 적합한 헤어스타일을 추천**  
✔️ OpenAI API를 활용해 맞춤형 추천 제공  
✔️ 이모지와 마크다운을 활용한 가독성 높은 설명  

### 3️⃣ **대화 내역 관리**
💬 **유저와 AI의 대화 기록 저장**  
✔️ SQLite 기반으로 `ai_history` 테이블에 기록  
✔️ API 호출 시 과거 대화 히스토리 반영  

---

## 🔗 **API 명세**
### 1️⃣ **사진 업로드 & AI 분석 요청**
```
POST /upload-photo
```
#### 🔹 **Request Body (JSON)**
```json
{
  "user_id": "abc123",
  "gender": "male",
  "image_url": "http://..."
}
```
#### 🔹 **Response (JSON)**
```json
{
  "status": "success",
  "user_id": "abc123",
  "message": "이미지 업로드 완료. AI 분석 진행 중.",
  "features": {
    "forehead": "평범한 이마",
    "nose": "짧은 코",
    "chin": "긴 턱",
    "eye_mid": "평범한 미간",
    "vertical": "짧은 얼굴",
    "shape": "세모형"
  }
}
```

---

### 2️⃣ **사용자의 얼굴 특징 조회**
```
GET /select-story-image/{user_id}
```
#### 🔹 **Response (JSON)**
```json
{
  "user_features": {
    "forehead": "평범한 이마",
    "nose": "짧은 코",
    "chin": "긴 턱",
    "eye_mid": "평범한 미간",
    "vertical": "짧은 얼굴",
    "shape": "세모형"
  }
}
```

---

### 3️⃣ **헤어스타일 추천 결과 조회**
```
GET /get-story-result/{user_id}
```
#### 🔹 **Response (JSON)**
```json
{
  "description": "헤어 스타일 추천 결과",
  "content": {
    "type": "text/markdown",
    "text": "### **📌 개선된 답변 예시 (템플릿 적용)**\n\n> 📌 **사용자 얼굴 특징:** 긴 얼굴, 짧은 이마, 긴 코  \n>  \n> **💇‍♀️ 최적의 추천 스타일:** **사이드 스윕 뱅 (Side-Swept Bangs)**  \n\n..."
  }
}
```

---

## 📂 **프로젝트 구조**
```
HairPower_AI/
│── main.py                # FastAPI 서버 실행 코드
│── face_analyzer.py       # YOLO & EfficientNet 기반 얼굴 분석 모듈
│── hairstyle_recommender.py  # LLM 기반 헤어스타일 추천 로직
│── database.py            # SQLite 데이터베이스 관리
│── requirements.txt       # 필요한 라이브러리 목록
│── README.md              # 프로젝트 설명
```

---

## 🚀 **설치 및 실행 방법**
### 1️⃣ **Python 환경 설정**
```bash
python -m venv venv
source venv/bin/activate  # (Windows는 venv\Scripts\activate)
pip install -r requirements.txt
```

### 2️⃣ **데이터베이스 생성**
```bash
python database.py
```

### 3️⃣ **FastAPI 서버 실행**
```bash
uvicorn main:app --reload
```

### 4️⃣ **Ngrok 터널링**
```bash
ngrok http 8000
```

### 5️⃣ 그 외 YOUR_API_KEY
---

## 📢 **향후 개선 사항**
✅ YOLO 최신 버전 도입하여 얼굴 인식 정밀도 향상  
✅ 다양한 얼굴 특징 데이터 학습 및 개선  
✅ 스타일 추천 정확도 향상을 위한 추가 데이터 확보  

---

## 👥 **팀 소개**
| 역할 | 이름 | GitHub |
|------|------|--------|
| 👩‍💻 프로젝트 리더, AI 모델링 | ian.lee | [@dealm99-ai](https://github.com/Idealm99) |
| 👩‍💻 AI 모델링 | anna.kim | [@anna-ai](https://github.com/sunnyanna0) |
| 👩‍💻 프론트 | zwen.ji | [@zwen-fullstack](https://github.com/zwen-yirochi) |
| 👩‍💻 백엔드 | denver.ko | [@denver-cloud](https://github.com/SeriousBug98) |
| 👩‍💻 백엔드 | cinnamon.lee | [@cinnamon-cloud](https://github.com/mintchococ) |
| 👩‍💻 클라우드 | ken.kim | [@ken-cloud](https://github.com/year99) |

