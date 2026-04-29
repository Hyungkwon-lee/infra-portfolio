# Ansible IaC Project

AWS 환경에서 인프라를 코드로 관리하기 위해  
Ansible 기반 Infrastructure as Code(IaC) 환경을 구성한 프로젝트입니다.

본 단계에서는 수동 리소스 생성이 아닌,  
반복 가능하고 일관된 방식으로 AWS 인프라를 구성할 수 있는 자동화 기반을 구축하는 것을 목표로 하였습니다.

---

## Project Overview

Ansible IaC Project는 2차 프로젝트의 두 번째 단계로,  
AWS 환경에서 서비스 운영에 필요한 인프라를 코드로 구성하고 자동화하는 것을 목표로 진행하였습니다.

기존 온프레미스 환경에서 검증한 서비스 구조를 AWS 상에 재현하기 위해  
네트워크와 서버 구성을 수동으로 생성하는 대신,  
Ansible 기반 자동화 구성을 통해 반복 가능한 인프라 배포 환경을 구성하였습니다.

---

## Project Objectives

- AWS 인프라 자동화 환경 구성
- Ansible 기반 Infrastructure as Code(IaC) 구현
- AWS 네트워크 구성 자동화
- 서버 배포 자동화 기반 구성
- 반복 가능한 인프라 배포 구조 설계

---

## Environment Overview

본 프로젝트는 AWS 환경에서 서비스 운영을 위한  
기본 인프라 계층을 자동화하는 것을 중심으로 진행하였습니다.

주요 구성 요소는 다음과 같습니다.

- Ansible
- AWS VPC
- Public Subnet
- Private Subnet
- Internet Gateway
- NAT Gateway
- Route Table
- Security Group
- EC2

각 리소스는 Ansible 기반으로 분리 및 구성하여  
반복 가능하고 일관된 방식으로 배포할 수 있도록 설계하였습니다.

---

## Key Components

### Ansible
AWS 인프라 자동화를 위한  
기본 구성 관리 도구로 Ansible을 사용하였습니다.

- Playbook 기반 구성
- Role 기반 구조 분리
- 변수 기반 리소스 관리
- 반복 가능한 인프라 구성

---

### Network Architecture
AWS 상에서 서비스 운영을 위한  
기본 네트워크 구조를 구성하였습니다.

- VPC 구성
- Public Subnet 2개 구성
- Private Subnet 2개 구성
- Internet Gateway 연결
- NAT Gateway 구성
- Route Table 분리 구성

외부 접근이 필요한 리소스와 내부 서비스 리소스를 분리하여  
기본적인 네트워크 보안 구조를 적용하였습니다.

---

### Security Configuration
서비스 접근 제어를 위해  
Security Group 기반 보안 구성을 적용하였습니다.

- Jenkins 접근 제어
- WAS 접근 제어
- 내부 통신 허용
- 서비스 포트 분리

각 리소스의 접근 범위를 역할에 따라 분리하여  
기본적인 접근 제어 구조를 구성하였습니다.

---

### Compute Resources
서비스 운영을 위한  
기본 EC2 인스턴스를 구성하였습니다.

- Jenkins Server 구성
- WAS Server 구성
- Private Subnet 기반 서비스 배치

서비스 서버는 외부 직접 노출 없이  
Private Subnet 내부에서 운영되도록 구성하였습니다.

---

## Troubleshooting Summary

AWS 인프라를 Ansible로 구성하는 과정에서  
Auto Scaling Group과 라우팅 구성에서 문제가 발생하였습니다.

초기 Auto Scaling Group 구성 시 Health Check 기준을 ELB로 설정하였으나,  
Target Group에 연결된 EC2가 정상 상태로 유지되지 않아  
인스턴스가 반복적으로 생성되고 제거되는 문제가 발생하였습니다.

초기 구축 단계에서는 안정적인 인스턴스 유지를 우선하기 위해  
Health Check 기준을 EC2로 변경하여 Auto Scaling Group이 정상적으로 유지되도록 수정하였습니다.

또한 Public / Private Route Table을 루프 구조로 한 번에 생성하고  
각 Subnet에 연결하려 했으나, 의도한 라우팅 연결이 정상적으로 적용되지 않는 문제가 있었습니다.

이후 Public Route Table과 Private Route Table 구성을 분리하고,  
각 Subnet에 명시적으로 연결하는 방식으로 수정하여  
Public / Private 라우팅 경로가 정상적으로 적용되도록 정리하였습니다.

---


## Implementation Summary

본 단계에서는 AWS 상에서 서비스 운영에 필요한  
기본 인프라 계층을 Ansible 기반으로 자동화하였습니다.

우선 VPC와 Subnet을 구성하여  
서비스 운영을 위한 기본 네트워크 구조를 마련하였고,  
Internet Gateway 및 NAT Gateway를 통해  
외부 접근과 내부 통신 경로를 분리하였습니다.

이후 Security Group을 통해 리소스별 접근 정책을 분리하고,  
Jenkins 및 WAS 서버를 EC2 기반으로 구성하여  
서비스 운영을 위한 기본 인프라 계층을 완성하였습니다.

모든 리소스는 Ansible Playbook 및 Role 기반으로 구성하여  
수동 작업 없이 반복적으로 동일한 환경을 배포할 수 있도록 설계하였습니다.

---

## Result

본 프로젝트를 통해 AWS 환경에서  
서비스 운영을 위한 기본 인프라 계층을 코드로 자동화하였습니다.

Ansible 기반으로 네트워크 및 서버 구성을 자동화함으로써,  
반복 가능하고 일관된 인프라 배포 환경을 구성할 수 있었으며,  
이후 배포 자동화 단계로 확장할 수 있는 기반을 마련하였습니다.

---

## Related Documents

- Architecture Diagram *(To be added)*
- Role Structure *(To be added)*
- Troubleshooting Notes *(To be added)*

---

## Source Repository

`Repository Link`

---