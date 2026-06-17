# 🧪 POOM-MLFLOW

> **POOM** — PB(Private Banker) 업무 지원 AI Assistant 플랫폼의 ML 실험 관리 서버

---

## 📌 개요

POOM 플랫폼의 MLflow 기반 모델 실험 관리 레포지토리입니다.
경제지표 예측 모델(금값·기준금리·매매가격지수)의 실험 이력, 파라미터, 메트릭, 아티팩트를
추적하고 관리합니다. 아티팩트는 AWS S3에 저장되며 메타데이터는 PostgreSQL에 기록됩니다.

---

## 🗂 프로젝트 구조
POOM-MLFLOW/

├── .github/workflows/          # GitHub Actions CI/CD

├── Dockerfile                  # MLflow 서버 이미지 빌드

├── docker-compose-mlflow.yml   # MLflow 서비스 구성

└── README.md

---

## ⚙️ 기술 스택

| 분류 | 기술 |
|---|---|
| **실험 관리** | MLflow |
| **메타데이터 DB** | PostgreSQL 13 |
| **아티팩트 저장소** | AWS S3 |
| **인프라** | Docker Compose (멀티스테이지 빌드), `poom-network` |

---

## 🧩 서비스 구성

`docker-compose-mlflow.yml` 기준으로 아래 서비스가 실행됩니다.

| 서비스 | 역할 | 포트 |
|---|---|---|
| `mlflow-server` | MLflow Tracking 서버 | 5002 |
| `mlflow-postgres` | 실험 메타데이터 저장 | - |

> 모델 아티팩트는 `MLFLOW_DEFAULT_ARTIFACT_ROOT`로 지정된 AWS S3 버킷에 저장됩니다.

---

## 🚀 실행 방법

```bash
# 1. 환경변수 설정
cp .env.example .env

# 2. 서비스 실행
docker compose -f docker-compose-mlflow.yml up -d

# 3. MLflow UI 접속
# http://localhost:5002
```

---

## 🔗 연관 레포지토리

| 레포 | 역할 |
|---|---|
| [POOM-AI](https://github.com/PoomSaengPoomSa/POOM-AI) | 모델 학습 및 실험 기록 |
| [POOM-AIRFLOW](https://github.com/PoomSaengPoomSa/POOM-AIRFLOW) | MLOps 파이프라인 |
| [POOM-BACK](https://github.com/PoomSaengPoomSa/POOM-BACK) | FastAPI 백엔드 서버 |
| [POOM-ELK](https://github.com/PoomSaengPoomSa/POOM-ELK) | 로그 모니터링 |

---

> 우리FISA AI 엔지니어링 1팀 | POOM 프로젝트
