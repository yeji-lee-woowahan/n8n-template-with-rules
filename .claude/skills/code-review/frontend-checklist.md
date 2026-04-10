# 프론트 코드리뷰 체크리스트

> - 체크리스트 형태로 딱딱 체크
> - ★★★★ 커밋 전 필수 / ★★★ 발견 시 수정
> - 설명은 최소화, 상세는 참조문서 링크로

---

## ★★★★ 커밋 전 필수

### 데이터 호출 (Colocation)
- [ ] **Prop Drilling 하지 않는다**: 자식이 직접 API 훅을 호출할 수 있는데, 부모가 가져와서 Props로 3단계 이상 내려주고 있지 않은가?
- [ ] **중복 호출을 두려워하지 않는다**: 서로 멀리 떨어진 컴포넌트에서 같은 데이터가 필요할 때, 억지로 상위로 끌어올리지 않고 각자 훅을 호출했는가? (React Query 캐싱이 네트워크 요청을 1회로 최적화함)
- [ ] 반복문 내부 호출 금지: 리스트 아이템(map 내부)에서는 API 훅을 호출하지 않고, 부모가 데이터를 받아서 Props로 내려주는가?

→ 상세: [상태관리.md](../design-review/상태관리.md#데이터-호출-원칙-colocation)

### 컴포넌트 구조
- [ ] **UI 컴포넌트 순수성**: `shared/ui/` 컴포넌트 내부에서 API 훅을 호출하지 않는다. UI 컴포넌트는 오직 Props만 받아서 렌더링해야 한다.
- [ ] **과한 추상화 금지**: 한 곳에서만 쓰이는데 굳이 Container.tsx와 View.tsx로 파일을 쪼개지 않았는가? 기본은 로직+UI를 한 파일에 작성한다.
- [ ] **도메인 컴포넌트 명확성**: API를 호출하는 컴포넌트의 이름에 비즈니스 맥락(Mcp, MySpace 등)이 포함되어 있는가?
- [ ] **인터페이스 깔끔함**: props가 5개 이상이면 객체로 묶는 것을 고려했는가? 반환값/props 인터페이스가 명확하고 예측 가능한가?

→ 상세: [컴포넌트-설계.md](../design-review/컴포넌트-설계.md#ui-컴포넌트-vs-도메인-컴포넌트)

### Suspense
- [ ] 단일 데이터 패칭에 Suspense 쿼리를 사용하지 않는다
- [ ] Suspense 사용 시 ErrorBoundary가 있다

→ 상세: [Suspense-규칙.md](./Suspense-규칙.md)

### API 에러 처리
- [ ] catch에서 `message.error()`를 직접 호출하지 않는다
- [ ] 성공 시만 `message.success()`를 호출한다

→ 상세: [API-사용법.md](./API-사용법.md)

### Atelier 스타일
- [ ] **Props로만 스타일 변경**: Atelier 컴포넌트 스타일 오버라이드 시도하지 않는다
- [ ] **커스텀 순서 준수**: MCP로 props 검색 → div로 감싸서 해결 → 스펙아웃 요청
- [ ] **Atelier 컴포넌트 우선**: `div` 대신 `Flex`, `span/p` 대신 `Typography` 사용

→ 상세: [Atelier-사용법.md](./Atelier-사용법.md)

### 스타일링
- [ ] **Atelier 우선**: Atelier props로 해결 가능한데 직접 구현하지 않는다
- [ ] **SCSS Module만 사용**: `.css` 파일을 직접 작성하지 않는다 (예외: `src/app/styles/` 전역 스타일)
- [ ] **인라인 스타일 최소화**: Atelier props → SCSS → 간단한 건 인라인 OK
- [ ] **SCSS 분리 기준**: 인라인 스타일이 (1) 속성 4개 이상이거나 (2) 파일 내 3군데 이상이면 SCSS로 분리했는가?
- [ ] **!important 금지**: `!important`를 사용하지 않는다
- [ ] **테마 색상 하드코딩 금지**: Primary/Brand 색상은 CSS 변수 사용 (일회성 레이아웃 값 `margin: 8px` 등은 허용)
- [ ] **조건부 클래스는 clsx 사용**: 삼항연산자나 템플릿 리터럴로 className 조합하지 않는다

→ 상세: [스타일링.md](./스타일링.md)

### 보안
- [ ] `dangerouslySetInnerHTML` 사용 시 `DOMPurify`를 적용한다
- [ ] 민감 데이터(JWT, Token, PII)를 localStorage에 저장하지 않는다

### 타입

**단일 소스 원칙 (타입을 정의하지 말고 추출하라)**
- [ ] API 요청/응답 타입을 직접 정의하지 않는다 (orval 생성 타입 사용)
- [ ] 프론트 전용 타입은 서버 타입에서 파생한다 (Pick, Omit, Partial 등)
- [ ] 특정 필드 타입이 필요하면 Lookup Type으로 추출한다 (`Dto['field']`)
- [ ] 라이브러리 래핑 시 `ComponentProps<typeof X>` 또는 라이브러리 export 타입을 사용한다
- [ ] 하드코딩된 유니온 대신 `as const` + `typeof`로 상수에서 타입을 파생한다

**타입 안전성**
- [ ] `any`, `as`, `!`를 사용하지 않는다 (Type Guard로 타입을 좁힌다)
- [ ] `||` 대신 `??` (nullish coalescing)를 사용한다
- [ ] `.filter()` 후 타입 유지가 필요하면 Type Predicate를 사용한다 (`isNotNull`)

→ 상세: [타입-전략.md](./타입-전략.md)

### API 호출
- [ ] `axiosInstance`를 직접 호출하지 않는다 (orval 생성 함수 사용)

### API 응답 타입
- [ ] 응답은 `{ data: T }` 형식이므로 `.data`로 접근한다 (`data?.data` 패턴)
- [ ] 타입 추출 시 `SomeControllerMethod200['data']` 형태로 사용한다

→ 상세: [API-사용법.md](./API-사용법.md)

### 상태 관리 도구 선택
- [ ] API 서버 데이터는 **React Query**를 사용한다
- [ ] 전역 클라이언트 상태는 **Zustand**를 사용한다 (정말 전역 필요한지 자문)
- [ ] 공유 가능해야 하는 상태(탭/필터/페이지네이션)는 **URL**에 저장한다
- [ ] 컴포넌트 로컬 상태는 **useState**를 사용한다
- [ ] **Context/Jotai 사용 금지** → Zustand 사용
- [ ] **Zustand selector 필수** - 전체 스토어 구독 (`const store = useStore()`) 금지

→ 상세: [상태관리.md](../design-review/상태관리.md)

### FSD 의존 방향
- [ ] **상위 → 하위만 import 가능** (역방향 금지): `app/` → `pages/` → `features/` → `shared/`
- [ ] `shared/`에서 `features/`를 import하지 않는다
- [ ] `features/A`에서 `features/B`를 직접 import하지 않는다

→ 상세: [FSD-폴더구조.md](../design-review/FSD-폴더구조.md)

### Import
- [ ] FSD 레이어별 alias 사용: `@app`, `@pages`, `@features`, `@shared`
- [ ] 상대 경로(`../../../`) 대신 alias를 사용한다

### 렌더링
- [ ] 숫자 조건부 렌더링에서 `count && <X/>` 대신 `count > 0 ? <X/> : null` 사용했는가?
- [ ] 배열 정렬 시 `toSorted()` 또는 `[...arr].sort()` 사용하여 원본 변경 방지했는가?

### Deprecated 패턴
- [ ] `defaultProps` 대신 ES6 파라미터 기본값 사용
- [ ] `propTypes` 대신 TypeScript 사용
- [ ] TanStack Query v5: 객체 형태(`{ queryKey, queryFn }`)만 사용, `onSuccess`/`onError` 콜백 미사용
- [ ] `cacheTime` 대신 `gcTime`, `isLoading` 대신 `isPending` 사용

→ 상세: [deprecated-패턴.md](./deprecated-패턴.md)

---

## ★★★ 발견 시 수정

### 기본
- [ ] 주석/커밋을 한국어로 작성한다
- [ ] barrel export (`index.ts`)를 작성한다

→ 상세: [FSD-폴더구조.md](../design-review/FSD-폴더구조.md)

### 커스텀 훅
- [ ] 커스텀 훅이 JSX를 반환하지 않는다 (Headless 원칙)
- [ ] 훅 반환값 3개 이상이면 객체로 반환한다
- [ ] **훅이 상태를 소유**하고, 컴포넌트는 UI만 담당한다 (단일 진실의 원천)
- [ ] 외부 prop은 트리거/힌트 역할만, 훅 내부 상태에 동기화한다
- [ ] `isOpen = open ?? internalOpen` 같은 외부/내부 상태 혼용을 피한다
- [ ] 외부 의존성(API 클라이언트, 스토리지 등)은 **훅 파라미터로 주입 가능**한가?

### 상태 관리
- [ ] 공유해야 하는 상태(탭/필터/페이지네이션)는 URL에 저장한다
- [ ] 패널/시트는 전용 훅을 사용한다

### WebSocket + React Query
- [ ] React Query 데이터를 useState로 복사하지 않는다
- [ ] WebSocket 이벤트 수신 시 `queryClient.setQueryData()`로 캐시 직접 업데이트한다
- [ ] 예외: 편집 중인 임시 데이터, UI 전용 상태는 로컬 상태 허용

→ 상세: [상태관리.md](../design-review/상태관리.md#실시간-데이터-websocket--react-query)

### 코드 품질 & 상수관리
- [ ] `import.meta.env` 사용 시 타입 정의 또는 undefined 체크를 한다
- [ ] 핵심 색상(Primary/Brand)은 하드코딩하지 않고 Token/상수를 사용한다
- [ ] 단순 UI 수치(px)는 리터럴 허용하되, 짝수 값을 권장한다

**상수 위치 구분:**
- [ ] 기획 값(최대 글자수, 재시도 횟수, 유효기간 등)은 shared/constants에 둔다
- [ ] 글로벌 영향 값(z-index, Timeout, 브레이크포인트)은 shared/constants에 둔다
- [ ] 구현 상세(애니메이션 duration, 디바운스 시간)는 해당 파일 상단에 둔다

→ 상세: [설계-철학.md](../design-review/설계-철학.md#상수-위치-결정)

### 주석
- [ ] **번역기 금지**: 코드를 읽으면 알 수 있는 내용을 주석으로 적지 않았는가?
- [ ] **이름이 먼저**: 주석을 달기 전에 변수/함수명을 더 명확하게 바꿀 수는 없는가?
- [ ] **최신화**: 코드를 수정하면서 관련된 주석도 함께 수정(또는 삭제)했는가?

**[SPEC] 태그 필요 여부 확인:**
- [ ] 뜬금없는 매직 넘버(숫자)나 예외 처리에 `[SPEC]` + 기획서 링크가 있는가?
- [ ] 직관과 반대되는 로직(기획 요구사항 때문에 억지로 구현)에 `[SPEC]` + 근거가 있는가?
- [ ] 백엔드 API 미지원/레거시 문제로 인한 우회 처리에 `[SPEC]` + 이유가 있는가?

**[CORE] 태그 필요 여부 확인:**
- [ ] 복잡하거나 일반적이지 않은 구현 방식에 `[CORE]` + 이유가 적혀있는가?

**[WARN] 태그 필요 여부 확인:**
- [ ] 수정 시 다른 기능에 Side Effect가 발생하는 코드에 `[WARN]` + 영향 범위가 적혀있는가?

→ 상세: [주석-가이드.md](../doc-cleanup/주석-가이드.md)

### 컴포넌트 분리
- [ ] **분리 조건 충족 확인**: 분리하려면 (1) 순수 재사용 (2) 공통 UI 라이브러리 중 하나에 해당해야 한다. 해당하지 않으면 한 파일에 유지한다.
- [ ] **복잡도 기반 분리 (Soft Limit 500줄)**: 단순히 길다고 분리하지 않는다. 500줄 초과 시 ① 상수/타입 추출 → ② Custom Hook 추출 → ③ 그래도 JSX가 길면 컴포넌트 분리 순서로 검토한다.
- [ ] **도메인 컴포넌트가 UI 컴포넌트를 조합**: `features/{domain}/components/`의 도메인 컴포넌트가 API 호출 + `shared/ui/`의 UI 컴포넌트 조합 역할을 하고 있는가?

→ 상세: [컴포넌트-설계.md](../design-review/컴포넌트-설계.md#컴포넌트-분리-전략)

### 성능 최적화
- [ ] 배열에서 반복 검색 시 `Set`/`Map`으로 O(1) 조회로 변환했는가?
- [ ] 배열 비교(정렬, deep equality) 전에 `length` 먼저 체크했는가?
- [ ] 동일 키로 여러 번 `.find()` 호출 시 `Map` 인덱스를 빌드했는가?
- [ ] 컴포넌트 내 RegExp를 모듈 스코프 또는 `useMemo`로 호이스팅했는가?
- [ ] 렌더링 중 동일 입력으로 반복 호출되는 함수를 캐싱했는가?
- [ ] 앱 전역 초기화를 모듈 레벨 guard로 보호했는가?
- [ ] 긴 리스트에 가상화를 적용했는가? (SelectWithSearch, Table 등 Atelier 컴포넌트도 지원)
- [ ] 가상화가 어려운 경우 `content-visibility: auto` + `contain-intrinsic-size` 적용했는가?
