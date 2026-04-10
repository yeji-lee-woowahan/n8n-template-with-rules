# Deprecated 패턴 (AI 습관 교정)

> AI가 자주 생성하는 구버전 패턴. 발견 시 즉시 수정.

---

## React & Router

| ❌ Deprecated / Legacy | ✅ Modern Way | 비고 |
|------------------------|---------------|------|
| `import React` | 삭제 | React 17+ JSX Transform으로 불필요 |
| `ReactDOM.render` | `createRoot` | React 18+ 진입점 표준 |
| `defaultProps` | `{ prop = 'val' }` | ES6 파라미터 기본값 |
| `propTypes` | TypeScript | TS 프로젝트에서 불필요 |
| `e.persist()` | 삭제 | React 17+ 이벤트 풀링 제거 |
| `component` prop | `element` prop | React Router v6+ |
| `useHistory` | `useNavigate` | React Router v6+ |
| `<Redirect>` | `<Navigate>` | React Router v6+ |

---

## TanStack Query v5

AI는 습관적으로 `useQuery(key, fn)` 형태나 `onSuccess` 콜백을 사용하려 합니다. v5에서는 에러가 나거나 권장되지 않는 패턴입니다.

| ❌ Legacy (AI가 자주 틀림) | ✅ Modern (v5) | 비고 |
|---------------------------|----------------|------|
| `useQuery(key, fn, opt)` | `useQuery({ queryKey, queryFn })` | 인자 3개 방식 삭제됨. 객체 형태만 허용 |
| `onSuccess`, `onError` | `useEffect` 또는 mutate 콜백 | useQuery 옵션에서 콜백 삭제됨 |
| `keepPreviousData: true` | `placeholderData: keepPreviousData` | 옵션명 및 방식 변경 |
| `cacheTime` | `gcTime` | Garbage Collection Time으로 명칭 변경 |
| `isLoading` | `isPending` | 초기 로딩 상태는 isPending이 더 정확 |
| `remove()` | `gcTime: 0` | 쿼리 제거 메서드 대신 GC 시간 조절 |
