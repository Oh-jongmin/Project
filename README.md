# 🛠️ 중간 프로젝트 - AWS3팀

## 1. 🧭 프로젝트 개요

- **주제**: 3-Tier 기반 WEB-WAS-DB 인프라 환경 구축
- **플랫폼**: AWS
- **목표**:
  - Apache, Tomcat, MariaDB를 활용한 인프라 구성
  - Proxy 또는 mod_jk 기반의 Web-WAS 연동
  - 샘플 애플리케이션(Petclinic) 배포
  - 고가용성, 보안성, 확장성 고려
  - 선택사항: 도메인 연결, TLS/SSL 구성, 모니터링 적용

---

## 2. 👥 팀 구성

| 이름 | 역할 | 주요 업무 |
|------|------|-----------|
| 오종민 | 팀장 / 인프라 설계 | 전체 아키텍처 설계, 네트워크 구성, VPC 설정, 일정 관리 |
| 김지원 | 웹 서버 담당 | Apache 설치, Proxy 설정, 정적 리소스 제공 |
| 이수현 | WAS 담당 | Tomcat, OpenJDK 설치, 애플리케이션 배포, 연동 |
| 박준호 | DB 담당 | MariaDB 설치 및 연동, 사용자 및 권한 설정 |

---

## 3. 🗓️ 프로젝트 일정 (Gantt)

| 작업 항목 | 기간 |
|-----------|------|
| 요구사항 분석 및 설계 | 4/21 ~ 4/22 |
| WEB/WAS 인스턴스 구성 및 설치 | 4/23 ~ 4/24 |
| WEB-WAS 연동 설정 | 4/25 ~ 4/26 |
| DB 서버 구축 및 연동 | 4/27 ~ 4/28 |
| 애플리케이션 배포 및 테스트 | 4/29 ~ 4/30 |
| 확장 기능 구성 (TLS, 도메인 등) | 5/1 |
| 최종 점검 및 발표자료 준비 | 5/2 |

---

## 4. 🧰 세부 기술 스택

| 계층 | 구성 요소 | 주요 기술 | 설명 |
|------|-----------|------------|------|
| **WEB** | Web Server | Apache HTTP Server (v2.4+) | 클라이언트 요청 처리, Proxy 또는 mod_jk 설정 |
|  | 연동 방식 | ProxyPass / mod_jk | Web-WAS 간 리버스 프록시 또는 AJP 연동 |
| **WAS** | WAS Server | Apache Tomcat | Java 기반 동적 웹 애플리케이션 처리 |
|  | Java Runtime | OpenJDK 11+ | Tomcat 실행에 필요 |
|  | 애플리케이션 | Petclinic | Java 기반 샘플 애플리케이션 |
| **DB** | Database | MariaDB | 관계형 데이터베이스, JDBC 연동 |
|  | 연동 방식 | JDBC | Tomcat <-> DB 연결 |
| **공통 인프라** | CSP | AWS | EC2 기반 구성 |
|  | 네트워크 | VPC, Subnet, ACG, NACL | 계층 분리 및 보안 설정 |
|  | 도메인 (옵션) | Route 53 | 사용자 지정 도메인 연결 |
|  | 인증 (옵션) | TLS/SSL | HTTPS 적용 (Let’s Encrypt 등) |
|  | 모니터링 (옵션) | CloudWatch, 로그 수집 | 상태 모니터링, Alert 구성 |

---

## 5. 📌 비고

- 프로젝트 샘플 애플리케이션으로 [Petclinic](https://github.com/spring-projects/spring-petclinic) 사용
- 각 단계별 테스트 및 로그는 `/logs` 디렉터리에 정리 예정
- 발표 자료 및 Gantt Chart는 `/docs` 폴더에 별도 업로드 예정

---

## 🔗 슬로건

> "Run, Do, Share" – 실행하고, 나누는 인프라 구축 여정
