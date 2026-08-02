# 🚨 알람 & 예지보전 분석 대시보드

포스코퓨처엠 양극재 4라인 (대입경A/B/단결정/열처리) 알람 및 설비 가동 이력 통합 분석 시스템

## 🌟 주요 기능

### 알람 분석
- 라인별 알람 발생빈도 TOP N 분석
- 일별 추세 · 이상탐지 (IsolationForest)
- RandomForest / MLP 신경망 기반 예측
- Gemini API 자동 리포트 생성

### 예지보전 (Predictive Maintenance)
- **설비별 MTBF/MTTR** — 신뢰성 지표
- **부위별 Pareto** — 고장 부품 우선순위
- **임박 고장 경보** — 반복 발생 패턴 탐지
- **잔여수명(RUL) 추정** — 부품 교체 시점 예측
- **이력 타임라인** — Gantt 시각화

## 📦 설치 및 실행

```bash
# 1. 저장소 클론
git clone https://github.com/YOUR_USERNAME/predictive-maintenance-dashboard.git
cd predictive-maintenance-dashboard

# 2. 가상환경 생성 (선택)
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

# 3. 의존성 설치
pip install -r requirements.txt

# 4. 실행
streamlit run app.py
```

## 📁 파일 형식

### 알람 이력 파일
- **J열(10번째)**: TAG (RA4/RB4/RC4/RX4로 시작)
- 발생시간 컬럼 자동 감지

### 예지보전 파일 (가동정보 iba)
| 열 | 내용 | 예시 |
|---|---|---|
| D | Asset 코드 | 4PE100154 (대입경A) |
| F | 시작일시 | 2026-08-03 07:00 |
| G | 종료일시 | 2026-08-04 07:00 |
| H | 경과시간(분) | 1440 |
| I | 휴지코드 | 계획정지, 설비장애, 작업준비 |
| L | 주요작업내용 | 충진기 서보 교체작업 |

### 설비 매핑
- `4PE100154` → 4라인 대입경A (소성 #A)
- `4PE100155` → 4라인 대입경B (소성 #B)
- `4PE100156` → 4라인 단결정 (소성 #C)
- `4PE100157` → 4라인 열처리

## ☁️ Streamlit Cloud 배포

1. GitHub 저장소에 push
2. [share.streamlit.io](https://share.streamlit.io) 접속
3. New app → 저장소 선택 → `app.py` 지정 → Deploy
