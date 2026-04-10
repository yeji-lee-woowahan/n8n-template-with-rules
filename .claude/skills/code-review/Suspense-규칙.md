# Suspense 쿼리 사용 규칙

## Suspense 허용

1. 코드 스플리팅 (`React.lazy`)
2. 여러 데이터를 복합으로 보여주는 경우 → 부모 컴포넌트에 Suspense 래핑

## Suspense 금지

- 단일 데이터 패칭 → 일반 쿼리 사용 (`useXxx`)

---

## 이유

| 쿼리 타입 | 에러 처리 | 결과 |
|-----------|-----------|------|
| Suspense 쿼리 | 에러 시 throw | ErrorBoundary 필요, 없으면 앱 크래시 |
| 일반 쿼리 | `isLoading`, `isError` 반환 | 직접 처리 가능, 앱 안정성 보장 |

---

## 예시

```typescript
// ❌ 단일 데이터에 Suspense 쿼리 사용
const { data } = useSuspenseQuery(...);

// ✅ 일반 쿼리 사용
const { data, isLoading, isError } = useQuery(...);
if (isLoading) return <Skeleton />;
if (isError) return <ErrorMessage />;
```
