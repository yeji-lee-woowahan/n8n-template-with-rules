# FSD 폴더 구조 (커스텀)

표준 FSD에서 `entities`, `widgets` 레이어를 생략한 간소화된 구조.

## 레이어 구조

```
n8n-template/src/
├── app/              # 앱 초기화, 전역 설정
├── pages/            # 페이지 컴포넌트
├── features/         # 도메인별 기능 (핵심)
└── shared/           # 공유 리소스
```

| 레이어 | 역할 | import 가능 대상 |
|--------|------|------------------|
| `app/` | 프로바이더, 라우터, 레이아웃, 전역 스타일 | pages, features, shared |
| `pages/` | 라우트별 페이지 컴포넌트 | features, shared |
| `features/` | 도메인별 UI + 로직 | shared, 다른 features |
| `shared/` | 공용 UI, 유틸, API, 상수 | 없음 (최하위) |

**역방향 의존 금지:**
- shared → features/pages/app 금지
- features → pages/app 금지
- pages → app 금지

**FSD alias 사용:**
- `@app`, `@pages`, `@features`, `@shared`
- 상대 경로(`../../../`) 대신 alias 사용

---

## app/ 구조

```
app/
├── layouts/          # 앱 레이아웃 (GNB, 사이드바 포함)
├── providers/        # React 프로바이더 (Query, Atelier)
├── routes/           # 라우터, 가드, 리다이렉트
└── styles/           # 전역 CSS (reset, fonts)
```

**app/layouts/ vs shared/ui/ 차이:**

| 항목 | `app/layouts/` | `shared/ui/` |
|------|----------------|--------------|
| 역할 | **앱 Shell** (네비게이션 구조) | **순수 UI 컴포넌트** |
| 포함 내용 | GNB, 사이드바, 라우팅 로직 | 스타일링만 (로직 없음) |
| 크기 | 대형 (300줄+) | 소형 (50줄 미만) |
| 예시 | `MainLayout` | `PageHeader`, `ContentWrapper` |

- `app/layouts/` = 라우터 최상위에서 페이지를 감싸는 **앱 구조**
- `shared/ui/` = 페이지 내부에서 사용하는 **재사용 가능한 UI 래퍼**

---

## pages/ 구조

```
pages/
├── home/             # 홈 페이지
├── mcp/              # MCP 목록, 상세, 등록/수정 페이지
├── myspace/          # MySpace 하위 페이지들
├── guide/            # 가이드 페이지
└── NotFoundPage.tsx  # 404 페이지
```

**라우트 매핑:**

| 경로 | 페이지 파일 |
|------|------------|
| `/` | `pages/home/HomePage.tsx` |
| `/mcp` | `pages/mcp/McpListPage.tsx` |
| `/mcp/:id` | `pages/mcp/McpDetailPage.tsx` |
| `/mcp/submit` | `pages/mcp/McpSubmitPage.tsx` |
| `/myspace` | `pages/myspace/MySpaceUsagePage.tsx` |
| `/myspace/registered` | `pages/myspace/MySpaceRegisteredPage.tsx` |
| `/myspace/review` | `pages/myspace/MySpaceReviewPage.tsx` |
| `/myspace/pat` | `pages/myspace/MySpacePatPage.tsx` |
| `/guide` | `pages/guide/GuidePage.tsx` |

- 페이지 파일명: `{Domain}{Action}Page.tsx` (예: `McpListPage.tsx`, `MySpaceUsagePage.tsx`)
- 페이지별 스타일: `PageName.module.scss` (같은 폴더)

---

## features/ 구조

**도메인 분류 기준: "무엇을 다루는가"** (사용되는 곳 기준 X)

```
features/
├── auth/             # 인증 (SSO, 가드, PAT)
├── home/             # 홈 (추천 MCP, 퀵가이드, FAQ)
├── mcp/              # MCP (카드, 검색, 등록폼)
└── myspace/          # MySpace (사용현황, 등록현황, 검토현황)
```

**각 도메인 내부 구조:**

```
features/{domain}/
├── components/       # UI 컴포넌트
├── modals/           # 모달 컴포넌트 (별도 분리)
├── hooks/            # 커스텀 훅
│   └── index.ts      # barrel export
├── context/          # React Context
│   └── index.ts      # barrel export
├── stores/           # Zustand 스토어
├── utils/            # 도메인 전용 유틸리티
├── mocks/            # 테스트용 목 데이터
├── types.ts          # 타입 정의
└── index.ts          # barrel export (필수)
```

**barrel export 규칙 (`index.ts`):**

```typescript
// Components
export { default as McpCard } from './components/McpCard';

// Hooks
export { useMcpSearch } from './hooks';

// Modals
export { default as McpDetailModal } from './modals/McpDetailModal';

// Types
export type { McpServer } from './types';
```

---

## shared/ 구조

```
shared/
├── api/              # API 관련
│   ├── generated/    # orval 자동 생성 (수정 금지)
│   ├── model/        # orval 자동 생성 타입 (수정 금지)
│   ├── axiosInstance.ts
│   └── tokenStorage.ts
├── constants/        # 상수 (색상, 사이즈, 상태값 등)
├── lib/              # 라이브러리 성격 유틸 (Context, 포맷터)
├── ui/               # 공용 UI 컴포넌트
│   └── index.ts      # barrel export
└── utils/            # 순수 유틸리티 함수
```

---

## 배치 판단 기준

| 상황 | 위치 | 예시 |
|------|------|------|
| MCP 목록에서만 쓰는 카드 컴포넌트 | `features/mcp/` | `McpCard` |
| 여러 도메인에서 쓰는 Badge | `shared/ui/` | `StatusBadge` |
| MySpace 페이지 전용 탭 | `features/myspace/` | `MySpaceTabs` |
| 앱 전역 레이아웃 | `app/layouts/` | `MainLayout` |
| 홈 페이지 | `pages/home/` | `HomePage` |
