# [몰드] 어드민 가이드 연관 링크 및 로컬 문서

## 웹·외부 링크

- **웹 가이드 (메인)**: https://atelier-mold.betabaemin.in/admin/docs
- **개발 시작하기**: https://atelier-mold.betabaemin.in/admin/docs/getting-started
- **Blue (re-export 목록)**: https://atelier-mold.betabaemin.in/admin/docs/reexported-blue
- **클레이블루 공식 문서**: https://atelier.baemin.com/docs/blue/
- **Storybook**: https://atelier-mold.betabaemin.in/admin/storybooks/?path=/docs/intro-시작하기--docs
- **Figma**: [몰드]어드민가이드 (어드민 제작 가이드)
- **소스 (mold-admin)**: https://git.baemin.in/common-fe/platform/system/woowahan-atelier/molds/mold/-/tree/main/packages/mold-admin
- **서포트**: Slack #support-몰드-어드민가이드
- **온보딩**: Wiki [몰드]어드민가이드 사용 온보딩
- **우아한플레이그라운드**: https://playground.betawoowa.in

## 로컬 references (웹 가이드 본문 요약)

아래 파일들은 웹 가이드 문서 페이지 내용을 가져와 둔 것입니다. 상세·최신 내용은 위 웹 가이드에서 확인하세요.

### 소개·시작·re-export

| 구분 | 파일명 | 대응 웹 경로 |
|------|--------|--------------|
| 소개 | intro.md | /admin/docs |
| 개발 시작 | getting-started.md | /admin/docs/getting-started |
| Blue re-export 목록 | reexported-blue.md | /admin/docs/reexported-blue |

### Blue Customs (몰드가 재정의한 블루 컴포넌트, 7개)

| 파일명 | 컴포넌트 | 설명 |
|--------|----------|------|
| blue-card.md | Card | 블루 Card 확장. variant='outline', radius='large' 고정 |
| blue-header-pageheader.md | PageHeader | 몰드 전용 페이지 헤더 |
| blue-header-serviceheader.md | ServiceHeader | 몰드 전용 서비스 헤더 |
| blue-select.md | Select | 블루 Select 재정의 |
| blue-textarea.md | TextArea | 블루 TextArea 재정의 |
| blue-textinput.md | TextInput | 블루 TextInput 재정의 |
| blue-uploader.md | Uploader | 블루 Uploader 재정의 |

### Blue Re-exported 컴포넌트 (순수 블루 re-export, 56개)

몰드어드민에서 `@atelier-mold/admin`으로 re-export되는 클레이블루 원본 컴포넌트입니다.

