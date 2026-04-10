# Atelier 사용법

> 우아한형제들 디자인 시스템. 몰드어드민은 `@atelier/blue` 기반.

## ⚠️ 핵심: @atelier-mold/admin에서 import

**`@atelier/blue` 직접 사용 금지!** 몰드어드민이 블루를 re-export하므로 모든 컴포넌트는 `@atelier-mold/admin`에서 import합니다.

```tsx
// ❌ Bad - @atelier/blue 직접 import
import { Flex, Typography, Button } from '@atelier/blue'

// ✅ Good - @atelier-mold/admin에서 import
import { Flex, Typography, Button } from '@atelier-mold/admin'
```

**이유:**
- 몰드어드민의 `AtelierRoot`가 필요한 Provider를 포함
- 혼용 시 Provider 불일치 에러 발생

## 기본 설정

```tsx
// AtelierProvider.tsx
import { AtelierRoot } from '@atelier-mold/admin'
import '@atelier-mold/admin/style.css'

<AtelierRoot>
  <App />
</AtelierRoot>
```

---

## 핵심 규칙

### 1. HTML 대신 Atelier 컴포넌트 사용

| HTML | Atelier |
|------|---------|
| `<div style="display:flex">` | `<Flex>` |
| `<span>`, `<p>`, `<strong>` | `<Typography>` |
| `<button>` | `<Button>` |
| `<input type="text">` | `<TextInput>` / `<SelectWithSearch>` |

### 2. inline style 금지

```tsx
// ❌ Bad
<div style={{ display: 'flex', alignItems: 'center' }}>

// ✅ Good
<Flex alignItems="center">
```

### 3. Flex 컴포넌트 props 활용

```tsx
// ❌ Bad - CSS style에 의존
<Flex className={styles.container}>  // style에 flex 속성 정의

// ✅ Good - props 사용
<Flex alignItems="center" justifyContent="space-between" gap="100">
```

### 4. Typography 적극 사용

```tsx
// ❌ Bad
<span>텍스트</span>
<p>내용</p>

// ✅ Good
<Typography as="span" variant="body1">텍스트</Typography>
<Typography as="p" variant="body2">내용</Typography>
```

---

## 주요 컴포넌트

### Button

```tsx
import { Button } from '@atelier-mold/admin'

<Button variant="fill" color="primary" size="medium">
  확인
</Button>

// 아이콘 포함
<Button>
  <Button.Left><CheckIcon /></Button.Left>
  확인
</Button>
```

| prop | 값 |
|------|-----|
| variant | `fill`, `outline` |
| color | `primary`, `primaryDanger`, `secondary`, `white` |
| size | `small`, `medium`, `large`, `xlarge` |
| width | `string \| number` (style로 넣지 말 것) |
| loading | `boolean` |
| disabled | `boolean` |

### Typography

```tsx
import { Typography } from '@atelier-mold/admin'

<Typography as="h1" variant="title1" weight="bold" color="fg_primary">
  제목
</Typography>
```

| prop | 값 |
|------|-----|
| as | `span`, `p`, `h1`~`h6`, `strong` 등 |
| variant | `caption`, `body3`, `body2`, `body1`, `title4`, `title3`, `title2`, `title1` |
| weight | `regular`, `medium`, `bold` |
| color | `fg_primary`, `fg_secondary`, `fg_accent`, `fg_danger` 등 |
| maxLines | `number` (말줄임) |

### Flex

```tsx
import { Flex } from '@atelier-mold/admin'

<Flex flexDirection="column" alignItems="center" gap="100">
  <div>Item 1</div>
  <div>Item 2</div>
</Flex>
```

| prop | 값 |
|------|-----|
| flexDirection | `row`, `column` |
| alignItems | `center`, `flex-start`, `flex-end`, `stretch` |
| justifyContent | `center`, `space-between`, `flex-start`, `flex-end` |
| gap | `100`, `200`, `300`, `400`, `500` ... (Spacing 토큰) |
| flexWrap | `wrap`, `nowrap` |

#### ⚠️ flexGrow, flexShrink는 deprecated

`flexGrow`, `flexShrink` props는 deprecated되었습니다. SCSS에서 처리하세요.

```tsx
// ❌ Bad - deprecated props
<Flex flexGrow={1}>

// ✅ Good - SCSS 클래스 사용
<Flex className={styles.grow}>
```

```scss
// ComponentName.module.scss
.grow {
  flex-grow: 1;
}
```

