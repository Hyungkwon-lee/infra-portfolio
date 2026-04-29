# AWS Deployment Project

Jenkins 파이프라인으로 Docker 이미지를 빌드하고
S3 → CodeDeploy → EC2 흐름의 AWS 배포 자동화를 구현한 프로젝트입니다.

→ 상세 문서: [aws-deployment-project](https://github.com/Hyungkwon-lee/aws-deployment-project)

---

## 목표

코드 변경 이후 빌드, 이미지 생성, 배포까지의 과정을 자동화해
수동 개입 없이 반복 가능한 서비스 배포 환경을 구성합니다.

---

## 배포 흐름
'''
GitHub (main) → Maven Build → Docker Build
→ Docker Hub Push → S3 업로드 → CodeDeploy → EC2 배포
'''
---

## 담당 작업

- Jenkinsfile 작성 (8단계 CI/CD 파이프라인)
- appspec.yml 작성 (CodeDeploy 배포 훅 구성)
- 배포 스크립트 작성 (`kill_process.sh`, `run_process.sh`)
- Docker Compose 기반 컨테이너 실행 구성

---

## 트러블슈팅

**Jenkins IAM 권한 문제**

초기에 EC2 공통 IAM Role을 Jenkins에 적용했으나
CodeDeploy 실행 권한이 없어 배포 단계가 실패했습니다.
Jenkins 전용 IAM Role을 분리하고 `AWSCodeDeployFullAccess`를 추가해 해결했습니다.

---

## 기술 스택

`Jenkins` `Docker` `Docker Hub` `AWS CodeDeploy` `S3` `Maven` `Spring-PetClinic`
