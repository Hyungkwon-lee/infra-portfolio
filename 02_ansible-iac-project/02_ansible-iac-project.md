# Ansible IaC Project

Ansible Playbook으로 AWS 인프라 전체를 코드로 자동화한 프로젝트입니다.
Role 단위로 모듈화하고 멱등성을 고려해 반복 가능한 인프라 배포 환경을 구축했습니다.

→ 상세 문서: [ansible-iac-project](https://github.com/Hyungkwon-lee/02_ansible-iac-project)

---

## 목표

수동 리소스 생성 없이 Ansible 단일 명령으로
AWS 인프라 전체를 순차적으로 구축할 수 있는 환경을 구성합니다.

---

## 인프라 구성 흐름

```
network → iam → security → app_origin → jenkins → loadbalancer → asg
```

```bash
source scripts/token.sh {MFA_CODE}
ansible-playbook site.yml -e "action=main"
```

---

## 담당 작업

- AWS 인프라 전체 설계 및 Ansible Playbook 작성
- MFA 기반 STS 임시 Credential 인증 구성
- Role 단위 모듈화 및 멱등성 처리
- 구축/삭제 양방향 Playbook 구성

---

## 트러블슈팅

**ASG Health Check 충돌 문제**

ASG Health Check를 ELB로 설정했을 때, 초기 배포 상태에서 웹 서비스가 없어
ALB Health Check 실패 → EC2 비정상 판단 → 종료 후 재생성이 반복됐습니다.
EC2 Health Check로 변경해 인스턴스가 안정적으로 유지되도록 해결했습니다.
운영 환경에서는 nginx-proxy를 베이스로 설치해 ELB Health Check를 유지하는 방식이 더 적합합니다.

**Route Table 연결 문제**

Public/Private Route Table을 루프로 한 번에 생성하고 서브넷에 연결하려 했으나
라우팅이 의도한 대로 적용되지 않는 문제가 발생했습니다.
각 Route Table 구성을 분리하고 서브넷에 명시적으로 연결하는 방식으로 해결했습니다.

---

## 기술 스택

`Ansible` `AWS` `VPC` `EC2` `ALB` `ASG` `IAM` `CodeDeploy` `S3`
`amazon.aws 10.1.2` `community.aws 10.1.0`
