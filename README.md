# infra-portfolio

온프레미스 + AWS 클라우드 기반 하이브리드 인프라 구축 포트폴리오입니다.  
부산 IT 아카데미 2차 프로젝트 (2026.03.25 ~ 04.27)

---

## 프로젝트 개요

온프레미스에서 운영되던 서비스를 AWS 클라우드로 확장하는 하이브리드 인프라 구성을 목표로 진행했습니다.  
온프레미스 K8s 기반 CI/CD → AWS 인프라 자동화(IaC) → AWS 배포 자동화 순서로 단계별로 구축했습니다.

---

## 구성도

![Architecture](./docs/architecture.png)

---

## 프로젝트 구성

### 01. Kubernetes Platform Project
온프레미스 쿠버네티스 클러스터 환경에서 Jenkins 커스텀 이미지를 직접 설계하고  
GitHub → Maven → Docker Hub → kubectl 흐름의 CI/CD 파이프라인을 구현했습니다.

| 항목 | 내용 |
|------|------|
| 환경 | On-Premise (Master 1 / Worker 3 / NFS Server) |
| 담당 | NFS 서버 구축, Jenkins 커스텀 이미지 설계, 전체 매니페스트 작성, Jenkinsfile 작성 |
| 기술 | Kubernetes, Jenkins, Docker, MetalLB, ingress-nginx, NFS |

→ [Repository](https://github.com/kwony93/01_kubernetes-platform-project)

---

### 02. Ansible IaC Project
Ansible Playbook으로 AWS 인프라 전체를 코드로 자동화했습니다.  
Role 단위로 모듈화하고 멱등성을 고려한 구성으로 반복 가능한 인프라 배포 환경을 구축했습니다.

| 항목 | 내용 |
|------|------|
| 환경 | AWS (VPC, EC2, ALB, ASG, IAM, CodeDeploy) |
| 담당 | 전체 Playbook 설계, Role 작성, MFA 기반 인증 구성 |
| 기술 | Ansible, AWS, amazon.aws, community.aws |

→ [Repository](https://github.com/kwony93/02_ansible-iac-project)

---

### 03. AWS Deployment Project
Jenkins 파이프라인으로 Docker 이미지를 빌드하고  
S3 → CodeDeploy → EC2 흐름의 AWS 배포 자동화를 구현했습니다.

| 항목 | 내용 |
|------|------|
| 환경 | AWS (Jenkins EC2, ASG, CodeDeploy, S3) |
| 담당 | Jenkinsfile 작성, appspec.yml 작성, 배포 스크립트 작성 |
| 기술 | Jenkins, Docker, Docker Hub, AWS CodeDeploy, S3 |

→ [Repository](https://github.com/kwony93/03_aws-deployment-project)

---

## 전체 기술 스택

`Kubernetes` `Jenkins` `Docker` `Ansible` `AWS`  
`MetalLB` `ingress-nginx` `NFS` `CodeDeploy` `S3` `ALB` `ASG`

---

## 발표 자료

- [프로젝트 결과 보고서 PDF](docs/Project-Result-Report.pdf)
