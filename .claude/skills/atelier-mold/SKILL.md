---
name: atelier-mold
description: [몰드]어드민가이드 스킬. @atelier-mold/admin 기반 어드민 UI 개발 시 참조. 소개·개발 시작하기(의존성·설치·AtelierRoot)·Blue/Extension 컴포넌트·마이그레이션 가이드·연관 링크.
---

# [몰드] 어드민 가이드 스킬

이 스킬은 **몰드 어드민 가이드**(https://atelier-mold.betabaemin.in/) 내용을 요약합니다. `@atelier-mold/admin` 패키지를 사용해 어드민 화면을 개발할 때 컴포넌트·설치·사용법을 참고합니다.

## 사용 시점

- 어드민 화면을 `@atelier-mold/admin`으로 구현·리팩터할 때
- Blue(우아한공방 블루) re-export·Extension 컴포넌트 선택이 필요할 때
- 블루어드민(`@atelier/blue-admin`)에서 몰드어드민으로 마이그레이션할 때

---

## 1. 몰드 어드민 가이드란

- **목적**: 어드민 제작 시 기획/디자인/개발 비용을 줄이기 위한 **재사용 패턴·통일된 사용성** 제공.
- **활용**: 기획 시 예시 화면(캡처)·피그마·와이어프레임으로 요구사항 전달. 개발 시 가이드 컴포넌트로 구현.
- **문의**: Slack `#support-몰드-어드민가이드`  
- **온보딩**: Wiki [몰드]어드민가이드 사용 온보딩 참고.

---

## 2. 개발 시작하기

### 사전 준비

- **Peer dependency**: `react@18`, `react-dom@18`
- **FormCoat·Form presets 사용 시**: `react-hook-form@^7.46.2` 추가
- **포함 의존성**: `@atelier/blue@^1.37.0`, `@vanilla-extract/dynamic@2.0.3`, `react-vtree@3.0.0-beta.3` 등 (패키지에 포함됨)

### .npmrc (사내 레지스트리)

프로젝트 루트 `.npmrc`에 다음이 있어야 합니다.

```
registry=https://nexus.baemin.in/repository/npm/
```

### 설치

```bash
pnpm add @atelier-mold/admin
```

### 사용하기

- **AtelierRoot**: 모든 몰드어드민 컴포넌트를 쓰는 앱 상위에 `AtelierRoot` Provider 적용.
- **스타일**: `@atelier-mold/admin/style.css` import.

```tsx
import { AtelierRoot } from '@atelier-mold/admin'
import '@atelier-mold/admin/style.css'

export function App({ children }) {
  return (
    <AtelierRoot>
      {children}
    </AtelierRoot>
  )
}
```

### 가이드 읽기 전 참고

- **Blue**: 우아한공방 블루 컴포넌트를 re-export. 문서에서 re-export 목록 확인.
- **Blue Customs**: 일부 블루 컴포넌트를 몰드에서 재정의. Card, Header(PageHeader, ServiceHeader), Select, TextArea, TextInput, Uploader 등.
- **Extension**: 블루 기반 확장 컴포넌트. AddressSearch, BottomActionBar, CategoryPicker, CategoryTree, Dashboard, DataView, FormCoat, GNB, Layout, MultiPicker, RequiredMark, SearchFilter, SelectWithSearch, Header 계열 등.
- **마이그레이션**: `@atelier/blue-admin` → `@atelier-mold/admin` 전환 시 마이그레이션 가이드 참고.

---

## 3. 컴포넌트·유틸 구조 (문서 기준)

| 구분 | 설명 | references 수 | 예시 |
|------|------|-------------|------|
| Blue (re-export) | 우아한공방 블루 컴포넌트 re-export. **전체 56개 상세 문서 보유** | 56개 | Accordion, Alert, Badge, Button, Checkbox, Dialog, Flex, Form, Pagination, Tab, Table, Typography 등 |
| Blue Customs | 블루를 몰드에서 재정의 | 7개 | Card, PageHeader, ServiceHeader, Select, TextArea, TextInput, Uploader |
| Extension | 블루 기반 확장 컴포넌트 | 18개 | GNB, Layout, FormCoat, BottomActionBar, SelectWithSearch, DataView, Dashboard, Header 계열 등 |
| Hooks | 유틸리티 훅 | 5개 | toFormNumber, toFormString, toFormArrayNumber, toFormArrayString, useSimpleAlert |
| 마이그레이션 가이드 | v1→v2, Layout/GNB/FormCoat 등 변경사항 | 5개 | V2Guide, LayoutGuide, GnbGuide, FormCoatGuide, BottomActionBarGuide |

---

## 4. 연관 링크

- **Web**: [몰드]어드민가이드 — https://atelier-mold.betabaemin.in/admin/docs
- **Figma**: [몰드]어드민가이드 (디자인·예시)
- **Storybook**: https://atelier-mold.betabaemin.in/admin/storybooks/ (컴포넌트 체험)
- **소스**: mold-admin 패키지 (GitLab)
- **체험**: 우아한플레이그라운드 https://playground.betawoowa.in
- **서포트**: Slack `#support-몰드-어드민가이드`

상세 컴포넌트 API·예제는 **skills-hub MCP** (`skills_search_component({name: "컴포넌트명", skill: "atelier-mold"})`)로 조회하거나, **웹 가이드**와 **Storybook**에서 확인한다.  
MCP가 있으면 `references/` 파일을 직접 읽을 필요 없이 **온디맨드 조회**가 가능하다. MCP 없을 때는 `references/links.md`에서 전체 목록을 확인한다.

### Blue re-export 컴포넌트 (56개 상세 문서)

몰드어드민에서 `@atelier-mold/admin`으로 re-export되는 클레이블루 컴포넌트의 전체 Props·서브컴포넌트·사용법 문서:

**액션**: Button, IconButton, TextButton, Link  
**폼**: Checkbox, DatePicker, Form, Radio, RadioButtonGroup, Select(Custom), Stepper, Switch, TextArea(Custom), TextInput(Custom), TimePicker, TimeRangePicker  
**오버레이**: ActionSheet, Alert, BottomSheet, Dialog, Dropdown, ImageViewer, OverlayFooter, OverlayHeader, PageSheet  
**레이아웃**: Accordion, Container, Divider, Flex, Spacer  
**네비게이션**: BottomBar, Breadcrumb, PageIndicator, Pagination, Tab, Topbar  
**표시**: AssistiveText, Badge, Banner, Chip, HintTooltip, MessageBox, NotificationBadge, Snackbar, Tag, Thumbnail, Tooltip  
**헤더**: CardHeader, ListHeader, SectionHeader  
**리스트**: ListItem, TextListItem  
**로딩**: CircleLoading, SkeletonLoading  
**텍스트**: Highlight, Typography  
**데이터**: Table
