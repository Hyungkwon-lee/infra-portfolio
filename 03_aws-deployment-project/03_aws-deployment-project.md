# AWS Deployment Project

Jenkins 기반 CI/CD 파이프라인을 구성하여  
AWS 환경에서 애플리케이션 배포 자동화를 구현한 프로젝트입니다.

본 단계에서는 코드 변경 이후 빌드, 이미지 생성, 배포까지의 과정을 자동화하여  
반복 가능한 서비스 배포 환경을 구성하는 것을 목표로 하였습니다.

---

## Project Overview

AWS Deployment Project는 2차 프로젝트의 세 번째 단계로,  
AWS 환경에서 애플리케이션 배포 과정을 자동화하는 것을 목표로 진행하였습니다.

이 단계에서는 단순한 애플리케이션 실행이 아닌,  
코드 변경 이후 빌드, 이미지 생성, 배포까지 이어지는  
CI/CD 기반 운영 흐름을 구성하는 데 중점을 두었습니다.

이를 위해 Jenkins를 중심으로  
GitHub, Docker Hub, Amazon S3, AWS CodeDeploy, AWS WAS 환경을 연동하여  
자동 배포가 가능한 운영 구조를 구성하였습니다.

---

## Project Objectives

- Jenkins 기반 CI/CD 파이프라인 구성
- GitHub 연동 및 자동 빌드 구성
- Docker 이미지 생성 및 배포 자산 구성
- Amazon S3 및 AWS CodeDeploy 기반 배포 자동화
- 반복 가능한 애플리케이션 배포 구조 설계

---

## Environment Overview

본 프로젝트는 AWS 환경에서 애플리케이션 배포 자동화를 위한  
운영 흐름을 구성하는 것을 중심으로 진행하였습니다.

주요 구성 요소는 다음과 같습니다.

- Jenkins
- GitHub
- Docker
- Docker Hub
- Amazon S3
- AWS CodeDeploy
- AWS WAS Server
- Spring PetClinic

각 구성 요소를 연계하여  
코드 변경부터 서비스 반영까지 자동으로 이어지는 배포 흐름을 구성하였습니다.

---

## Key Components

### Jenkins Pipeline
애플리케이션 배포 자동화를 위해  
Jenkins 기반 Pipeline을 구성하였습니다.

- Pipeline Job 구성
- Jenkinsfile 기반 단계 분리
- Build / Package / Deploy 흐름 구성
- 배포 흐름 검증

---

### GitHub Integration
소스 변경 감지를 위해  
GitHub Repository와 Jenkins를 연동하였습니다.

- Source Repository 연동
- GitHub Webhook 구성
- 자동 빌드 트리거 구성

코드 변경 이후 수동 개입 없이  
자동으로 배포 흐름이 시작되도록 구성하였습니다.

---

### Build and Package
애플리케이션 배포를 위해  
빌드 및 배포 자산 생성 흐름을 구성하였습니다.

- 애플리케이션 빌드
- Docker Image Build
- Version Tag 적용
- 배포 파일 패키징

배포 시점마다 새로운 빌드 결과와 배포 자산을 생성하고  
반복 가능한 형태로 관리할 수 있도록 구성하였습니다.

---

### Deployment Flow
최종적으로 AWS WAS 환경에  
애플리케이션을 자동 배포할 수 있도록 배포 흐름을 구성하였습니다.

- 배포 파일 생성
- Amazon S3 업로드
- AWS CodeDeploy 연동
- WAS Server 배포
- 서비스 반영 검증

빌드 완료 이후 배포 자산을 Amazon S3로 전달하고,  
AWS CodeDeploy를 통해 AWS WAS 환경에 자동 반영되도록 구성하였습니다.

---

## Troubleshooting Summary

애플리케이션 배포 자동화 단계에서는  
배포 흐름 구성보다 Jenkins와 AWS 서비스 간 권한 및 배포 대상 구성을 먼저 정리해야 했습니다.

초기에는 EC2 공통 IAM Role을 기준으로 Jenkins를 구성하였으나,  
CodeDeploy 실행에 필요한 권한이 포함되어 있지 않아  
배포 단계가 정상적으로 진행되지 않는 문제가 있었습니다.

이후 Jenkins 전용 IAM Role을 분리하여  
CodeDeploy 권한을 별도로 구성하고 Jenkins 서버에 적용하였습니다.

또한 S3와 CodeDeploy를 연계하는 과정에서  
배포에 필요한 S3 Bucket, CodeDeploy Application, Deployment Group은  
별도로 구성하여 배포 흐름을 우선 검증하였습니다.

---

## Implementation Summary

본 단계에서는 Jenkins를 중심으로  
애플리케이션 배포 자동화 흐름을 구성하였습니다.

GitHub Repository와 Jenkins를 연동하여  
코드 변경 시 자동으로 빌드가 시작되도록 구성하였고,  
Jenkins Pipeline을 통해 Build, Package, Deploy 단계를 연결하였습니다.

이후 애플리케이션 빌드와 Docker 이미지 생성을 수행하고,  
배포 자산을 구성하여 Amazon S3로 전달한 뒤  
AWS CodeDeploy를 통해 WAS 서버에 자동 배포되도록 구성하였습니다.

이를 통해 코드 변경 이후  
수동 작업 없이 반복 가능한 애플리케이션 배포 흐름을 구성할 수 있었습니다.

---

## Result

본 프로젝트를 통해 AWS 환경에서  
애플리케이션 배포 자동화 흐름을 구성하였습니다.

Jenkins 기반 CI/CD 파이프라인을 통해  
코드 변경 이후 빌드, 패키징, 배포까지의 과정을 자동화하였으며,  
Amazon S3와 AWS CodeDeploy를 연계하여  
반복 가능하고 일관된 서비스 배포 환경을 구성할 수 있었습니다.

이를 통해 인프라 자동화 이후  
실제 서비스 운영 단계까지 이어지는 자동화 흐름을 완성하였습니다.

---

## Related Documents

- Pipeline Flow *(To be added)*
- Deployment Process *(To be added)*
- Troubleshooting Notes *(To be added)*

---

## Source Repository

`Repository Link`

---