📁 S3 프로젝트 IAM 역할 및 권한 구조

이 문서는 S3 중간 프로젝트에서 팀원들의 업무 역할에 따라 IAM 권한을 어떻게 구성하고 부여했는지를 정리한 내용

🧭 IAM 구조 다이어그램

S3 프로젝트 IAM 권한 구조
└── 관리자 (팀장 - kdt001)
    ├── 권한: AdministratorAccess
    ├── IAM 그룹 관리
    └── IAM 정책 할당 / 사용자 권한 위임

    ├── IAM 그룹: KDT-Common
    │   ├── 권한:
    │   │   ├─ IAMReadOnlyAccess
    │   │   ├─ EC2/VPC/S3/SSM Describe 권한
    │   │   └─ CloudWatchReadOnlyAccess
    │   └── 구성원: kdt017, kdt018, kdt019

    ├── IAM 그룹: Web-EC2Access
    │   ├── 권한:
    │   │   └─ EC2 인스턴스 시작/중지/조회
    │   └── 구성원: kdt017

    ├── IAM 그룹: WAS-TomcatAccess
    │   ├── 권한:
    │   │   ├─ EC2 제어 (WAS용)
    │   │   ├─ SSM StartSession
    │   │   └─ IAM 읽기
    │   └── 구성원: kdt018

    ├── IAM 그룹: DB-RDSAccess
    │   ├── 권한:
    │   │   ├─ RDS 전체 제어
    │   │   └─ CloudWatch 모니터링
    │   └── 구성원: kdt019

    └── 모든 사용자 공통 개별 권한:
        └── IAMUserChangePassword

📋 그룹별 역할 요약

IAM 그룹명

설명

부여 권한

구성원

KDT-Common

공통 조회/모니터링

IAMReadOnly, Describe 권한, CloudWatch Read

모든 팀원

Web-EC2Access

Web 서버 EC2 제어

EC2 Start/Stop/Describe

kdt017

WAS-TomcatAccess

WAS + SSM + IAM 읽기

EC2, SSM 세션, IAM 읽기

kdt018

DB-RDSAccess

RDS 제어 및 모니터링

RDS*, CloudWatch

kdt019

✅ 권한 부여 방식

IAM 사용자 별로 공통 그룹 + 역할별 그룹을 조합하여 구성

역할 변경이 생길 경우 IAM 그룹 이동만으로 권한 제어 가능

사용자별 IAMUserChangePassword 권한은 인라인 또는 별도 정책으로 적용

이 구조는 팀 운영 중 변경 가능하며, 필요시 추가 역할 또는 권한을 동적으로 구성할 수 있음
