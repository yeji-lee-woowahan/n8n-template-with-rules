# 서버 개발 요청 API 명세서

프론트엔드에서 필요한 API 중 서버 측 추가/변경이 필요한 항목을 정리합니다.
타입·필드명은 참고용이며, 서버 컨벤션에 맞게 조정해 주세요.

---

## 1. 템플릿 목록 조회 필터/정렬 추가

**`GET /api/templates`** (기존 API 변경)

현재 pageable 파라미터만 지원하고 있는데, 아래 필터 파라미터와 정렬 옵션 추가가 필요합니다.
"내 템플릿" 조회는 기존 `GET /api/templates/mine`을 그대로 사용합니다.

### 추가 Query 파라미터

| 파라미터 | 설명           | 비고     |
| -------- | -------------- | -------- |
| keyword  | 제목/설명 검색 | optional |

### 정렬 지원

| sort 값        | 의미                     |
| -------------- | ------------------------ |
| viewCount,desc | 인기순 (조회수 내림차순) |
| createdAt,desc | 최신순 (기본값)          |

### 응답 타입 정의 필요

현재 `GET /api/templates`와 `GET /api/templates/mine`의 응답이 OpenAPI 스펙에 정의되어 있지 않아서
orval이 `{ [key: string]: unknown }` 타입을 생성합니다.
아래와 같은 paginated 응답 스키마를 OpenAPI에 정의해 주세요.

| 필드          | 타입                        | 설명         |
| ------------- | --------------------------- | ------------ |
| content       | TemplateDetailResponse[]    | 템플릿 목록  |
| totalElements | number                      | 전체 건수    |
| totalPages    | number                      | 전체 페이지  |
| size          | number                      | 페이지 크기  |
| number        | number                      | 현재 페이지  |

---

## 2. 템플릿 수정 API — OpenAPI 스펙 추가

**`PUT /api/templates/:id`** (기존 API 스펙 누락)

### 요청 Body (참고)

| 필드          | 설명                    | 비고                            |
| ------------- | ----------------------- | ------------------------------- |
| title         | 제목                    | required                        |
| description   | 설명                    | optional                        |
| jsonContent   | n8n 워크플로우 JSON     | required                        |
| manualTimeMin | 수동 작업 소요 시간(분) | required                        |

> authorId는 인증 정보에서 자동으로 가져오므로 Body에 포함하지 않습니다.

### 응답

- **200**: 수정된 템플릿 상세 (기존 TemplateDetailResponse 구조)
- **404**: 템플릿 없음

---

## 3. 노드 스펙 활성/비활성 전환 — 신규 API

**`PATCH /api/admin/node-specs/:id/status`** (신규)

관리자가 노드 스펙을 활성/비활성 전환할 수 있는 API입니다.

### Path

| 파라미터 | 설명         |
| -------- | ------------ |
| id       | 노드 스펙 ID |

### 요청 Body

| 필드     | 설명      | 비고     |
| -------- | --------- | -------- |
| isActive | 활성 여부 | required |

### 응답

- **200**: isActive가 변경된 노드 스펙 (기존 NodeSpecResponse 구조)
- **404**: 노드 스펙 없음

---

## 4. 템플릿 응답 확장 필드 추가

현재 서버 응답(TemplateDetailResponse)에 아래 필드가 없어서, 목록 조회 시 프론트에서 표시할 수 없습니다.
서버 응답에 추가해 주시면 됩니다.

| 필드     | 설명                | 비고     |
| -------- | ------------------- | -------- |
| userName | 등록자 표시 이름    | optional |
| userCn   | 등록자 ID (사번 등) | optional |

---

## 5. 워크플로우 검증 응답 타입 정의

**`POST /api/workflows/validate`** (기존 API 스펙 보완)

현재 OpenAPI 스펙에 응답 스키마가 정의되어 있지 않아 orval이 `{ [key: string]: string }` 타입을 생성합니다.
아래와 같이 응답 스키마를 정의해 주세요.

### 응답 Body

| 필드    | 타입    | 설명           |
| ------- | ------- | -------------- |
| valid   | boolean | 검증 통과 여부 |
| message | string  | 결과 메시지    |

---

## 우선순위 요약

| 순서 | API                                      | 설명                                                   |
| ---- | ---------------------------------------- | ------------------------------------------------------ |
| 1    | `PATCH /api/admin/node-specs/:id/status` | 노드 활성/비활성 전환 (신규)                           |
| 2    | `GET /api/templates` 필터/정렬           | keyword 필터 + 인기순 정렬 + 응답 타입 정의            |
| 3    | `PUT /api/templates/:id`                 | OpenAPI 스펙 추가 (authorId는 인증에서 자동)           |
| 4    | 템플릿 응답 확장 필드                    | userName, userCn                                       |
| 5    | `POST /api/workflows/validate` 응답 타입 | 응답 스키마 정의 (valid, message)                      |

---

_Last Updated: 2026-04-15_
