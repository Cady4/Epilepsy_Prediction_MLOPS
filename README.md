<div style="display: flex; justify-content: center;">
  <h1> 🧠 Projet MLOps Epilepsy Prediction  P</h1>
</div>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://docker.com)
[![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=for-the-badge&logo=mlflow&logoColor=white)](https://mlflow.org)
[![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)](https://prometheus.io)
[![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)](https://grafana.com)

*Une plateforme MLOps complète pour la prédiction d'épilepsie avec orchestration automatisée*

[🚀 Démarrage Rapide](#-démarrage-rapide) • [📋 Documentation](#-documentation) • [🏗️ Architecture](#️-architecture) • [🤝 Contribution](#-contribution)

</div>

---

## 🎯 Vue d'ensemble

Cette plateforme a été conçue pour prédire les crises d’épilepsie. Elle applique les bonnes pratiques DevOps et MLOps et utilise des micro-services, ce qui lui assure évolutivité et sécurité.

Le schéma suivant illustre le workflow général, étant donné qu'un utilisateur lance une requete pour faire une prédiction : 

![Texte alternatif](assets/workflow_general.png)


### ✨ Fonctionnalités Clés

```mermaid
graph LR
    A[🔐 Authentification JWT] --> B[📊 Preprocessing]
    B --> C[🤖 Training LSTM]
    C --> D[📈 Evaluation]
    D --> E[🚀 Inference API]
    E --> F[📱 Monitoring]
    
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#fff3e0
    style E fill:#fce4ec
    style F fill:#f1f8e9
```
## 🗂️ Structure du Projet

```
📁 epilepsy-mlops/
├── 🔧 .github/workflows/          # CI/CD Pipeline
│   └── ci-cd.yml
├── 📊 monitoring/                 # Prometheus & Grafana configs
│   ├── prometheus/
│   └── grafana/
├── 🐳 services/                   # Microservices
│   ├── 🔐 authentication/        # JWT Auth API
│   ├── 📊 preprocessing/          # Data Pipeline
│   ├── 🤖 model_training/         # LSTM Training
│   ├── 📈 evaluation/             # Model Evaluation
│   ├── 🚀 inference/              # Prediction API
│   └── 📋 patient_data_pull/      # Data Extraction
├── 🧪 tests/                      # Test Suite
│   ├── unit/
├── 📦 data/                       # Data Management
│   ├── raw/
│   ├── processed/
│   └── models/
├── ⚡ orchestration/              # Prefect Workflows
│   └── flows/
├── 🐳 docker-compose.yml          # Container Orchestration
├── 📋 requirements.txt            # Dependencies
└── 📚 docs/                       # Documentation
```
## 🏗️ Architecture Système

### Infrastructure MLOps

Le schéma suivant détaille le workflow MLOPS utilisé : 
![Texte alternatif](assets/workflow_mlops.png)


### Pipeline de Données

```mermaid
flowchart TD
    A[📥 Raw Patient Data] --> B{🔍 Data Validation}
    B -->|✅ Valid| C[🧹 Preprocessing]
    B -->|❌ Invalid| D[⚠️ Error Handling]
    
    C --> E[⚖️ Balanced Sampling]
    E --> F[🔢 LSTM Format Conversion]
    F --> G[💾 Processed Data Storage]
    
    G --> H[🤖 Model Training]
    H --> I[📊 Model Evaluation]
    I --> J{📈 Performance Check}
    
    
    J -->|⭐ Better| K[🚀 Model Promotion]
    J -->|📉 Worse| L[🔄 Retrain with New Params]
    
    K --> M[🌐 Production Deployment]
    M --> N[📱 Real-time Inference]
    
    style A fill:#e3f2fd
    style C fill:#f3e5f5
    style H fill:#e8f5e8
    style I fill:#fff3e0
    style K fill:#e8f5e8
    style M fill:#fce4ec
    style N fill:#f1f8e9
```

## 🚀 Démarrage Rapide

### Prérequis

```bash
# Versions requises
Python >= 3.10
Docker >= 20.10
Docker Compose >= 2.0
Git >= 2.30
```

### Installation Express

```bash
# 1️⃣ Cloner le repository
cd epilepsy-mlops

# 2️⃣ Configuration de l'environnement
python -m venv virtmlops

virtmlops\Scripts\activate (windows)

# 3️⃣ Batir les images
docker-compose build

# 4️⃣ Initialiser les données
dvc pull

# 5️⃣ Démarrer l'infrastructure
docker-compose up -d
```

### Accès aux Services

| Service | URL | Description |
|---------|-----|-------------|
| 🔐 Authentication | `http://localhost:8000` | API d'authentification JWT |
| 🚀 Inference API | `http://localhost:8001` | Prédictions en temps réel |
| 🔬 MLflow UI | `http://localhost:5000` | Suivi des expériences |
| 📊 Prometheus | `http://localhost:9090` | Métriques système |
| 📈 Grafana | `http://localhost:3000` | Dashboards de monitoring |
| ⚡ Prefect UI | `http://localhost:4200` | Orchestration des workflows |

## 🔄 Pipeline CI/CD

### GitHub Actions Workflow

```mermaid
graph LR
    A[📝 Code Push/PR] --> B[🧪 Unit Tests]
    B --> C{✅ Tests Pass?}
    C -->|❌ Fail| D[🚫 Block Pipeline]
    C -->|✅ Pass| E[🏗️ Build Docker Images]
    E --> F[📦 Push to Docker Hub]
    F --> G[🎉 Deployment Ready]
    
    subgraph "🐳 Services Built"
        S1[Authentication]
        S2[Preprocessing] 
        S3[Model Training]
        S4[Evaluation]
        S5[Inference]
        S6[Patient Data Pull]
        S7[Prefect Orchestrator]
    end
    
    E -.-> S1
    E -.-> S2
    E -.-> S3
    E -.-> S4
    E -.-> S5
    E -.-> S6
    E -.-> S7
    
    style A fill:#e3f2fd
    style B fill:#f3e5f5
    style C fill:#fff3e0
    style E fill:#e8f5e8
    style F fill:#f1f8e9
    style G fill:#e8eaf6
    style D fill:#ffebee
```

## 📊 Monitoring & Observabilité
```mermaid

graph LR
    subgraph Business["Business Metrics"]
        BM[Model Performance<br/>Accuracy & Latency<br/>Drift Detection]
    end
    
    subgraph Technical["Technical Metrics"]
        TM[System Health<br/>API Performance<br/>Resource Usage]
    end
    
    subgraph User["User Metrics"]
        UM[Authentication<br/>API Usage<br/>Error Rates]
    end
    
    BM --> MONITORING[Monitoring Platform]
    TM --> MONITORING
    UM --> MONITORING
    
    MONITORING --> PROM[Prometheus<br/>Collection]
    MONITORING --> GRAF[Grafana<br/>Visualization]
    
    style Business fill:#e8f5e8
    style Technical fill:#fff3e0
    style User fill:#e3f2fd
    style MONITORING fill:#f3e5f5
    style PROM fill:#FF6B6B
    style GRAF fill:#4ECDC4
```



---

<div align="center">




</div>

---

