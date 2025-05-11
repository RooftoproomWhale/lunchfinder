# 🍱 밥은 먹고 다니냐 (LunchFinder)

위치 기반으로 점심 메뉴를 추천해주는 Spring Boot 기반 사이드 프로젝트입니다.  
매일 점심 메뉴 고민하는 개발자들의 루틴을 줄이기 위해 만들어졌습니다.

---

## 🧩 프로젝트 개요

- **프로젝트명**: 밥은 먹고 다니냐
- **목표**: 현재 위치를 기반으로 주변 음식점을 등록하고, 추천해주는 MVP 수준의 실용 앱
- **특징**: CQRS 설계 + Soft Delete + PostGIS 반경 검색

---

## 📌 기획 배경

> “점심 뭐 먹지?” 라는 고민을 줄여보자.

- 최소한의 입력으로 음식점 등록
- 위치 기반으로 주변 음식점 조회
- 이후에는 랜덤 추천 + 선호도 기반 추천까지 확장 예정

---

## 🛠️ 기술 스택

| 항목 | 기술 | 선택 이유 |
|------|------|-----------|
| Language | Java 21 | 최신 LTS, Record / Pattern Matching 실습 |
| Framework | Spring Boot 3.x | Jakarta EE 기반 최신 구조 학습 |
| DB | PostgreSQL + PostGIS | 거리 기반 검색 성능 및 정확도 확보 |
| ORM | JPA + Querydsl | CRUD는 JPA, 조건 검색은 Querydsl |
| 인증 | Spring Security + JWT | 세션 없는 토큰 기반 인증 |
| 지도 | Kakao Map JS SDK | 지도 기반 위치 선택 UX 구현 |
| 문서화 | Springdoc OpenAPI 3 | Swagger 기반 자동 API 문서화 |
| 배포 | Fly.io / Render.com | 무료 + Docker 기반 빠른 배포 경험 |

---

## 📁 프로젝트 구조 (CQRS 설계 기준)

```bash
lunchfinder
├── restaurant/
│   ├── command/
│   │   ├── controller/
│   │   ├── service/
│   │   └── dto/
│   ├── query/
│   │   ├── controller/
│   │   ├── service/
│   │   └── dto/
│   ├── domain/
│   └── repository/
├── auth/
├── common/
├── config/
```

---

## ✨ 주요 기능

| 기능 | 설명 | 사용 이유 |
|------|------|-----------|
| 음식점 등록 | 지도 클릭 후 이름/주소 등 입력 | 간편한 위치 기반 UX |
| 음식점 조회 | 현재 위치 기준 반경 내 조회 | PostGIS + 거리 필터링 |
| 지도 뷰 | 마커 기반 음식점 시각화 | Kakao Map SDK 사용 |
| 음식점 삭제 | Soft Delete 적용 | 데이터 보존 및 복구 고려 |
| 회원가입 / 로그인 | JWT 인증 적용 | 세션 없는 API 기반 인증 |
| 식별자 생성 | Snowflake ID | 전역 고유성 확보, 정렬 가능 |