| 파일명 | 컴포넌트 | 카테고리 |
|--------|----------|----------|
| blue-accordion.md | Accordion | 레이아웃 |
| blue-actionsheet.md | ActionSheet | 오버레이 |
| blue-alert.md | Alert | 오버레이 |
| blue-assistivetext.md | AssistiveText | 텍스트 |
| blue-badge.md | Badge | 표시 |
| blue-banner.md | Banner | 표시 |
| blue-bottombar.md | BottomBar | 네비게이션 |
| blue-bottomsheet.md | BottomSheet | 오버레이 |
| blue-breadcrumb.md | Breadcrumb | 네비게이션 |
| blue-button.md | Button | 액션 |
| blue-cardheader.md | CardHeader | 헤더 |
| blue-checkbox.md | Checkbox | 폼 |
| blue-chip.md | Chip | 선택 |
| blue-circleloading.md | CircleLoading | 로딩 |
| blue-container.md | Container | 레이아웃 |
| blue-datepicker.md | DatePicker | 폼 |
| blue-dialog.md | Dialog | 오버레이 |
| blue-divider.md | Divider | 레이아웃 |
| blue-dropdown.md | Dropdown | 오버레이 |
| blue-flex.md | Flex | 레이아웃 |
| blue-form.md | Form | 폼 |
| blue-highlight.md | Highlight | 텍스트 |
| blue-hinttooltip.md | HintTooltip | 표시 |
| blue-iconbutton.md | IconButton | 액션 |
| blue-imageviewer.md | ImageViewer | 오버레이 |
| blue-link.md | Link | 액션 |
| blue-listheader.md | ListHeader | 헤더 |
| blue-listitem.md | ListItem | 리스트 |
| blue-messagebox.md | MessageBox | 표시 |
| blue-notificationbadge.md | NotificationBadge | 표시 |
| blue-overlayfooter.md | OverlayFooter | 오버레이 |
| blue-overlayheader.md | OverlayHeader | 오버레이 |
| blue-pageindicator.md | PageIndicator | 네비게이션 |
| blue-pagesheet.md | PageSheet | 오버레이 |
| blue-pagination.md | Pagination | 네비게이션 |
| blue-radio.md | Radio | 폼 |
| blue-radiobuttongroup.md | RadioButtonGroup | 폼 |
| blue-searchbar.md | SearchBar | 검색 |
| blue-searchinput.md | SearchInput | 검색 |
| blue-sectionheader.md | SectionHeader | 헤더 |
| blue-skeletonloading.md | SkeletonLoading | 로딩 |
| blue-snackbar.md | Snackbar | 표시 |
| blue-spacer.md | Spacer | 레이아웃 |
| blue-stepper.md | Stepper | 폼 |
| blue-switch.md | Switch | 폼 |
| blue-tab.md | Tab | 네비게이션 |
| blue-table.md | Table | 데이터 |
| blue-tag.md | Tag | 표시 |
| blue-textbutton.md | TextButton | 액션 |
| blue-textlistitem.md | TextListItem | 리스트 |
| blue-thumbnail.md | Thumbnail | 표시 |
| blue-timepicker.md | TimePicker | 폼 |
| blue-timerangepicker.md | TimeRangePicker | 폼 |
| blue-tooltip.md | Tooltip | 표시 |
| blue-topbar.md | Topbar | 네비게이션 |
| blue-typography.md | Typography | 텍스트 |

### Extension (몰드 확장 컴포넌트, 14개)

| 파일명 | 컴포넌트 |
|--------|----------|
| extension-addresssearch.md | AddressSearch |
| extension-bottomactionbar.md | BottomActionBar |
| extension-categorypicker.md | CategoryPicker |
| extension-categorytree.md | CategoryTree |
| extension-dashboard.md | Dashboard |
| extension-dataview.md | DataView |
| extension-formcoat.md | FormCoat |
| extension-gnb.md | GNB |
| extension-header-accordioncardheader.md | AccordionCardHeader |
| extension-header-editableeditcardheader.md | EditableEditCardHeader |
| extension-header-editableviewcardheader.md | EditableViewCardHeader |
| extension-header-simplecardheader.md | SimpleCardHeader |
| extension-header-tableheader.md | TableHeader |
| extension-layout.md | Layout |
| extension-multipicker.md | MultiPicker |
| extension-requiredmark.md | RequiredMark |
| extension-searchfilter.md | SearchFilter |
| extension-selectwithsearch.md | SelectWithSearch |

### Hooks (5개)

| 파일명 | Hook |
|--------|------|
| hooks-toformarraynumber.md | toFormArrayNumber |
| hooks-toformarraystring.md | toFormArrayString |
| hooks-toformnumber.md | toFormNumber |
| hooks-toformstring.md | toFormString |
| hooks-usealert.md | useSimpleAlert |

### 마이그레이션 가이드 (5개)

| 파일명 | 가이드 |
|--------|--------|
| migration-guides-v2guide.md | V2 마이그레이션 |
| migration-guides-layoutguide.md | Layout 마이그레이션 |
| migration-guides-gnbguide.md | GNB 마이그레이션 |
| migration-guides-formcoatguide.md | FormCoat 마이그레이션 |
| migration-guides-bottomactionbarguide.md | BottomActionBar 마이그레이션 |

재수집: 프로젝트 루트에서 `node scripts/fetch-atelier-mold-docs.js` 실행.
