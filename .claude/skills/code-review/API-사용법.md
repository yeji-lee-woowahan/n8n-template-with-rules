# API 사용법

## 타입 사용 원칙

**목적:** 서버 명세 변경 시 프론트에서 타입 에러가 발생하도록 하여 동기화를 강제한다.

### 기본 규칙

1. **서버 타입만 사용** - API 요청/응답 타입은 orval 생성 타입만 사용
2. **파생만 허용** - 프론트 전용 타입이 필요하면 서버 타입에서 파생
3. **독립 정의 금지** - 서버 타입과 무관한 타입을 새로 정의하지 않음

### 올바른 예시

```typescript
import type { CharacterDto, CreateCharacterDto } from '@/shared/api/generated';

// 그대로 사용
type Character = CharacterDto;

// 일부 필드만 필요할 때
type CharacterSummary = Pick<CharacterDto, 'id' | 'name' | 'thumbnail'>;

// 특정 필드 제외
type CharacterWithoutId = Omit<CreateCharacterDto, 'id'>;

// 선택적 필드로 변환
type PartialCharacter = Partial<CharacterDto>;

// 조합
type CharacterFormData = Omit<CreateCharacterDto, 'authorId'> & {
  localImage?: File;
};
```

### 금지 예시

```typescript
// ❌ 서버 타입과 무관하게 독립 정의
interface Character {
  id: string;
  name: string;
}

// ❌ API 응답 타입 직접 정의
interface GetCharacterResponse {
  data: Character;
}
```

### 왜 이렇게 해야 하는가?

- 서버에서 `CharacterDto.name` → `CharacterDto.displayName`으로 변경 시
- 서버 타입에서 파생했다면 → **프론트 빌드 에러** (즉시 인지)
- 독립 정의했다면 → **런타임 버그** (나중에 발견)

---

## orval 함수만 사용

```bash
pnpm api:generate
```

```typescript
// Query
const { data } = useUsersControllerGetMe();

// Mutation (직접 호출)
await authControllerGoogleLogin({ idToken });
```

### 서버 수정이 필요한 경우

orval 생성 코드가 실제 서버 동작과 다르거나, 필요한 API가 없는 경우:

1. **작업 중단** - 직접 axios 호출로 우회하지 않음
2. **사용자에게 확인** - "서버 수정이 필요합니다. 진행할까요?"
3. **서버 수정 후** - orval 재생성 (`pnpm api:generate`)
4. **생성된 함수 사용** - 원칙대로 orval 함수 사용

**금지:** `axiosInstance.post('/api/...')` 직접 호출로 우회

---

## Query Key 규칙

Query Key는 반드시 Codegen이 생성한 `get...QueryKey()` 함수만 사용

```typescript
// 올바른 사용
import { getTagsControllerGetTagDetailQueryKey } from '@/shared/api/generated/태그/태그';

removeQueryKeys: [getTagsControllerGetTagDetailQueryKey(tagId)]
invalidateQueries({ queryKey: getTagsControllerGetTagDetailQueryKey(tagId) })

// 금지 (ESLint 에러)
removeQueryKeys: [['/api/tags', tagId]]  // 리터럴 배열
removeQueryKeys: [someVariable]          // 변수 참조
```

**이유:**
- 문자열 오타 시 조용히 실패 (버그)
- API 경로 변경 시 수동 동기화 필요
- Codegen 함수는 타입 안전 + 자동 동기화

**ESLint 자동 검사:** `pnpm lint`에서 위반 시 에러 발생

---

## 응답 형식

```typescript
{ data: T }                                              // 단일
{ data: T[], metadata: { total, limit, currentOffset } } // 목록
```

---

## 에러 처리

**원칙:** 인터셉터가 모든 API 에러를 자동으로 스낵바 표시 (서버 메시지 사용)

### 기본 패턴

```typescript
const { message } = App.useApp();

try {
  await apiCall();
  message.success('성공 메시지'); // 성공 시만 스낵바 표시
} catch {
  // 에러 스낵바는 인터셉터에서 자동 표시
}
```

### 커스텀 에러 처리 (특수한 경우만)

```typescript
try {
  await apiCall({
    // ... params
  }, {
    skipErrorSnackbar: true, // 자동 스낵바 끄기
  });
} catch (error) {
  if (error instanceof ApiError) {
    if (error.code === 'specific-error') {
      navigate('/somewhere');
    } else {
      message.error(error.message);
    }
  }
}
```

### 자동 처리되는 에러

| 에러 | 동작 |
|------|------|
| 401 인증 만료 | 자동 토큰 갱신 → 실패 시 로그인 페이지 리다이렉트 (스낵바 없음) |
| 422 유효성 검증 | 서버 메시지 스낵바 |
| 500 서버 에러 | "서버 오류가 발생했습니다" 스낵바 |
| 네트워크 에러 | "서버에 연결할 수 없습니다" 스낵바 |
