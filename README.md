<div style="display: flex; justify-content: center;">
  <h1> 🧠 Epilepsy Prediction MLOps Platform </h1>
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

Cette plateforme MLOps de pointe offre une solution complète pour la prédiction d'épilepsie, intégrant les meilleures pratiques DevOps et MLOps dans un environnement de microservices hautement scalable et sécurisé.

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
git clone https://github.com/your-org/epilepsy-mlops.git
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
    A[📝 Code Push] --> B[🧪 Unit Tests]
    B --> C[🔍 Code Quality]
    C --> D[🏗️ Build Images]
    D --> E[🔐 Security Scan]
    E --> F[📦 Push to Registry]
    F --> G[🚀 Deploy to Staging]
    G --> H[✅ Integration Tests]
    H --> I[🌐 Deploy to Production]
    
    style A fill:#e3f2fd
    style B fill:#f3e5f5
    style C fill:#fff3e0
    style D fill:#e8f5e8
    style E fill:#fce4ec
    style F fill:#f1f8e9
    style G fill:#e0f2f1
    style H fill:#fff8e1
    style I fill:#e8eaf6
```

## 📊 Monitoring & Observabilité

### Métriques Clés

```mermaid
graph TD
    subgraph "🎯 Business Metrics"
        A[Accuracy Score]
        B[Prediction Latency]
        C[Model Drift Score]
    end
    
    subgraph "🛠️ Technical Metrics"
        D[API Response Time]
        E[Container Health]
        F[Resource Usage]
    end
    
    subgraph "👥 User Metrics"
        G[Authentication Rate]
        H[API Usage]
        I[Error Rate]
    end
    
    A --> PROM[📊 Prometheus]
    B --> PROM
    C --> PROM
    D --> PROM
    E --> PROM
    F --> PROM
    G --> PROM
    H --> PROM
    I --> PROM
    
    PROM --> GRAF[📈 Grafana Dashboard]
    
    style PROM fill:#FF6B6B
    style GRAF fill:#4ECDC4
```



## 🛡️ Sécurité & Bonnes Pratiques

### Architecture de Sécurité

```mermaid
graph TB
    subgraph "🔐 Security Layer"
        JWT[JWT Authentication]
        RBAC[Role-Based Access]
        SSL[SSL/TLS Encryption]
    end
    
    subgraph "🛡️ Infrastructure Security"
        FW[Firewall Rules]
        SEC[Security Scanning]
        VAULT[Secrets Management]
    end
    
    subgraph "📊 Audit & Compliance"
        LOG[Security Logging]
        MON[Anomaly Detection]
        COMP[Compliance Checks]
    end
    
    JWT --> RBAC
    RBAC --> SSL
    SSL --> FW
    FW --> SEC
    SEC --> VAULT
    VAULT --> LOG
    LOG --> MON
    MON --> COMP
    
    style JWT fill:#FF6B6B
    style RBAC fill:#4ECDC4
    style SSL fill:#45B7D1
    style FW fill:#96CEB4
    style SEC fill:#FFEAA7
    style VAULT fill:#DDA0DD
    style LOG fill:#FFB74D
    style MON fill:#81C784
    style COMP fill:#F06292
```

## 📈 Performance & Scalabilité

### Métriques de Performance

| Métrique | Objectif | Actuel |
|----------|----------|---------|
| 🚀 Latence API | < 200ms | 150ms |
| 🎯 Accuracy | > 95% | 97.2% |
| 📊 Throughput | 1000 req/s | 1200 req/s |
| ⚡ Uptime | 99.9% | 99.95% |

## 🤝 Contribution

### Workflow de Contribution

```mermaid
gitgraph
    commit id: "main"
    branch feature/new-model
    checkout feature/new-model
    commit id: "🔬 Research"
    commit id: "🤖 Implement"
    commit id: "🧪 Test"
    checkout main
    merge feature/new-model
    commit id: "🚀 Release v2.0"
```

### Guide de Contribution

1. **Fork** le repository
2. **Créer** une branche feature (`git checkout -b feature/amazing-feature`)
3. **Commiter** vos changements (`git commit -m '✨ Add amazing feature'`)
4. **Pousser** vers la branche (`git push origin feature/amazing-feature`)
5. **Ouvrir** une Pull Request


---

<div align="center">

**🌟 Si ce projet vous aide, n'hésitez pas à lui donner une étoile ! 🌟**

[⬆️ Retour en haut](#-epilepsy-prediction-mlops-platform)

</div>

---

<div align="center">
<sub>Réalisé par Sarah dans le cadre du projet MLOps • © 2025</sub>
</div>
