# 🚀 MSA 기반 AWS 클라우드 인프라 & GitOps 배포 시스템

> Terraform + EKS + GitHub Actions + ArgoCD 기반  
> **완전 자동화된 MSA 서비스 배포 환경 구축 프로젝트**

---

## 📌 프로젝트 개요

본 프로젝트는 AWS 클라우드 환경에서 MSA(Microservice Architecture)를 기반으로  
**인프라부터 애플리케이션까지 자동으로 배포되는 GitOps 시스템**을 구축하는 것을 목표로 합니다.

- 인프라: Terraform 기반 코드형 인프라(IaC)
- 플랫폼: Amazon EKS (Kubernetes)
- CI/CD: GitHub Actions + ArgoCD
- 아키텍처: MSA 기반 서비스 구조

---

## 🏗️ 전체 아키텍처

~~~text
[ GitHub ]
    ↓ (Push / PR)
[ GitHub Actions ]
    ↓ (CI/CD)
[ ECR (Docker Image) ]
    ↓
[ ArgoCD ]
    ↓
[ EKS Cluster ]
    ↓
[ MSA Services (Pod) ]
~~~

---

## ⚙️ 기술 스택

### ☁️ Cloud / Infra
- AWS (VPC, EKS, RDS, ECR, IAM)
- Terraform

### 🚀 CI/CD
- GitHub Actions
- ArgoCD (GitOps)

### 🐳 Container / Orchestration
- Docker
- Kubernetes (EKS)

### 💻 Backend / Frontend
- MSA 구조 서비스 (Gateway, Member, Order, Product 등)
- HTML / CSS / JS 기반 Frontend

---

## 📁 프로젝트 구조

~~~text
team_project_msa-main/
│
├── terraform/                # 인프라 코드
│   ├── environments/
│   └── modules/
│
├── msa/                      # MSA 서비스
│   ├── apigateway/
│   ├── member/
│   ├── order/
│   └── product/
│
├── k8s/                      # Kubernetes YAML
│   ├── deployment/
│   ├── service/
│   └── ingress/
│
├── argocd/                   # ArgoCD 설정
│   └── applications/
│
├── .github/workflows/        # GitHub Actions CI/CD
│
└── README.md
~~~

---

## 🔄 CI/CD 파이프라인

### 1. 코드 변경
- GitHub Push 또는 PR 발생

### 2. GitHub Actions 실행
- Docker Image Build
- ECR Push
- Kubernetes 배포 트리거

### 3. ArgoCD
- Git 상태 감지
- 자동 Sync (배포)

👉 **코드 변경 → 자동 배포까지 완전 자동화**

---

## ☁️ 인프라 구성

### 🌐 VPC 구조
- Public Subnet
  - ALB / NAT Gateway / Bastion
- Private App Subnet
  - EKS Worker Node
- Private DB Subnet
  - RDS (MySQL)

---

### 🐳 EKS 구성
- Private Subnet 기반 Cluster
- Node Group 구성
- Ingress Controller (Nginx)

---

### 🗄️ 데이터베이스
- RDS (MySQL)
- Private Subnet 배치 (외부 접근 차단)

---

## 🔐 보안 설계

- IAM Role 기반 권한 관리
- OIDC 기반 GitHub Actions 인증
- Security Group 최소 권한 설정
- Bastion Host 통한 내부 접근

---

## 📦 GitOps 전략

- ArgoCD를 통한 선언적 배포
- Git을 단일 Source of Truth로 사용
- 자동 Sync + Self-Healing

---

## 🧩 MSA 서비스 구성

| 서비스 | 역할 |
|--------|------|
| API Gateway | 외부 요청 라우팅 |
| Member | 사용자 관리 |
| Order | 주문 처리 |
| Product | 상품 관리 |

---

## 🚀 배포 흐름

~~~text
1. 코드 수정 후 Push
2. GitHub Actions 실행
3. Docker Image Build & Push (ECR)
4. ArgoCD Sync
5. Kubernetes 배포 완료
~~~

---

## ⚠️ 트러블슈팅 경험

### ❗ CSS 적용 안됨 문제
- 원인: 상대경로 사용 (`assets/style.css`)
- 해결: 절대경로로 변경 (`/assets/style.css`)

### ❗ EKS 노드 인식 안됨
- 원인: IAM Role / SSM 설정 문제
- 해결: Instance Role 및 정책 재설정

### ❗ Terraform Destroy 동작 안됨
- 원인: Remote State 미사용
- 해결: S3 + DynamoDB Backend 구성

---

## 📈 프로젝트 성과

- 인프라 자동화 (Terraform)
- 배포 자동화 (GitHub Actions + ArgoCD)
- GitOps 기반 운영 환경 구축
- MSA 구조 서비스 배포 성공

---

## 🔮 향후 개선 방향

- Helm Chart 적용
- HPA (Auto Scaling)
- Observability (Prometheus + Grafana)
- 서비스 메시 (Istio)

---

## 👨‍💻 팀 구성

- Backend: 3명
- Frontend: 1명
- Infra(System): 1명
