# Kubernetes Platform Project

온프레미스 쿠버네티스 클러스터 환경에서 Jenkins 커스텀 이미지를 직접 설계하고,
GitHub → Maven → Docker Hub → kubectl 흐름의 CI/CD 파이프라인을 구현한 프로젝트입니다.

→ 상세 문서: [kubernetes-platform-project](https://github.com/Hyungkwon-lee/kubernetes-platform-project)

---

## 1. 목표

온프레미스 환경에서 컨테이너 기반 CI/CD 파이프라인을 직접 구축하고,
이후 AWS 클라우드 환경으로 확장하기 전 플랫폼 계층을 사전 검증합니다.

---

## 2. 환경 구성

| 구분 | 내용 |
|------|------|
| Master Node | 1대 |
| Worker Node | 3대 |
| NFS Server | 1대 (별도, PV 스토리지 전용) |
| CNI | Calico |
| Load Balancer | MetalLB |
| Ingress | ingress-nginx |

---

## 3. 담당 작업

- NFS 서버 구축 및 Worker Node 마운트 설정
- Jenkins 커스텀 Docker 이미지 설계 및 빌드
- Jenkins / WAS 전체 K8s 매니페스트 작성
- Jenkinsfile 작성 (5단계 CI/CD 파이프라인 전체)

---

## 4. CI/CD 흐름

GitHub (main) → Maven Build → Docker Build → Docker Hub Push → kubectl rolling update

---

## 5. 트러블슈팅

**이미지 캐시로 인한 변경사항 미반영**

소스 수정 후 재배포했지만 변경사항이 반영되지 않는 문제가 발생했습니다.
원인은 `imagePullPolicy` 설정으로 인해 기존 이미지가 재사용된 것이었습니다.
이후 소스 수정 → 이미지 재빌드 → 재배포 순서로 흐름을 정리하고,
`imagePullPolicy: Always` 설정을 명시해 해결했습니다.

---

## 6. 기술 스택

`Kubernetes` `Jenkins` `Docker` `Docker Hub` `Maven` `Spring-PetClinic`
`MetalLB` `ingress-nginx` `NFS` `Calico`
