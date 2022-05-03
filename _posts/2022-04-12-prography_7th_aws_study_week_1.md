---
layout: post
title: "[AWS] 프로그라피 7기 AWS 스터디 1주차 학습 내용 정리"
subtitle: 🔖 1장. 클라우드와 아마존 웹 서비스 - 2장. 확장성과 안정성 높은 서버 만들기
categories: DevOps
tags: [AWS_Discovery_Book, 클라우드, EC2]
---

### 🧩 애플리케이션 구성

| 애플리케이션           |
| ---------------------- |
| 운영체제 (OS)          |
| 네트워크 (랜카드/랜선) |
| 스토리지 (HDD/SSD)     |
| 컴퓨팅 (CPU + RAM)     |

### ℹ️ 클라우드 컴퓨팅 서비스 이용 방식

- IaaS
  - Infrastructure as a Service
  - `물리적 서버, 네트워크, 스토리지` 즉, `인프라`를 제공해주는 서비스
  - 사용자는 가상 서버에 필요한 OS와 프로그램 직접 설치하여 사용 및 운영
  - ex) AWS의 EC2
- PaaS
  - Platform as a Service
  - `인프라 + OS + 미들웨어/런타임`을 제공해 주는 서비스
  - 웹/앱 서비스의 개발 및 실행을 위한 표준 환경을 제공해주기 때문에, 사용자는 제공되는 런타임 환경에서 개발에 집중할 수 있다
  - ex) AWS의 RDS, Elastic Beanstalk
- Serverless
  - `인프라 + OS + 런타임 + 애플리케이션 백엔드`를 제공해 주는 서비스
  - 개발에 필요한 대부분을 제공해주는 서비스
  - ex) AWS Lambda
- SaaS
  - Software as a Service
  - `인프라 + OS + 소프트웨어`를 제공해 주는 서비스
  - 서비스 자체를 제공해주기 때문에 사용자는 이용만 하면 된다
  - ex) AWS Gateway

### 📍 클라우드 용어

- 가용영역
  - 한 개 이상의 데이터 센터들의 모음
- 리전
  - 여러 개의 가용영역의 모음
  - 최소 2개의 가용영역으로 구성
- 엣지 로케이션
  - 캐시 서버들의 모음

### 🎁 EC2

- Elastic Compute Cloud
- EC2 생성 시 필요한 개념
  1. AMI
     1. Amazone Machine Image
     2. 인스턴스의 기반이 되는 이미지
     3. 사용자가 원하는 OS와 환경 구성된 서버를 선택해 사용 가능
     4. 사용자가 원하는 환경을 구성한 뒤 이미지로 만들어 사용도 가능
  2. EBS
     1. Elastic Block Store
     2. 서버용 하드디스크
     3. 가용 영역 내의 EC2 인스턴스에 연결되어 사용
     4. 필요시 용량 증가 가능
  3. 보안 그룹
     1. 보안을 위해 IP와 포트 번호를 이용하여 만든 서버 접속 규칙
  4. 키 페어
     1. 서버에 접속하기 위한 키
     2. AWS EC2에선 기본적으로 SSH 키 페어를 사용
        1. SSH? 네트워크를 통해 원격 시스템에 접근할 수 있는 프로토콜 및 프로그램
        2. Window에서는 PuTTY 클라이언트, macOS나 Linux에서는 ssh 명령어를 통해 접속