### Card

```tsx
import { Card } from '@atelier-mold/admin'

<Card variant="outline" radius="large" padding="medium">
  콘텐츠
</Card>
```

| prop | 값 |
|------|-----|
| variant | `basic`, `outline`, `shadow`, `fill` |
| radius | `none`, `large` |
| padding | `none`, `small`, `medium`, `large` |

---

## 몰드어드민 전용 컴포넌트

- **GNB** - 좌측 사이드바
- **Layout** - 페이지 레이아웃
- **PageHeader** - 페이지 헤더
- **DataView** - 데이터 테이블
- **SearchFilter** - 검색 필터
- **SelectWithSearch** - 검색 가능한 셀렉트
- **FormCoat** - 폼 래퍼
- **Card** / **SimpleCardHeader** / **EditableCardHeader** - 카드 컴포넌트
- **Uploader** - 파일 업로드

---

## 주의사항

1. **Props 타입 확인** - 존재하는 props만 사용
2. **width는 props로** - Button 등 width props 있는 컴포넌트는 style 대신 props 사용
3. **커스텀 스타일 최소화** - 기본 스타일 우선, className으로 최소한만 커스텀
4. **접근성 내장** - 추가 접근성 속성은 필요할 때만

---

## Spacing 토큰 참고

| 토큰 | 값 |
|------|-----|
| 100 | 4px |
| 200 | 8px |
| 300 | 12px |
| 400 | 16px |
| 500 | 20px |
| 600 | 24px |
| 700 | 28px |
| 800 | 32px |

---

## CSS 변수 (Design Tokens)

Atelier는 CSS 변수로 디자인 토큰을 제공합니다. SCSS에서 색상을 사용할 때 하드코딩 대신 이 변수를 사용하세요.

### 사용법

```scss
// ❌ Bad - 하드코딩
.content {
  background-color: #f9f9f9;
}

// ✅ Good - Atelier CSS 변수
.content {
  background-color: var(--blue-color-fill-primary);
}
```

### 주요 색상 토큰

#### Semantic 토큰 (용도별)

| 용도 | CSS 변수 | 설명 |
|------|----------|------|
| 배경 (Primary) | `--blue-color-bg-primary` | 기본 배경색 |
| 배경 (Secondary) | `--blue-color-bg-secondary` | 보조 배경색 |
| Fill (Primary) | `--blue-color-fill-primary` | 기본 채움색 |
| Fill (Secondary) | `--blue-color-fill-secondary` | 보조 채움색 |
| Fill (Tertiary) | `--blue-color-fill-tertiary` | 3차 채움색 |
| 테두리 (Primary) | `--blue-color-line-primary` | 기본 테두리 |
| 테두리 (Secondary) | `--blue-color-line-secondary` | 보조 테두리 |
| 전경 (Primary) | `--blue-color-fg-primary` | 기본 텍스트 |
| 전경 (Secondary) | `--blue-color-fg-secondary` | 보조 텍스트 |
| 전경 (Tertiary) | `--blue-color-fg-tertiary` | 3차 텍스트 |

#### 상태 색상

| 상태 | Fill | Foreground |
|------|------|------------|
| 성공 (Success) | `--blue-color-fill-success-primary` | `--blue-color-fg-success` |
| 위험 (Danger) | `--blue-color-fill-danger-primary` | `--blue-color-fg-danger` |
| 경고 (Warning) | `--blue-color-fill-warning-primary` | `--blue-color-fg-warning` |
| 강조 (Accent) | `--blue-color-fill-accent-primary` | `--blue-color-fg-accent` |

#### Reference 토큰 (색상 팔레트)

```scss
// Gray 스케일 (gray1 ~ gray12)
var(--ref-blue-color-gray1)   // #f3f5f7 (밝음)
var(--ref-blue-color-gray12)  // #181a1c (어두움)

// 컬러 팔레트 (1=밝음 ~ 8=어두움)
var(--ref-blue-color-blue5)   // #1a7cff
var(--ref-blue-color-red5)    // #ff403e
var(--ref-blue-color-green5)  // #00b96b
```

### 색상 선택 가이드

1. **Semantic 토큰 우선** - 용도에 맞는 semantic 토큰이 있으면 사용
2. **Reference 토큰** - semantic에 없으면 reference 팔레트 사용
3. **하드코딩 금지** - 임의 색상값 직접 입력 금지
