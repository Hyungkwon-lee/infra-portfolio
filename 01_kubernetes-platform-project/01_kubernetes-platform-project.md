# Kubernetes Platform Project

온프레미스 환경에서 Kubernetes 기반 서비스 운영 플랫폼을 구성하고,  
애플리케이션 배포를 위한 기본 실행 환경을 구축한 프로젝트입니다.

본 단계에서는 클라우드 이전 이전에 서비스가 안정적으로 동작할 수 있는  
기본 플랫폼 계층을 먼저 구성하고 검증하는 것을 목표로 하였습니다.

---

## Project Overview

Kubernetes Platform Project는 2차 프로젝트의 첫 번째 단계로,  
애플리케이션이 실행될 수 있는 온프레미스 기반 플랫폼 환경을 구성하는 것을 목표로 진행하였습니다.

이 단계에서는 단순히 Kubernetes Cluster를 구축하는 것에 그치지 않고,  
이후 AWS 확장 및 자동화 환경으로 이어질 수 있도록  
컨테이너 기반 서비스 운영 구조를 사전 검증하는 데 중점을 두었습니다.

---

## Project Objectives

- 온프레미스 기반 Kubernetes Cluster 구성
- Jenkins 기반 CI 환경 구성
- NFS 기반 스토리지 구성
- 컨테이너 기반 애플리케이션 실행 환경 검증
- AWS 확장 이전 플랫폼 계층 사전 검증

---

## Environment Overview

본 프로젝트는 온프레미스 환경에서 컨테이너 기반 서비스 운영을 위한  
기본 플랫폼 계층을 구성하는 것을 중심으로 진행하였습니다.

주요 구성 요소는 다음과 같습니다.

- Kubernetes Cluster
- Jenkins
- NFS Server
- Docker
- Spring PetClinic

각 구성 요소는 이후 AWS 환경 확장 및 배포 자동화 단계를 고려하여  
독립적으로 운영 가능한 형태로 구성하였습니다.

---

## Key Components

### Kubernetes Cluster
컨테이너 기반 애플리케이션 실행을 위한  
기본 오케스트레이션 환경을 구성하였습니다.

- Control Plane 구성
- Worker Node 구성
- 기본 워크로드 배포 테스트
- 서비스 실행 검증

---

### Jenkins
애플리케이션 빌드 및 배포 자동화를 위한  
기본 CI 서버를 구성하였습니다.

- Jenkins 설치
- 기본 프로젝트 구성
- GitHub 연동
- 빌드 환경 검증

---

### NFS Server
컨테이너 환경에서 필요한 공유 스토리지를 제공하기 위해  
NFS 기반 스토리지 서버를 구성하였습니다.

- NFS Server 구성
- 공유 디렉토리 구성
- 마운트 테스트
- 접근 검증

---

### Application Validation
플랫폼 환경 검증을 위해 Spring PetClinic 애플리케이션을 활용하여  
기본 실행 및 배포 테스트를 진행하였습니다.

- 애플리케이션 실행 테스트
- 컨테이너 기반 실행 검증
- 서비스 접근 테스트

---

## Troubleshooting Summary

애플리케이션 수정 이후 변경 사항이 즉시 반영되지 않는 문제가 있었습니다.  
초기에는 배포 과정 자체의 문제로 판단하였으나, 확인 결과 기존 이미지가 재사용되면서 변경 사항 반영이 지연되고 있었습니다.

이후 소스 수정, 이미지 재빌드, 재배포 순서로 배포 흐름을 다시 정리하였고,  
변경 사항이 정상적으로 반영되는 것을 확인하였습니다.

해당 과정은 이후 AWS 배포 자동화 단계에서도  
동일하게 이어지는 배포 흐름 검증 과정으로 활용하였습니다.

---

## Implementation Summary

본 단계에서는 Kubernetes 기반 플랫폼 환경을 우선 구성하고,  
애플리케이션 실행에 필요한 기본 요소를 순차적으로 검증하였습니다.

우선 Kubernetes Cluster를 구성하여  
컨테이너 기반 애플리케이션 실행 환경을 마련하였고,  
이후 Jenkins를 연동하여 기본 빌드 환경을 구성하였습니다.

또한 NFS Server를 별도로 구성하여  
컨테이너 환경에서 필요한 공유 스토리지를 제공하였으며,  
최종적으로 Spring PetClinic 애플리케이션을 활용하여  
플랫폼 계층의 기본 동작을 검증하였습니다.

이를 통해 이후 AWS 환경으로 확장하기 전,  
서비스 운영을 위한 기본 플랫폼 계층을 사전 검증할 수 있었습니다.

---

## Result

본 프로젝트를 통해 온프레미스 환경에서  
컨테이너 기반 서비스 운영을 위한 기본 플랫폼 계층을 구성하였습니다.

Kubernetes Cluster, Jenkins, NFS 기반의 실행 환경을 구성하고  
애플리케이션 실행 검증까지 완료함으로써,  
이후 AWS 인프라 자동화 및 배포 자동화 단계로 확장할 수 있는 기반을 마련하였습니다.

---

## Related Documents

- Architecture Diagram *(To be added)*
- Deployment Flow *(To be added)*
- Troubleshooting Notes *(To be added)*

---

## Source Repository

`Repository Link`

---