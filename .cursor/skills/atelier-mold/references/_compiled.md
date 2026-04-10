# atelier-mold — Compiled References
<!-- 자동 생성 파일. 수정하지 마세요. scripts/compile-skill-references.js -->
<!-- 원본: references/*.md (94개) → 94개 항목 압축 -->
### Accordion | `import { Accordion } from '@atelier/blue' | 몰드: import { Accordion } from '@atelier-mold/admin'`
접고 펼칠 수 있는 타이틀의 리스트 컴포넌트입니다.
**props**: expandedIdList: string[] = - — 펼쳐진 Accordion.Item의 id 리스트 (제어) · onExpandedChange: (expandedIdList: string[]) => void = - — 펼쳐진 id 리스트 콜백 · defaultExpandedIdList: string[] = - — 초기에 펼쳐진 id 리스트 (비제어) · multipleExpanded: boolean = false — 복수 펼침 여부 · size: 'large' \ = 'small' — 'large' · children: React.ReactNode = (필수) — Accordion.Item으로 구성
**subs**: Accordion.Item(Accordion을 구성하는 각각의 아이템. id: string prop 필수) · Accordion.Trigger(Accordion.Item의 접고/펼쳐짐을 전환하는 트리거 영역. spacing, onClick prop 지원) · Accordion.TriggerCaption(Accordion.Trigger의 캡션 영역) · Accordion.TriggerDescription(Accordion.Trigger의 디스크립션 영역) · Accordion.TriggerLeft(Accordion.Trigger의 왼쪽 영역. 뱃지, 아이콘 배치 가능) · Accordion.Content(Accordion.Trigger 클릭시 펼쳐지는 컨텐츠 영역. spacing, backgroundColor prop 지원) · prop(설명) · spacing(내부 패딩) · children(타이틀 및 서브컴포넌트) · onClick(클릭 이벤트 핸들러) · prop(설명) · spacing(내부 패딩) · backgroundColor(배경색) · children(컨텐츠)
**note**: 접고 펼칠 수 있는 타이틀의 리스트예요.. `Accordion`은 복수의 `Accordion.Item`으로 구성해요.
**ex**: `const [list, setList] = useState(['1']) <Accordion onExpandedChange={(next) => setList(next)} expandedIdList={list}> <Accordion.Item id='1'> <Accordion.Trigger> <Accordion.TriggerCaption>캡션</Accordion.TriggerCaption> <Accordion.TriggerLeft> <Badge>Badge</Badge> <CheckIcon /> </Accordion.TriggerLeft> 타이틀을 클릭하면 펼쳐져요. <Accordion.TriggerDescription>디스크립션</Accordion.TriggerDescription> </Accordion.Trigger> <Accordion.Content> 펼쳐지면 보이는 내용이에요. </Accordion.Content> </Accordion.Item> <Accordion.Item id='2'> <Accordion.Trigger> <Accordion.TriggerCaption>캡션</Accordion.TriggerCaption> 타이틀을 클릭하면 펼쳐져요.2 <Accordion.TriggerDescription>디스크립션</Accordion.TriggerDescription> </Accordion.Trigger> <Accordion.Content> 펼쳐지면 보이는 내용이에요. </Accordion.Content> </Accordion.Item> </Accordion>`

---

### ActionSheet | `import { ActionSheet } from '@atelier/blue' | 몰드: import { ActionSheet } from '@atelier-mold/admin'`
모바일 뷰포트에서 선택지를 제공할 때 사용하는 시트 컴포넌트입니다.
**props**: open: boolean = - — 열림 여부 (제어) · defaultOpen: boolean = - — 열림 여부 (비제어) · onClose: () => void = - — 닫힘 콜백 · value: string = - — 선택된 옵션 값 (제어) · defaultValue: string = - — 기본 옵션 값 (비제어) · onChange: ChangeEventHandler<HTMLSelectElement> = - — 옵션 변경 콜백 · title: string = - — 시트 상단 제목 (aria-label과 택1) · aria-label: string = - — 접근성 레이블 (title과 택1) · children: React.ReactNode = (필수) — 옵션 목록
**subs**: ActionSheet.Trigger(비제어 방식에서 시트를 열 때 사용. Popup.Trigger 기반) · ActionSheet.Option(시트 내 선택 가능한 옵션. value, color, disabled prop 지원) · ActionSheet.OptionLeft(옵션 왼쪽 영역) · ActionSheet.OptionRight(옵션 오른쪽 영역) · prop(설명) · value(옵션 값) · color(위험 색상) · disabled(비활성화 여부) · children(옵션 내용)
**note**: 모바일 뷰포트에서 선택지를 제공할 때 사용해요.. 제어, 비제어 방식을 지원해요.. 하단의 '취소' 버튼 또는 바깥 영역을 누르면 시트가 닫혀요.. `title`이 불필요한 경우 접근성 지원을 위해 `aria-label` prop을 전달해주세요.
**ex**: `const [open, setOpen] = useState(false) const [option, setOption] = useState('') <> <Button onClick={() => setOpen(true)}>옵션 선택</Button> <ActionSheet title='옵션 목록' open={open} onClose={() => setOpen(false)} value={option} onChange={(e) => setOption(e.target.value)} > <ActionSheet.Option value='option1'>옵션 1</ActionSheet.Option> <ActionSheet.Option value='option2'>옵션 2</ActionSheet.Option> <ActionSheet.Option value='option3' disabled>옵션 3 (비활성화)</ActionSheet.Option> </ActionSheet> </>`

---

### Alert | `import { Alert } from '@atelier/blue' | 몰드: import { Alert } from '@atelier-mold/admin'`
사용자의 행동을 막으면서 메세지를 전달할 때 사용하는 다이얼로그 컴포넌트입니다.
**props**: open: boolean = - — 열림 여부 (제어) · onClose: () => void = - — 닫힘 콜백 · children: React.ReactNode = (필수) — Alert 내부 콘텐츠
**subs**: Alert.Title(Alert의 타이틀 영역) · Alert.Description(Alert의 본문 영역) · Alert.Footer(Alert의 푸터 영역 (OverlayFooter 기반)) · Alert.Trigger(Trigger로 감싸진 요소를 클릭하면 Alert이 열림 (비제어 방식)) · Alert.Close(Close로 감싸진 요소를 클릭하면 Alert이 닫힘)
**note**: 사용자의 행동을 막으면서 메세지를 전달할 때 사용해요.. 바깥 영역(Backdrop)을 클릭해도 `Alert`은 닫히지 않아요.. 추가적인 기능, 컴포넌트를 담아야 한다면 `Dialog`를 사용해요.
**ex**: `const [open, setOpen] = useState(false) <> <Button onClick={() => setOpen(true)}>Alert 열기</Button> <Alert open={open} onClose={() => setOpen(false)}> <Alert.Title>타이틀</Alert.Title> <Alert.Description>본문은 마침표를 넣어 문장을 마무리해요.</Alert.Description> <Alert.Footer> <Alert.Close> <Button>확인</Button> </Alert.Close> </Alert.Footer> </Alert> </>`

---

### AssistiveText | `import { AssistiveText } from '@atelier/blue' | 몰드: import { AssistiveText } from '@atelier-mold/admin'`
추가 세부 정보를 노출해 내용을 인지할 수 있도록 돕는 역할을 하는 컴포넌트입니다.
**props**: variant: 'default' \ = 'invalid' \ — 'valid' · children: React.ReactNode = (필수) — 표시할 텍스트
**note**: 추가 세부 정보를 노출해 내용을 인지할 수 있도록 돕는 역할을 해요.. `Form`과 조합할 땐 `Form.Message`를 사용해주세요.
**ex**: `<AssistiveText variant='invalid'> 텍스트를 입력해주세요. </AssistiveText>`

---

### Badge | `import { Badge } from '@atelier/blue' | 몰드: import { Badge } from '@atelier-mold/admin'`
상태와 부가적인 정보를 나타낼 때 사용하는 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — Badge에 삽입될 텍스트 · variant: BadgeVariant = 'neutral' — Badge 색상 · size: 'small' \ = 'medium' — 'small' · round: boolean = false — 모서리 둥글게 여부 · ellipsis: boolean = true — 말줄임 여부
**subs**: Badge.Left(Badge 텍스트 왼쪽에 배치. 아이콘을 자식으로 가져야 함) · Badge.Right(Badge 텍스트 오른쪽에 배치. 말줄임되지 않고 마지막에 표시될 텍스트. 🚨 텍스트의 공백이 유지되지 않음)
**note**: 상태와 부가적인 정보를 나타낼 때 사용해요. 각 서비스의 기준에 따라 적절한 컬러의 뱃지를 사용해요.. 뱃지의 텍스트는 한 줄로 말줄임이 되어요.. 특정 텍스트를 말줄임 되게하지 않고 표시하고 싶으면 `Badge.Right`를 사용해주세요.. 뱃지의 텍스트는 공백이 유지돼요.
**ex**: `<Badge size='medium' ellipsis variant='lightBlue'> <Badge.Left> <NewIcon /> </Badge.Left> 배지 <Badge.Right>말줄임 안되는 텍스트</Badge.Right> </Badge>`

---

### Banner | `import { Banner } from '@atelier/blue' | 몰드: import { Banner } from '@atelier-mold/admin'`
프로모션 또는 중요한 안내사항 페이지로 연결되는 배너를 지속적으로 노출할 때 사용하는 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — Banner.ImageSlide 또는 Banner.TextSlide로 구성 · ratio: BannerRatio = (필수) — '2:1' \ · round: boolean = false — 모서리 둥글게 여부 · defaultIndex: number = 0 — 최초 슬라이드 index · title: string = (필수) — 접근성 지원 텍스트 · onIndexChange: (index: number) => void = - — index 변경 콜백 (임프레션 로그 등) · height: number = - — 고정 높이 (px). 지정 시 높이고정형
**subs**: Banner.ImageSlide(이미지만으로 구성하는 슬라이드. src, alt 필수) · Banner.TextSlide(텍스트와 이미지로 구성하는 슬라이드. src, color, backgroundColor 필수) · Banner.TextSlideTitle(텍스트 슬라이드의 title 영역) · Banner.TextSlideCaption(텍스트 슬라이드의 caption 영역. title 없이 단독 사용 불가) · prop(설명) · src(이미지 파일 경로) · alt(슬라이드 접근성 텍스트) · backgroundColor(배경 색상 (높이 고정형에서 사용)) · prop(설명) · src(이미지 파일 경로) · color(텍스트 색상) · backgroundColor(배경 색상) · alt(접근성 텍스트 (미지정 시 caption → title 순으로 읽음))
**note**: 프로모션 또는 중요한 안내사항 페이지로 연결되는 배너를 지속적으로 노출할 때 사용해요.. 사용자가 제스쳐를 하지 않아도 4초 후 다음 슬라이드로 넘어가요.. 슬라이드가 2개 이상일 때 인디케이터가 자동으로 표시돼요.. 마지막 슬라이드 다음에는 첫번째 슬라이드로 연결돼요.. 최대 10개의 슬라이드를 넣을 수 있어요.
**ex**: `const src = 'https://user-images.githubusercontent.com/60066472/184372060-fbf68515-956e-4410-af4b-ea58d23993fc.png' const alt = '배민상회 든든배송. 오늘 17시 이전 주문 시 내일 배송' <Banner ratio='2:1' title='메인 광고' round> <Banner.ImageSlide href='#1' src={src} alt={alt} /> <Banner.ImageSlide href='#2' src={src} alt={alt} /> </Banner>`

---

### BottomBar | `import { BottomBar } from '@atelier/blue' | 몰드: import { BottomBar } from '@atelier-mold/admin'`
모바일에서 주요 기능과 화면을 빠르게 탐색할 수 있는 하단 네비게이션 바 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — BottomBar.Item으로 구성 · position: 'static' \ = 'sticky' \ — 'fixed' · onChange: (value: string, event: MouseEvent) => void = (필수) — 변경 이벤트 · value: string = - — 현재 선택된 아이템의 value (제어) · defaultValue: string = - — 초기 선택된 아이템의 value (비제어)
**subs**: BottomBar.Item(BottomBar를 구성하는 아이템 요소) · prop(설명) · value(아이템별 고유한 value) · label(아이템 하단에 표시될 라벨) · highlight(아이템 강조 여부 (중앙 아이템에만 사용)) · children(아이콘 컴포넌트)
**note**: 모바일에서 주요 기능과 화면을 빠르게 탐색할 수 있어요.. 중앙에 위치한 버튼을 강조하려면 `BottomBar.Item`의 `highlight` prop을 사용해주세요.
**ex**: `const [value, setValue] = useState('home') <BottomBar value={value} onChange={(v, e) => setValue(v)}> <BottomBar.Item value="home" label="홈"> <HomeIcon /> </BottomBar.Item> <BottomBar.Item value="info" label="내정보"> <PersonSingleIcon /> </BottomBar.Item> </BottomBar>`

---

### BottomSheet | `import { BottomSheet } from '@atelier/blue' | 몰드: import { BottomSheet } from '@atelier-mold/admin'`
기존 페이지를 유지하며 추가적인 작업이 필요할 때 사용하는 시트 컴포넌트입니다.
**props**: open: boolean = - — 열림 여부 (제어) · onClose: () => void = - — 닫힘 콜백 · children: React.ReactNode = (필수) — 내부 콘텐츠 · mobileHeight: 'fill' \ = 'fit' \ — string · minHeight: string \ = number — '240px' · keepOldZIndex: boolean = false — (deprecated) 이전 z-index 값 사용 여부
**subs**: BottomSheet.Trigger(비제어 방식에서 시트를 여는 트리거. Popup.Trigger 기반) · BottomSheet.Close(감싸진 요소 클릭 시 시트 닫힘. Popup.Close 기반) · BottomSheet.Header(Header 영역 (OverlayHeader 기반)) · BottomSheet.HeaderLeft(Header 좌측 영역) · BottomSheet.HeaderRight(Header 우측 영역) · BottomSheet.HeaderTitle(Header 타이틀 영역) · BottomSheet.HeaderSubtitle(Header 서브타이틀 영역) · BottomSheet.Body(Body 영역. spacing prop 지원 (Container 기반)) · BottomSheet.Footer(Footer 영역 (버튼 정렬). OverlayFooter 기반)
**note**: 기존 페이지를 유지하며 추가적인 작업이 필요할 때 사용해요.. 제어, 비제어 방식을 모두 지원해요.
**ex**: `const [open, setOpen] = useState(false) <> <Button onClick={() => setOpen(true)}>바텀시트 열기</Button> <BottomSheet open={open} onClose={() => setOpen(false)}> <BottomSheet.Header> <BottomSheet.HeaderLeft> <IconButton size='large' label='닫기' shape='square' onClick={() => setOpen(false)}> <CloseIcon /> </IconButton> </BottomSheet.HeaderLeft> <BottomSheet.HeaderTitle>바텀시트 타이틀</BottomSheet.HeaderTitle> <BottomSheet.HeaderSubtitle>바텀시트 서브타이틀</BottomSheet.HeaderSubtitle> <BottomSheet.HeaderRight> <TextButton as='button' color='secondary' size='medium' underline onClick={() => console.log('제출')}> 제출하기 </TextButton> </BottomSheet.HeaderRight> </BottomSheet.Header> <BottomSheet.Body spacing={{ x: '200', top: '200' }}>본문</BottomSheet.Body> <BottomSheet.Footer> <Flex gap='100' justifyContent='flex-end'> <Button onClick={() => setOpen(false)}>취소</Button> <Button onClick={() => setOpen(false)}>확인</Button> </Flex> </BottomSheet.Footer> </BottomSheet> </>`

---

### Breadcrumb | `import { Breadcrumb } from '@atelier/blue' | 몰드: import { Breadcrumb } from '@atelier-mold/admin'`
현재 위치를 알려주고 페이지를 쉽게 이동할 수 있도록 하는 네비게이션 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — Breadcrumb.Item 및 Breadcrumb.Dropdown으로 구성 · hideCurrent: boolean = false — 마지막 아이템 숨김 (PageHeader 조합 시) · highlightCurrent: boolean = false — 현재 페이지 타이틀 강조 표시
**subs**: Breadcrumb.Item(Breadcrumb을 구성하는 각 아이템. as prop으로 <button> / <a> 전환 가능) · Breadcrumb.Dropdown(Breadcrumb을 구성하는 드롭다운. value, defaultValue, onChange, title/aria-label prop 지원) · Breadcrumb.DropdownItem(Breadcrumb.Dropdown을 구성하는 아이템 (Dropdown.Option 기반)) · prop(설명) · children(Breadcrumb.DropdownItem으로 구성) · value(선택된 값 (제어)) · defaultValue(기본 선택 값 (비제어)) · onChange(변경 콜백) · title(시트 상단 제목 (aria-label과 택1)) · aria-label(접근성 레이블 (title과 택1))
**note**: 현재 위치를 알려주고 페이지를 쉽게 이동할 수 있도록 해요.. `Breadcrumb.Item`은 `<button>`으로 동작해요. `as` prop으로 변경할 수 있어요.
**ex**: `const [value, setValue] = useState('/event/1') <Breadcrumb> <Breadcrumb.Item href="#">Breadcrumb</Breadcrumb.Item> <Breadcrumb.Item href="#서브컴포넌트">서브컴포넌트</Breadcrumb.Item> <Breadcrumb.Dropdown defaultValue='#breadcrumbitem' onChange={(e) => setValue(e.target.value)}> <Breadcrumb.DropdownItem value="#breadcrumbitem" indent={false}>Breadcrumb.Item</Breadcrumb.DropdownItem> <Breadcrumb.DropdownItem value="#breadcrumbdropdown" indent={false}>Breadcrumb.Dropdown</Breadcrumb.DropdownItem> </Breadcrumb.Dropdown> <Breadcrumb.Item href="#기본-사용법">기본 사용법</Breadcrumb.Item> </Breadcrumb>`

---

### Button | `import { Button } from '@atelier/blue' | 몰드: import { Button } from '@atelier-mold/admin'`
다양한 액션을 수행하는 버튼 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — 버튼 내용 · color: 'primary' \ = 'primaryDanger' \ — 'secondary' \ · size: 'small' \ = 'medium' \ — 'large' \ · disabled: boolean = - — 비활성화 여부 · width: string \ = number — 'fit-content' · variant: 'fill' \ = 'outline' — 'fill' · loading: boolean = false — 로딩 여부 (variant='outline'일 때 무시) · loadingText: string = '불러오는 중' — 로딩 접근성 텍스트 · ellipsis: boolean = true — 텍스트 말줄임 처리 · colorOverride: { background?, border?, text? } = - — 색상 재정의 (디자인 협의 후 사용) · as: 'a' \ = 'button' \ — ElementType
**subs**: Button.Left(아이콘을 Button 좌측에 배치) · Button.Right(chevron-down 아이콘을 Button 우측에 배치. 🚨 Left와 동시 사용 금지)
**note**: `variant="outline"`일 때는 `loading` prop을 무시해요.. 서브컴포넌트로 배치하는 아이콘에는 기본 크기가 적용되고, (`size="xlarge"`에서 24px, 그 외 16px) `<Icon size>`를 직접 지정해서 수동으로 변경할 수 있어요.. 디자인 가이드라인에 따르면 `Button.Left`와 `Button.Right`를 동시에 배치해선 안돼요.. `Button`은 `width` prop을 가지고 있어요. `style` 속성으로 width를 넣지 마세요.
**ex**: `const [submitting, setSubmitting] = useState(false) <Button color='primary' loading={submitting} size='medium' type='submit' variant='fill'> <Button.Left> <CheckIcon /> </Button.Left> <strong>구매</strong> 확인 <Button.Right> <PlusIcon /> </Button.Right> </Button>`

---

### Card
이 컴포넌트는 클레이블루의 Card 컴포넌트를 확장한 컴포넌트에요.
**props**: children: ReactNode — - · padding: Padding | { x?: Padding; y?: Padding; top?: Padding; bottom?: Padding | undefined; left?: Padding | undefined; right?: Padding | undefined; } | undefined = none — 상하좌우 패딩 - “x”, “y”, “top”, “bottom”, “left”, “right” 필드를 객체로 전달해 개별 패딩 값을 지정할 수 있어요. · width: string | number = 100% — 너비

---

### CardHeader | `import { CardHeader } from '@atelier/blue' | 몰드: import { CardHeader } from '@atelier-mold/admin'`
카드 상단에서 타이틀 역할을 하는 헤더 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — CardHeader 내부 콘텐츠
**subs**: CardHeader.Title('medium' (기본값 'medium')) · CardHeader.SubTitle(보조 제목) · CardHeader.Right(오른쪽 부분. 캡션/버튼/토글 등 다양한 컴포넌트 배치 가능) · CardHeader.Description(타이틀의 부가 설명) · CardHeader.Caption(타이틀 오른쪽 캡션) · CardHeader.Action(툴팁 또는 모달을 여는 TextButton. as='Tooltip' 또는 as='TextButton') · prop(설명) · size(Title의 크기) · as(렌더링할 요소) · children(제목 내용) · prop(설명) · as(동작 유형) · onClick(as='TextButton'일 때 클릭 핸들러) · content(as='Tooltip'일 때 툴팁 내용) · title(as='Tooltip'일 때 툴팁 제목)
**note**: 카드 상단에서 타이틀 역할을 해요.
**ex**: `<CardHeader> <CardHeader.SubTitle>서브타이틀</CardHeader.SubTitle> <CardHeader.Title as='h2'>타이틀</CardHeader.Title> <CardHeader.Caption>캡션</CardHeader.Caption> <CardHeader.Right>...right</CardHeader.Right> <CardHeader.Description>디스크립션입니다.</CardHeader.Description> <CardHeader.Action as='TextButton' onClick={() => {}}> 버튼 </CardHeader.Action> </CardHeader>`

---

### Checkbox | `import { Checkbox } from '@atelier/blue' | 몰드: import { Checkbox } from '@atelier-mold/admin'`
1개 이상의 옵션을 선택할 때 사용하는 체크박스 컴포넌트입니다.
**props**: children: React.ReactNode = - — 레이블 요소 · fullWidth: boolean = false — 레이블 너비 100% · invalid: boolean = - — 유효성 검증 실패 상태 · simple: boolean = false — 간결한 형태 (outline 아이콘) · small: boolean = false — 작은 크기 (simple=false일 때) · description: ReactNode = - — 하단 설명 문구 (simple=false일 때) · indeterminate: boolean = false — 중간 상태 (simple=false일 때) · tooltip: string = - — 툴팁 문구 (simple=true일 때) · checked: boolean = - — 체크 여부 (제어) · defaultChecked: boolean = - — 초기 체크 여부 (비제어) · onChange: ChangeEventHandler<HTMLInputElement> = - — 변경 콜백 · disabled: boolean = - — 비활성화 여부
**note**: 1개 이상의 옵션을 선택할 때 사용해요.. 하단 설명이나 툴팁 문구를 함께 제공할 수 있어요.
**ex**: `const [checked, setChecked] = useState(false) <Checkbox id='controlled' name='controlled' small={false} description='설명이 필요한 경우' checked={checked} onChange={(e) => setChecked(e.target.checked)} > 선택 </Checkbox>`

---

### Chip | `import { Chip } from '@atelier/blue' | 몰드: import { Chip } from '@atelier-mold/admin'`
버튼, 단일 선택, 다중 선택, 탭 등 다양한 액션을 할 수 있는 컴팩트한 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — Chip 내부 요소 · selected: boolean = false — 선택 여부 · maxWidth: string \ = number — 'none' · ellipsis: boolean = true — 텍스트 말줄임 · onClick: MouseEventHandler = - — 클릭 이벤트 · disabled: boolean = - — 비활성화 여부
**subs**: Chip.Left(왼쪽 영역. 아이콘(16px 고정)과 이미지(24px 고정) 배치 가능) · Chip.Right(오른쪽 영역. 아이콘(16px 고정). onClick prop으로 버튼화 가능. 🚨 하위에 IconButton 금지)
**note**: 버튼, 단일 선택, 다중 선택, 탭 등 다양한 액션을 할 수 있는 컴팩트한 컴포넌트예요.. 체크박스, 버튼, 탭의 용도로 사용될 수 있어요. 각각의 용도에 맞게 접근성 속성을 넣어주세요.
**ex**: `const [selected, setSelected] = useState(false) const toggle = () => setSelected(!selected) <Chip role='checkbox' aria-checked={selected} selected={selected} onClick={toggle}> <Chip.Left> <CheckIcon /> </Chip.Left> 텍스트 <Chip.Right> <CloseIcon color='fg_secondary' /> </Chip.Right> </Chip>`

---

### CircleLoading | `import { CircleLoading } from '@atelier/blue' | 몰드: import { CircleLoading } from '@atelier-mold/admin'`
UI 로딩이나 특정 액션이 진행 중임을 알리는 로딩 컴포넌트입니다.
**props**: label: string = - — 접근성 문구 (제공 시 aria-busy=true 적용) · small: boolean = false — 작은 크기 모드 · color: FgColor = - — 아이콘 색상 (small=true일 때만) · size: number \ = string — 24
**note**: UI 로딩이나 특정 액션이 진행 중임을 알리는 컴포넌트예요.. 사용자 경험이 중요한 페이지는 `SkeletonLoading`을 사용해주세요.
**ex**: `<CircleLoading small={false} label='상품 목록을 로딩 중이에요' />`

---

### Container | `import { Container } from '@atelier/blue' | 몰드: import { Container } from '@atelier-mold/admin'`
바깥 여백을 지정할 때 사용하는 레이아웃 컴포넌트입니다.
**props**: children: React.ReactNode = - — 내부에 렌더링되는 요소 · negative: boolean = false — true이면 CSS margin으로 적용 · spacing: SpacingMap<Spacing> = - — 바깥 여백 (x, y, top, bottom, left, right)
**note**: 바깥 여백을 지정할 때 사용해요.. blue 디자인토큰의 `spacing` 값이 prop으로 사용돼요.. `className`과 `styleObject`로 추가 스타일링을 해주세요.. `spacing`은 CSS padding으로 구현되어있어요. 단, `negative={true}`면 CSS margin으로 적용돼요.. Container 내부 요소 사이의 여백을 지정하려면 `Flex` 컴포넌트를 사용해주세요.
**ex**: `display: 'flex', alignItems: 'center', justifyContent: 'center', backgroundColor: '#1A7CFF', width: '250px', height: '250px', color: 'white', <Container style={containerStyle} negative={false} spacing={{ x: '200', y: '200' }}> <Flex style={{ width: '100%', height: '100%', background: '#D5D7D9' }} /> </Container>`

---

### DatePicker | `import { DatePicker } from '@atelier/blue' | 몰드: import { DatePicker } from '@atelier-mold/admin'`
현재와 가까운 날짜를 선택할 때 유용한 달력 컴포넌트입니다.
**props**: open: boolean = - — 제어 방식 열림 여부 · onClose: () => void = - — 닫을 때 콜백 · children: React.ReactNode = - — Trigger 등 하위 요소 · id: string = - — 요소의 고유한 ID · initCalendarDate: Date = new Date() — 달력 최초 표시 날짜 · value: Date \ = DateRange — - · width: number = 680 — Desktop 달력 너비 · disable: { before?, after?, fn? } = - — 선택 불가 날짜 설정 · weekStartsOn: WeekDay = 0 — 첫 요일 (0: 일요일) · range: boolean = false — 범위 선택 여부 · withFooter: boolean = false — Footer 표시 여부 · position: 'left' \ = 'right' \ — 'center' · sameDate: boolean = false — 시작/종료 같은 날짜 (range=true) · onDateChange: (value?) => void = - — 날짜 변경 콜백 · resetValue: Date \ = DateRange — 이전 선택 값
**subs**: DatePicker.Trigger(커스텀 트리거. children 없으면 기본 버튼 트리거 제공) · DatePicker.InputTrigger(직접 입력 가능한 트리거) · DatePicker.TimePicker(시간 설정이 필요한 경우 사용)
**note**: 현재와 가까운 날짜를 선택할 때 유용해요.. 기본으로 설정한 날짜 기준으로 달력을 볼 수 있어요.. 범위 형태로 날짜를 지정할 수 있어요.. 지정 불가능한 날짜를 설정할 수 있어요.
**ex**: `const [date, setDate] = useState() setDate(date) <DatePicker onDateChange={handleChange} initCalendarDate={new Date()} value={date} range={false} disable={{ after: new Date() }} weekStartsOn='1' > <DatePicker.Trigger width='100%' /> </DatePicker>`

---

### Dialog | `import { Dialog } from '@atelier/blue' | 몰드: import { Dialog } from '@atelier-mold/admin'`
중요한 내용을 공지하거나 프로모션할 때 사용하는 오버레이 컴포넌트입니다.
**props**: children: React.ReactNode = - — 내부에 렌더링되는 요소 · open: boolean = - — 제어 방식 열림 여부 · onClose: () => void = - — 닫을 때 콜백 · role: string = 'dialog' — Dialog의 role · closeOnClickOutside: boolean = false — 바깥 영역 클릭 시 닫기 여부 · keepOldZIndex: boolean = - — (deprecated) 이전 z-index 사용
**subs**: Dialog.Header(Header 영역. OverlayHeader 기반) · Dialog.HeaderLeft(Header 내 왼쪽 영역) · Dialog.HeaderTitle(Header 내 중앙 영역) · Dialog.HeaderRight(Header 내 오른쪽 영역) · Dialog.Body(Body 영역 (Container 기반)) · Dialog.Footer(Footer 영역. OverlayFooter 기반) · Dialog.Trigger(비제어 방식에서 Dialog를 여는 트리거) · Dialog.Close(감싸진 요소를 클릭하면 Dialog 닫힘)
**note**: 중요한 내용을 공지하거나 프로모션 할 때 사용해요.. `Dialog.Footer` 내부에 버튼 정렬이 필요하다면 `Flex` 컴포넌트를 사용해주세요.. 제어, 비제어 방식 모두 지원해요.
**ex**: `const [open, setOpen] = useState(false) <> <Button onClick={() => setOpen(true)}>Dialog 열기</Button> <Dialog open={open} onClose={() => setOpen(false)}> <Dialog.Header> <Dialog.HeaderLeft> <Dialog.Close> <IconButton label="닫기"><CloseIcon /></IconButton> </Dialog.Close> </Dialog.HeaderLeft> </Dialog.Header> <Dialog.Body> 본문 내용 </Dialog.Body> <Dialog.Footer> <Button type='button' onClick={() => setOpen(false)}>닫기</Button> </Dialog.Footer> </Dialog> </>`

---

### Divider | `import { Divider } from '@atelier/blue' | 몰드: import { Divider } from '@atelier-mold/admin'`
콘텐츠를 구분할 때 사용하는 구분선 컴포넌트입니다.
**props**: orientation: 'horizontal' \ = 'vertical' — 'horizontal' · color: LineColor = 'line_secondary' — 색상 · thickness: '1px' \ = '8px' — '1px' · size: string \ = number — '100%' · margin: { start?: Spacing; end?: Spacing } = { start: 'none', end: 'none' } — (deprecated) 전·후 마진
**note**: 콘텐츠를 구분할 때 사용해요.
**ex**: `<Flex flexDirection='column'> <Button color='secondary' width='100%'>버튼1</Button> <Spacer y='300' /> <Divider color='line_tertiary' thickness='1px' /> <Spacer y='300' /> <Button color='secondary' width='100%'>버튼2</Button> </Flex>`

---

### Dropdown | `import { Dropdown } from '@atelier/blue' | 몰드: import { Dropdown } from '@atelier-mold/admin'`
데스크탑 뷰포트에서 트리거 요소 위치를 기준으로 열리는 팝업 컴포넌트입니다.
**props**: open: boolean = - — 제어 방식 열림 여부 · defaultOpen: boolean = - — 비제어 방식 초기 열림 · onClose: () => void = - — 닫을 때 콜백 · onChange: ChangeEventHandler<HTMLSelectElement> = - — 옵션 변경 콜백 · enableVirtualFocus: boolean = false — 가상 포커스 사용 여부 · virtualFocusKey: string = '' — 가상 포커스 초기화 키 · fitToViewport: boolean = - — 뷰포트 맞춤 여부 · multiple: boolean = false — 다중 선택 여부 · value: string \ = string[] — - · defaultValue: string \ = string[] — - · title: string = - — 시트 상단 제목 · aria-label: string = - — 접근성 라벨
**subs**: Dropdown.Trigger(비제어 트리거 영역) · Dropdown.Option(선택 가능한 옵션 (option role 기반)) · Dropdown.OptionLeft(옵션 왼쪽 UI 영역) · Dropdown.OptionRight(옵션 오른쪽 UI 영역) · Dropdown.OptionGroup(옵션 그룹핑)
**note**: 데스크탑 뷰포트에서 트리거 요소 위치를 기준으로 열리는 팝업이에요.. 옵션 목록 중 1개를 선택하거나 커스텀 UI를 구성할 수 있어요.. 제어, 비제어 방식을 지원해요.. 접근성 지원을 위해 `aria-label` 또는 `title` prop을 전달해주세요.
**ex**: `const [open, setOpen] = useState(false) const [option, setOption] = useState('') <Dropdown open={open} onClose={() => setOpen(false)} value={option} onChange={(e) => setOption(e.target.value)} > <Dropdown.Trigger> <Button onClick={() => setOpen(true)}>옵션 선택</Button> </Dropdown.Trigger> <Dropdown.Option value='option1'>옵션 1</Dropdown.Option> <Dropdown.Option value='option2'>옵션 2</Dropdown.Option> <Dropdown.Option value='option3' disabled>옵션 3 (비활성화)</Dropdown.Option> </Dropdown>`

---

### Flex | `import { Flex } from '@atelier/blue' | 몰드: import { Flex } from '@atelier-mold/admin'`
CSS Flexbox 속성을 지원하는 레이아웃 컴포넌트입니다.
**props**: gap: Spacing \ = \${Spacing} ${Spacing}\ — - · rowGap: Spacing = - — 상하 간격 · columnGap: Spacing = - — 좌우 간격 · flexDirection: string = 'row' — flex-direction · flexWrap: string = 'nowrap' — flex-wrap · alignItems: string = - — align-items · justifyContent: string = - — justify-content · inline: boolean = false — inline-flex 여부 · flexGrow: number = - — flex-grow · flexShrink: number = - — flex-shrink
**subs**: Flex.Item(Flex 자식 아이템의 flex 속성을 제어)
**note**: CSS Flexbox 속성을 지원하는 컴포넌트에요.. 내부 아이템 간격을 지정할 때는 `gap`, `rowGap`, 또는 `columnGap` prop에 `Spacing` 토큰 값을 전달해주세요.. `className`과 `style` prop으로 스타일링 할 수 있어요.. `flexDirection`, `flexGrow`, `flexShrink`, `flexWrap`, `alignItems`, `justifyContent` 등의 스타일은 className 및 style 대신 prop으로 설정해주세요.. gap 미지원 브라우저 대응을 위해 margin 스타일을 활용하므로, 자식 요소에 margin이 필요하면 별도 요소로 감싸주세요.. `disableNativeGap` 속성으로 gap 미지원 브라우저 동작을 테스트할 수 있어요. (테스트 목적으로만 사용)
**ex**: `<Flex gap='300' flexDirection='column'> <div>Box 1</div> <div>Box 2</div> </Flex>`

---

### Form | `import { Form } from '@atelier/blue' | 몰드: import { Form } from '@atelier-mold/admin'`
HTML `form` 요소를 기반으로 폼 레이블, 컨트롤 요소, 메시지를 제공하는 컴포넌트입니다.
**props**: fieldGap: Spacing = '200' — Field 사이 간격 · vertical: boolean = false — 레이블/컨트롤 수직 배치 · wide: boolean = false — 레이블 너비 확장
**subs**: Form.Field(Control, Label, Message를 묶어주는 컴포넌트) · Form.Label(Control과 연결되는 레이블) · Form.LabelDetails(레이블 상세 설명 (툴팁, 다이얼로그 등)) · Form.Control(TextInput, Checkbox 등 컨트롤 요소 영역) · Form.Message(Control과 연결되는 검증 메시지)
**note**: HTML `form` 요소를 기반으로 폼 레이블, 컨트롤 요소, 메시지를 제공해요.. 폼 레이블, 컨트롤 요소, 메시지는 `Form.Field`로 구성돼요.. `Form.Field`는 여러 개로 구성할 수 있어요.. 보다 자세한 사항은 [Form 컴포넌트 가이드](https://cloud.wiki.woowa.in/wiki/x/VI_hBg)를 참고해주세요.
**ex**: `<Form vertical={false} wide={false} fieldGap='200'> <Form.Field validateOn='change'> <Form.Label is='required' height={48} tooltip='툴팁 문구'> 레이블 </Form.Label> <Form.Control> <TextInput name='basic' placeholder='플레이스홀더' width='300px' small={false} /> </Form.Control> <Form.Message asError match={({ basic }) => basic === ''} variant='invalid'> 텍스트를 입력해주세요. </Form.Message> </Form.Field> </Form>`

---

### PageHeader
이 컴포넌트는 클레이블루의 PageHeader 컴포넌트를 확장한 컴포넌트에요.
**props**: children(필수): ReactNode — - · children(필수): ReactNode — - · items(필수): (PageHeaderBreadcrumbItem | PageHeaderBreadcrumbItem[])[] — - · hideCurrent: boolean = false — 마지막 “Breadcrumb.Item”을 숨길지 여부 - “PageHeader”와 조합할 때 사용해요. · highlightCurrent: boolean = false — 현재 페이지의 타이틀을 강조 표시할지 여부 - 하단에 별도의 타이틀로 두어 강조 표시해요. - 현재 페이지가 Breadcrumb.Item으로 구성된 경우에만 동작해요. · children(필수): ReactNode — - · children(필수): ReactNode — - · children(필수): ReactNode — - · as(필수): "Tooltip" | "TextButton" — - · title: string — 툴팁의 제목 · content(필수): ReactNode — 툴팁의 컨텐츠 - 단순 문자열 또는 직접 작성한 리액트 컴포넌트 모두 가능해요 · onClick(필수): MouseEventHandler\<HTMLButtonElement\> — -

---

### ServiceHeader
Service Header는 화면 상단에 위치해요. 메뉴 Icon, 로그아웃, 권한관리같은 기본적인 기능을 제공해요.
**props**: onToggleMenu: () =\> void — 왼쪽 메뉴 버튼을 클릭했을 때 실행할 함수를 입력해주세요. · children(필수): ReactNode — - · as: keyof ReactHTML — - · children(필수): ReactNode — - · children(필수): ReactNode — - · children(필수): ReactNode — - · value: string — - · defaultValue: string — - · projectList: { label: string; value: string; }[] — - · onChange(필수): ChangeEventHandler\<HTMLSelectElement\> — - · src: string — - · placeholderText: string — - · alt: string — - · onClick: () =\> void — - · env: "local" | "dev" | "development" | "beta" | "prod" | "production" — 프로젝트 환경을 넣어주세요. (로컬 - local, 개발 - dev, development, 베타 - beta, 운영 - prod, production) · custom: { variant: "neutral" | "lightGreen" | "green" | "lightOrange" | "orange" | "lightRed" | "red" | "lightMint" | "mint" | "lightBlue" | "inverse" | "overlay" | "purple" | "lightPurple"; label: string; } — - · as: "a" | ComponentClass\<any, any\> | FunctionComponent\<any\> — -

---

### Highlight | `import { Highlight } from '@atelier/blue' | 몰드: import { Highlight } from '@atelier-mold/admin'`
특별히 강조하고 싶은 텍스트 영역에 사용하는 스타일 컴포넌트입니다.
**props**: children: React.ReactNode = - — 강조할 텍스트 요소
**note**: 특별히 강조하고 싶은 텍스트 영역에 사용하는 스타일이에요.
**ex**: `<> <Highlight>강조 문구</Highlight> 텍스트 <Typography variant="title3"> <Highlight>강조 텍스트</Highlight> </Typography> </>`

---

### HintTooltip | `import { HintTooltip } from '@atelier/blue' | 몰드: import { HintTooltip } from '@atelier-mold/admin'`
별도의 트리거 액션 없이 자동으로 노출되는 말풍선 툴팁 컴포넌트입니다.
**props**: open: boolean = - — 툴팁 노출 여부 (필수) · content: React.ReactNode = - — 툴팁 컨텐츠 (필수) · children: React.ReactNode = - — 트리거 요소 (필수) · fixedWidth: boolean = false — 너비 280px 고정 여부 · onClose: () => void = - — 닫기 콜백 (사용 시 Close 버튼 활성화) · hasCloseButton: boolean = false — 닫기 버튼 표시 · margin: { top?, bottom?, left?, right? } = { 16, 16, 16, 16 } — 오버레이 마진 · direction: 'top' \ = 'bottom' \ — 'left' \ · container: RefObject<HTMLElement> = undefined — 부모 엘리먼트 · asChild: boolean = false — children 그대로 렌더링 · portal: boolean = true — body 하위 렌더링 · duration: number = - — 지속시간 (ms, 최소 4초) · autoPosition: boolean = true — Overflow 위치 재조정 · preventBlurOnClose: boolean = false — 닫힐 때 blur 방지 · preventAutoClose: boolean = false — 자동 닫힘 방지 · gap: number = - — 트리거-콘텐츠 간격 (px)
**note**: 탭, 클릭과 같은 별도의 트리거 액션이 없어도 자동으로 노출되는 툴팁이에요.. 힌트툴팁이 열리는 시점은 사용처에서 직접 관리해요.. 닫기 버튼이 없는 경우, 툴팁 등장 후 4초 후에 자동으로 닫히며 지속시간은 커스텀 가능해요.. 닫기 버튼이 있는 경우엔 자동으로 닫히지 않고, 버튼 클릭을 통해서만 닫을 수 있어요.
**ex**: `const [open, setOpen] = useState(false) <HintTooltip open={open} content="고객이 결제한 금액" onClose={() => setOpen(false)}> <Button color="primary" size="large" variant="fill" type="button" onClick={() => setOpen(true)}> 입점 신청하기 </Button> </HintTooltip>`

---

### IconButton | `import { IconButton } from '@atelier/blue' | 몰드: import { IconButton } from '@atelier-mold/admin'`
아이콘만으로 구성된 버튼 컴포넌트입니다.
**props**: children: React.ReactNode = - — 아이콘 요소 (필수) · label: string = - — 접근성 텍스트 (필수) · color: 'transparent' \ = 'ghost' \ — 'inverse' · shape: 'circle' \ = 'square' — 'circle' · size: 'xsmall' \ = 'small' \ — 'medium' \ · shadow: boolean = false — box-shadow 적용 여부 · as: React.ElementType = 'button' — 렌더링 태그
**note**: 아이콘만으로 구성된 버튼이에요.. `label` prop으로 접근성 텍스트를 반드시 제공해주세요.
**ex**: `<IconButton color='ghost' label='홈으로 이동' shape='square' size='medium' type='button'> <HomeIcon /> </IconButton>`

---

### ImageViewer | `import { ImageViewer } from '@atelier/blue' | 몰드: import { ImageViewer } from '@atelier-mold/admin'`
여러 이미지 또는 파일명을 슬라이드로 제공하는 뷰어 컴포넌트입니다.
**props**: open: boolean = - — 제어 방식 열림 여부 · defaultOpen: boolean = - — 비제어 방식 초기 열림 · onClose: () => void = - — 닫기 콜백 · title: string = - — 뷰어 제목 (필수) · images: Image[] = - — 이미지/파일 목록 (필수) · defaultIndex: number = - — 최초 진입 이미지 인덱스 · fullscreen: boolean = false — 전체 화면 (모바일은 항상 활성) · children: React.ReactElement = - — Trigger 영역 (비제어)
**note**: 여러 이미지 또는 파일명을 슬라이드로 제공할 때 사용해요.. 제어, 비제어 방식을 지원해요.. URL 마지막 경로에 파일명이 포함되어야 해요.. 이미지 확장자가 아니면, 파일 정보만 제공해요.
**ex**: `const [open, setOpen] = useState(false) const images = [ { url: 'https://placehold.co/360x528', alt: '이미지 1 설명' }, { url: 'https://placehold.co/360x202', alt: '이미지 2 설명' }, { url: 'https://placehold.co/720x1048', alt: '이미지 3 설명' }, { url: 'https://example.com/report.pdf' }, ] <> <Button onClick={() => setOpen(true)}>뷰어 열기</Button> <ImageViewer open={open} onClose={() => setOpen(false)} title='이미지 뷰어' images={images} fullscreen={false} /> </>`

---

### Link | `import { Link } from '@atelier/blue' | 몰드: import { Link } from '@atelier-mold/admin'`
텍스트 링크 컴포넌트입니다. 페이지 이동 목적으로 사용합니다.
**props**: children: string = - — 링크 텍스트 (필수) · variant: TypographyProps['variant'] = - — 텍스트 스타일 · color: 'primary' \ = 'secondary' \ — 'accent' · underline: boolean = true — 밑줄 여부 · as: React.ElementType = 'a' — 외부 링크 컴포넌트 · to: string = - — React Router to prop · href: string = - — 링크 URL
**note**: 기본적으로 폰트사이즈 및 letter-spacing, line-height 본문과 동일해요.. `variant` prop을 활용해서 인접한 본문에서 사용되는 Typography와 동일한 variant로 변경할 수 있어요.. `TextButton`과는 다르게 별도의 패딩을 갖고 있지 않아요.. 페이지 이동의 목적이 아닌 데이터 또는 상태를 변경하는 작업에는 링크 대신 Button을 사용해요.
**ex**: `<Link color='primary' underline variant='body3'> 링크 </Link>`

---

### ListHeader | `import { ListHeader } from '@atelier/blue' | 몰드: import { ListHeader } from '@atelier-mold/admin'`
리스트를 구성할 때 타이틀 역할을 하는 컴포넌트입니다.
**props**: children: React.ReactNode = - — 내부에 렌더링되는 요소 (필수)
**subs**: ListHeader.Title(제목. as prop으로 Tooltip/링크/텍스트 태그 지정 가능) · ListHeader.Caption(타이틀 오른쪽 캡션) · ListHeader.Right(오른쪽 영역 (캡션/버튼/토글 등))
**note**: 리스트를 구성할 때 타이틀 역할을 해요.
**ex**: `<ListHeader> <Badge>배지</Badge> <ListHeader.Title as='h2'>타이틀</ListHeader.Title> <ListHeader.Caption>캡션</ListHeader.Caption> <ListHeader.Right> <Flex gap='100'> <Button size='small' variant='outline'> 취소 </Button> <Button size='small'>적용</Button> </Flex> </ListHeader.Right> </ListHeader>`

---

### ListItem | `import { ListItem } from '@atelier/blue' | 몰드: import { ListItem } from '@atelier-mold/admin'`
클릭, 탭과 같은 액션 가능한 리스트를 구성할 때 사용하는 컴포넌트입니다.
**props**: children: React.ReactNode = - — 내부에 렌더링되는 요소 (필수) · selected: boolean = - — 선택 상태 여부 · divider: boolean = - — 구분선 표시 여부 · as: 'button' \ = 'div' — 'button' · clickable: boolean = - — div일 때 클릭 스타일 적용
**subs**: ListItem.Left(왼쪽 영역) · ListItem.Right(오른쪽 영역) · ListItem.Title(중앙 상단 영역 (타이틀)) · ListItem.Description(중앙 하단 영역 (설명))
**note**: 클릭, 탭과 같은 액션 가능한 리스트를 구성할 때 사용해요.. `<li>` 태그 필요시, 사용처에서 ListItem을 감싸서 사용해주세요.. `<a>` 또는 `<Link>`로 구성하려면, `as` prop을 `div`로 설정한 후, `ListItem`을 감싸서 사용해주세요.
**ex**: `<ListItem> <ListItem.Left> <img src="https://atelier-assets.betabaemin.in/images/blue/material_bulb@2x.png" /> </ListItem.Left> <ListItem.Title>타이틀</ListItem.Title> <ListItem.Description>설명</ListItem.Description> <ListItem.Right> <ChevronRightIcon /> </ListItem.Right> </ListItem>`

---

### MessageBox | `import { MessageBox } from '@atelier/blue' | 몰드: import { MessageBox } from '@atelier-mold/admin'`
사장님이 언제든지 볼 수 있어야 하는 정보를 안내할 때 사용하는 컴포넌트에요.
**props**: children: React.ReactNode = (필수) — MessageBox 내부에 렌더링되는 요소. MessageBox.Icon, MessageBox.Badge, MessageBox.Title, MessageBox.Caption, MessageBox.Subtext, MessageBox.Action을 사용 · variant: 'default' \ = 'onGray' \ — 'warning' \ · direction: 'vertical' \ = 'horizontal' — 'vertical'
**subs**: MessageBox.Icon(타이틀 왼쪽의 Icon 영역. color, alt prop 지원) · MessageBox.Badge(타이틀 왼쪽의 Badge 영역. children, variant prop 지원) · MessageBox.Title(타이틀 영역) · MessageBox.Caption('right')) · MessageBox.Subtext('fg_secondary'만 사용 가능 (기본: fg_secondary)) · MessageBox.Action(버튼 영역. 최대 2개까지 노출 가능)
**note**: 사장님이 언제든지 볼 수 있어야 하는 정보를 안내할 때 사용해요.. 사장님이 반드시 확인해야 하는 정보는 `Alert`, `Dialog` 등으로 안내해요.. 한번만 봐도 되는 정보는 `Snackbar`로 안내해요.
**ex**: `<MessageBox variant='danger' direction='horizontal'> <MessageBox.Icon /> <MessageBox.Badge variant='lightRed'>취소</MessageBox.Badge> <MessageBox.Title>승인 취소</MessageBox.Title> <MessageBox.Caption>2021.12.31 (수) 오후 02:00</MessageBox.Caption> <MessageBox.Subtext>아래사항을 수정 후 다시 신청중에 있어요.</MessageBox.Subtext> <MessageBox.Action> <TextButton onClick={() => console.log('수정하기')}>수정하기</TextButton> </MessageBox.Action> </MessageBox>`

---

### NotificationBadge | `import { NotificationBadge } from '@atelier/blue' | 몰드: import { NotificationBadge } from '@atelier-mold/admin'`
상태와 부가적인 정보를 나타낼 때 사용하는 컴포넌트에요.
**props**: aria-label: string = - — 상태가 변할 때마다 Screen Reader에 읽힐 문구 · dotSize: 'small' \ = 'medium' — 'small' · new: boolean = - — NewIcon으로 표시 (count, dotSize와 함께 사용 불가) · count: number = - — 표시할 숫자. 100 이상은 99+로 표시 (new, dotSize와 함께 사용 불가) · className: string = - — 추가 CSS 클래스 · style: React.CSSProperties = - — 인라인 스타일
**note**: 상태와 부가적인 정보를 나타낼 때 사용해요.. 기본적으로 `small` 사이즈의 Dot으로 표시해요.. props에 따라 3가지 다른 모양을 가질 수 있어요:
**ex**: `<Flex gap='200'> <NotificationBadge dotSize='small' /> <NotificationBadge new /> <NotificationBadge count={99} /> </Flex>`

---

### OverlayFooter | `import { OverlayFooter } from '@atelier/blue' | 몰드: import { OverlayFooter } from '@atelier-mold/admin'`
Overlay 하단에 고정되는 영역으로 버튼을 조합해서 사용하는 컴포넌트에요.
**props**: children: React.ReactNode = (필수) — OverlayFooter 내부에 렌더링되는 요소 · spacing: ContainerProps['spacing'] = '250' — OverlayFooter의 padding값 · showDivider: boolean = - — Overlay 컨텐츠 영역과 구분하기 위한 Divider 표시 여부
**note**: Overlay 하단에 고정되는 영역으로 버튼을 조합해서 사용해요.. 컨테이너 안에 버튼을 자유롭게 조합해서 사용할 수 있어요.. 컨테이너의 좌우 패딩은 `spacing.x`, 상하 패딩은 `spacing.y` prop으로 조절할 수 있어요.. 내부 구현은 `Flex` 컴포넌트를 활용해주세요.
**ex**: `<div style={{ backgroundColor: '#fff' }}> <OverlayFooter spacing={"600"}> <Flex gap='200' justifyContent='flex-end'> <Button>취소</Button> <Button>확인</Button> </Flex> </OverlayFooter> </div>`

---

### OverlayHeader | `import { OverlayHeader } from '@atelier/blue' | 몰드: import { OverlayHeader } from '@atelier-mold/admin'`
Overlay의 헤더영역을 구성할 때 사용하는 컴포넌트에요.
**props**: children: React.ReactNode = (필수) — OverlayHeader 내부에 렌더링되는 요소. 서브컴포넌트를 조합하여 사용
**subs**: OverlayHeader.Title(타이틀 영역) · OverlayHeader.Subtitle(서브타이틀 영역) · OverlayHeader.Left(왼쪽에 들어갈 컴포넌트 영역) · OverlayHeader.Right(오른쪽에 들어갈 컴포넌트 영역) · OverlayHeader.Bottom(하단에 들어갈 컴포넌트 영역)
**note**: Overlay의 헤더영역을 구성할 때 사용해요.
**ex**: `<div style={{ backgroundColor: '#fff' }}> <OverlayHeader> <OverlayHeader.Left> <IconButton size='large' label='닫기' shape='square'> <ArrowLeftIcon /> </IconButton> </OverlayHeader.Left> <OverlayHeader.Title> <Typography as='h2' variant='body1' weight='medium'> 타이틀 </Typography> </OverlayHeader.Title> <OverlayHeader.Right> <TextButton as='button' color='secondary' size='medium' underline onClick={() => console.log('입점 신청')}> 입점 신청 </TextButton> </OverlayHeader.Right> <OverlayHeader.Bottom> <Divider /> </OverlayHeader.Bottom> </OverlayHeader> </div>`

---

### PageIndicator | `import { PageIndicator } from '@atelier/blue' | 몰드: import { PageIndicator } from '@atelier-mold/admin'`
컨텐츠의 양과 사용자의 현재 위치를 인지할 수 있도록 도와주는 컴포넌트에요.
**props**: total: number = (필수) — 전체 페이지 · current: number = (필수) — 현재 페이지 · aria-label: string = '전체 ${total} 페이지 중 ${current} 페이지' — 접근성 텍스트 · variant: 'count' \ = 'linear' \ — 'dot' · color: 'default' \ = 'inverse' (count) / 'default' \ — 'white' (dot)
**note**: 컨텐츠의 양과 사용자의 현재 위치를 인지할 수 있도록 도와요.
**ex**: `<Flex gap='300' alignItems='center'> <PageIndicator current={1} total={10} /> <PageIndicator color='inverse' current={1} total={10} /> </Flex>`

---

### PageSheet | `import { PageSheet } from '@atelier/blue' | 몰드: import { PageSheet } from '@atelier-mold/admin'`
양이 많은 작업에 사장님을 집중시킬 때 사용하는 전체 화면 시트 컴포넌트에요.
**props**: children: React.ReactNode = (필수) — 내부 요소. 서브컴포넌트를 조합하여 사용 · bgColor: 'bg_primary' \ = 'fill_black' \ — 'sf_level300' · closeOnClickOutside: boolean = false — 바깥 클릭 시 닫기 여부 · desktopFrame: 'medium' \ = 'large' \ — 'xlarge' · desktopWidth: string \ = number — - · desktopHeight: 'fit' \ = string — variant별 상이 · open: boolean = - — 열림/닫힘 (제어 방식) · onClose: () => void = - — 닫힐 때 호출
**subs**: PageSheet.Header(Header 영역. OverlayHeader 기반) · PageSheet.HeaderLeft(Header 좌측 영역) · PageSheet.HeaderRight(Header 우측 영역) · PageSheet.HeaderTitle(Header 타이틀 영역) · PageSheet.HeaderSubtitle(Header 서브타이틀 영역) · PageSheet.Body(Body 영역. Container 기반. spacing prop 지원) · PageSheet.Footer(Footer 영역. OverlayFooter 기반. Button은 항상 size=large) · PageSheet.Trigger(클릭 시 PageSheet 열기 (비제어 방식)) · PageSheet.Close(클릭 시 PageSheet 닫기 (비제어 방식))
**note**: 양이 많은 작업에 사장님을 집중시킬 때 사용해요.. 제어, 비제어 방식을 모두 지원해요.
**ex**: `const [open, setOpen] = useState(false) <> <Button onClick={() => setOpen(true)}>페이지시트 열기</Button> <PageSheet open={open}> <PageSheet.Header> <PageSheet.HeaderLeft> <IconButton size='large' label='닫기' shape='square' onClick={() => setOpen(false)}> <CloseIcon /> </IconButton> </PageSheet.HeaderLeft> <PageSheet.HeaderTitle>타이틀</PageSheet.HeaderTitle> <PageSheet.HeaderSubtitle>서브타이틀</PageSheet.HeaderSubtitle> <PageSheet.HeaderRight> <TextButton as='button' color='secondary' size='medium' underline onClick={() => console.log('신청서 전송')}> 입점 신청 </TextButton> </PageSheet.HeaderRight> </PageSheet.Header> <PageSheet.Body spacing={{ x: '200', top: '200' }}>본문</PageSheet.Body> <PageSheet.Footer> <Flex gap='100' justifyContent='flex-end'> <Button onClick={() => setOpen(false)}>취소</Button> <Button onClick={() => setOpen(false)}>확인</Button> </Flex> </PageSheet.Footer> </PageSheet> </>`

---

### Pagination | `import { Pagination } from '@atelier/blue' | 몰드: import { Pagination } from '@atelier-mold/admin'`
콘텐츠를 여러 개의 페이지로 나눠 쉽게 탐색할 수 있는 컴포넌트에요.
**props**: variant: 'ellipsisNumber' \ = 'number' \ — 'hiddenNumber' · total: number = (필수, number/ellipsisNumber) — 전체 페이지 수. 1이하면 렌더링 안됨 · page: number = - — 현재 페이지 (제어 방식) · defaultPage: number = - — 초기 페이지 (비제어 방식) · onPageChange: (page: number) => void = - — 페이지 변경 시 호출 · children: React.ReactNode = - — hiddenNumber variant에서 PrevButton/NextButton 배치
**subs**: Pagination.PrevButton(이전 페이지 버튼 (hiddenNumber variant에서 사용)) · Pagination.NextButton(다음 페이지 버튼 (hiddenNumber variant에서 사용))
**note**: 콘텐츠를 여러 개의 페이지로 나눠 쉽게 탐색할 수 있어요.. total 값이 1이하면 컴포넌트가 렌더링되지 않아요.. `hiddenNumber` variant는 `<Pagination.PrevButton />`, `<Pagination.NextButton />` 서브컴포넌트를 사용해요.
**ex**: `const [value, setValue] = useState(1) <Pagination page={value} total={15} onPageChange={(nextPage) => setValue(nextPage)} />`

---

### Radio | `import { Radio } from '@atelier/blue' | 몰드: import { Radio } from '@atelier-mold/admin'`
여러 옵션 중 하나만 선택할 때 사용하는 컴포넌트에요.
**props**: children: React.ReactNode = - — 레이블 요소. 문자열이면 body1 스타일, ReactElement면 커스텀 UI · description: React.ReactNode = - — 하단 설명 문구 · tooltip: string = - — 툴팁 문구 (children이 문자열일 때만 사용 가능) · fullWidth: boolean = false — 레이블 영역 너비를 100%로 설정 · small: boolean = false — 작게 표현할지 여부 · id: string = 자동 생성 — 전달하지 않으면 자동 생성 · name: string = - — 그룹으로 묶으려면 같은 name 지정 · value: string = - — Radio 값 · checked: boolean = - — 체크 여부 (제어) · defaultChecked: boolean = - — 초기 체크 여부 (비제어) · onChange: ChangeEventHandler<HTMLInputElement> = - — 변경 시 호출 · disabled: boolean = - — 비활성화 여부
**note**: 여러 옵션 중 하나만 선택할 때 사용해요.. 하단 설명이나 툴팁 문구를 함께 제공할 수 있어요.
**ex**: `const [selectedOption, setSelectedOption] = useState('1') const handleChange = (e) => setSelectedOption(e.target.value) <> <Radio id='basic-option1' name='basic' value='1' description='설명이 필요한 경우' tooltip='툴팁 문구' small={false} checked={selectedOption === '1'} onChange={handleChange} > 옵션 1 </Radio> <Radio id='basic-option2' name='basic' value='2' small={false} checked={selectedOption === '2'} onChange={handleChange} > 옵션 2 </Radio> </>`

---

### RadioButtonGroup | `import { RadioButtonGroup } from '@atelier/blue' | 몰드: import { RadioButtonGroup } from '@atelier-mold/admin'`
버튼 형태의 라디오 목록을 그룹으로 묶어 선택할 수 있게 해주는 컴포넌트에요.
**props**: name: string = (필수) — 라디오 그룹 이름 · value: string = - — 현재 선택된 값 (제어) · defaultValue: string = - — 초기 선택값 (비제어) · onChange: (e: ChangeEvent<HTMLInputElement>) => void = - — 변경 시 호출 · disabled: boolean = - — 전체 비활성화 여부 · children: React.ReactNode = (필수) — RadioButtonGroup.Item을 배치 · small: boolean = false — 아이템 레이블 크기. true면 body2, false면 body1
**subs**: RadioButtonGroup.Item(버튼 형태의 라디오 아이템) · prop(설명) · id(레이블과 연결되는 고유 ID) · label(레이블 텍스트) · value(선택 시 onChange에 전달되는 값) · disabled(개별 아이템 비활성화 여부)
**note**: 버튼 형태의 라디오 목록을 그룹으로 묶어 선택할 수 있게 해주는 컴포넌트에요.. 아이템은 최소 2개, 최대 4개까지 제공하는 것을 권장해요.
**ex**: `const [value, setValue] = useState('blue') <RadioButtonGroup name='pkg' small={false} disabled={false} value={value} onChange={(e) => setValue(e.target.value)} > <RadioButtonGroup.Item value='blue' label='블루' disabled={false} /> <RadioButtonGroup.Item value='core' label='코어' /> <RadioButtonGroup.Item value='mint' label='민트' /> </RadioButtonGroup>`

---

### SearchBar | `import { SearchBar } from '@atelier/blue' | 몰드: import { SearchBar } from '@atelier-mold/admin'`
모바일에서 검색 페이지 상단에 고정되는 컴포넌트에요.
**props**: children: React.ReactNode = (필수) — 내부 요소. SearchBar.Left, SearchBar.Right 서브컴포넌트 배치 · placeholder: string = - — 플레이스홀더 텍스트 · value: string = - — 입력값 (제어) · defaultValue: string = - — 초기값 (비제어) · onChange: ChangeEventHandler<HTMLInputElement> = - — 입력 변경 시 호출 · name: string = - — input name 속성
**subs**: SearchBar.Left(왼쪽 영역. 뒤로가기/홈 버튼 등 배치) · SearchBar.Right(오른쪽 영역. 장바구니 버튼 등 배치)
**note**: 모바일에서 검색 페이지 상단에 고정되는 컴포넌트예요.
**ex**: `const [value, setValue] = useState('') <form onSubmit={() => console.log(value)} > <SearchBar placeholder='검색해볼까요?' value={value} onChange={(e) => setValue(e.target.value)}> <SearchBar.Left> <IconButton label='뒤로가기'> <ArrowLeftIcon /> </IconButton> </SearchBar.Left> <SearchBar.Right> <IconButton label='장바구니로 이동'> <CartIcon /> </IconButton> </SearchBar.Right> </SearchBar> </form>`

---

### SearchInput | `import { SearchInput } from '@atelier/blue' | 몰드: import { SearchInput } from '@atelier-mold/admin'`
검색 키워드를 입력할 수 있는 컴포넌트에요. form과 연결해서 사용해요.
**props**: children: React.ReactNode = - — 내부 요소 (SearchInput.Option 등) · variant: 'outline' \ = 'fill' — 'outline' · autoComplete: string = 'off' — 브라우저 자동완성 · spellCheck: boolean = false — 스펠링 체크 · autoHighlight: boolean = true — 일치하는 값 하이라이트 (Option 있을 때만) · hasSubmitButton: boolean = true — submit IconButton 사용 여부 · openDropdown: boolean = - — Option 목록 열림 여부 (제어) · onChange: (e, detail?) => void = - — 변경 핸들러. Option 매치 시 { optionID } 전달 · onClickResetButton: MouseEventHandler = - — reset 핸들러 · containerRef: RefObject<HTMLElement> = - — Dropdown 위치 기준 엘리먼트 · placeholder: string = - — 플레이스홀더 · value: string = - — 입력값 (제어) · defaultValue: string = - — 초기값 (비제어) · small: boolean = - — 작은 사이즈 · disabled: boolean = - — 비활성화
**subs**: SearchInput.Option(자동완성 옵션 아이템. label (필수), optionID, children prop 지원) · SearchInput.OptionPlaceholder(Option이 없을 때 표시할 UI) · SearchInput.SearchButton('submit', 기본: 'submit'))
**note**: 검색 키워드를 입력할 수 있어요.. form과 연결해서 사용해주세요.
**ex**: `const [value, setValue] = useState('') <form onReset={() => setValue('')} onSubmit={(e) => e.preventDefault()}> <SearchInput placeholder='검색해볼까요?' value={value} onChange={(e) => setValue(e.target.value)} small={false} disabled={false} /> </form>`

---

### SectionHeader | `import { SectionHeader } from '@atelier/blue' | 몰드: import { SectionHeader } from '@atelier-mold/admin'`
섹션 단위를 구성할 때 타이틀 역할을 하는 컴포넌트에요.
**props**: children: React.ReactNode = (필수) — SectionHeader 내부에 렌더링되는 요소. 서브컴포넌트 조합
**subs**: SectionHeader.Title(제목 영역. as prop으로 'Tooltip', 'a', 텍스트 태그('h2'~'h6', 'p', 'span') 지정 가능. 기본: 'p') · SectionHeader.Description(타이틀의 부가 설명 영역) · SectionHeader.Caption(타이틀 오른쪽 및 Right 영역에 올 수 있는 캡션) · SectionHeader.Right(오른쪽 부분. 캡션/버튼/토글 등 다양한 컴포넌트 배치 가능. alignStart prop으로 flex-start 정렬 지원) · prop(설명) · children(오른쪽에 배치할 요소) · alignStart(true일 때 alignSelf: flex-start. SectionTitle이 여러 줄일 때 사용)
**note**: 섹션 단위를 구성할 때 타이틀 역할을 해요.
**ex**: `<SectionHeader> <MenubookIcon size='16' /> <SectionHeader.Title as='Tooltip' title='툴팁 타이틀' content='툴팁 콘텐츠'> 타이틀 </SectionHeader.Title> <SectionHeader.Caption>캡션</SectionHeader.Caption> <SectionHeader.Right> <Flex gap='100'> <Button size='small' variant='outline'> 취소 </Button> <Button size='small'>적용</Button> </Flex> </SectionHeader.Right> <SectionHeader.Description> 디스크립션입니다. 텍스트가 길어질 경우 자동으로 줄이 늘어납니다. 디스크립션입니다. </SectionHeader.Description> </SectionHeader>`

---

### Select
이 컴포넌트는 클레이블루의 Select 컴포넌트를 확장한 컴포넌트에요.
**props**: multiple: boolean = false — 다중 선택 가능 여부  - 활성화되면 옵션을 선택해도 드롭다운이 닫히지 않아요. 백드롭 영역을 눌러 닫을 수 있어요. - 🚨 native에서는 지원되지 않아요. · value: string | string[] — 옵션값 (제어) - “multiple”이 false이고, 선택 중인 값이 없다면 빈 문자열을 전달해주세요. - “multiple”이 true이고, 선택 중인 값이 없다면 빈 배열을 전달해주세요. · defaultValue: string | string[] — 옵션값 (비제어) · showCount: boolean = false — 다중 선택 시 ‘외 n건’ 레이블 제공 여부 · maxSelectionCount: number = Infinity — 선택 가능한 최대 옵션 수 · onChange: (event: ChangeEvent\<HTMLSelectElement\>, value: string | string[]) =\> void — 선택 옵션 변경 시 호출되는 이벤트 핸들러 · small: boolean = false — 트리거 UI 높이를 작게 표현할지 여부 - “false”: 48px - “true”: 40px · width: 328 | 180 | 600 | "180px" | "328px" | "600px" | "100%" = 100% — 너비 · invalid: boolean — 유효성 검증 통과 여부  - true인 경우 유효성 검증에 실패한 상태로 취급돼요. - 서버 응답(비동기)에 따른 유효성 처리가 필요하거나 ref에 접근할 수 없는 경우 활용해주세요. · native: boolean — option 요소 기반의 네이티브 셀렉트 여부 · placeholder: string — 드롭다운 방식(“native”가 false인 경우)에서 제공할 플레이스홀더  - 플레이스홀더는 옵션 목록으로 제공되지 않아요. · enableVirtualFocus: boolean = false — 드롭다운 옵션 목록을 가상 포커스로 제어할지 여부 · virtualFocusKey: string = &#x27;&#x27; — Option의 가상 포커스를 초기화 시키기 위한 키 - “enableVirtualFocus”가 “true”일 때만 동작해요. - 값이 달라질때마다 가상 포커스를 첫 아이템으로 초기화 시켜요. - Option들이 동적으로 추가되거나 사라지는 경우(검색 필터링)에 사용해요. · fitToViewport: boolean — - · fetchNextPage: () =\> void — - · hasNextPage: boolean — 무한스크롤이 가능한지 여부를 지정해요. · ref: Ref\<HTMLSelectElement\> — Allows getting a ref to the component instance. Once the component unmounts, React will set “ref.current” to “null” (or call the ref with “null” if you passed a callback ref). · value(필수): string — 옵션 값  - 선택 시 “onChange” prop으로 전달돼요. · color: "danger" — 옵션 문구 색상 · disabled: boolean — 옵션 비활성화 여부 · indent: boolean = true — 옵션 왼쪽 공간의 들여쓰기 여부 · children: ReactNode — - · tooltip: string — 마우스 호버 시 제공되는 툴팁 문구 · label: string — 접근성 또는 선택된 레이블로 활용되는 문구 · hidden: boolean = false — Dropdown 안에 보이지 않는 옵션을 DOM에 유지하고 싶을 때 사용해요. - 검색 기능 등에서 Select.Option 목록이 동적으로 변경될 때, 이전에 선택했던 옵션이나 전체 옵션 목록을 계속 유지해야하는 경우에 사용해요. - e.g. 검색어에 따라 옵션이 필터링되더라도, 선택된 값은 유지되어야 하는 경우

---

### SkeletonLoading | `import { SkeletonLoading } from '@atelier/blue' | 몰드: import { SkeletonLoading } from '@atelier-mold/admin'`
사용자 경험이 중요한 페이지에서 로딩 중임을 알리는 컴포넌트에요.
**props**: variant: 'body' \ = 'header' \ — 'image' · width: string \ = number — variant별 상이 (body/header: 80%, image: 100%) · height: string \ = number — variant별 상이 (body: 12px, header: 24px, image: 100%) · multiline: boolean \ = \${string}%\ — false
**note**: 사용자 경험이 중요한 페이지에서 로딩 중임을 알리는 컴포넌트에요.
**ex**: `<div style={{ width: '100px', height: '100px' }}> <SkeletonLoading variant='header' multiline='90%' /> </div>`

---

### Snackbar | `import { Snackbar, SnackbarProvider } from '@atelier/blue' | 몰드: import { Snackbar, SnackbarProvider } from '@atelier-mold/admin'`
일시적으로 표시되는 메시지를 보여줄 때 사용하는 컴포넌트에요.
**props**: children: React.ReactNode = (필수) — 내부 요소. 서브컴포넌트 조합 · duration: number \ = 'infinite' — 4000 (Action 있으면 8000) · position: 'top' \ = 'bottom' — 'bottom' · offset: string = 데스크톱 40px, 모바일 16px — 컨테이너로부터 이격 거리 · type: 'default' \ = 'success' \ — 'warning' \ · zIndex: string \ = number — elevation.level3(300) · open: boolean = - — 열림/닫힘 (제어). 미전달 시 마운트 즉시 표시 · onClose: () => void = - — 닫힐 때 호출
**subs**: Snackbar.Title(Title 영역) · Snackbar.Description(Description 영역) · Snackbar.Action('horizontal', 기본: 'horizontal')) · Snackbar.Close(닫기 이벤트 제공)
**note**: 일시적으로 표시되는 메시지를 보여줄 때 사용해요.. `open` prop을 넘겨주지 않으면 마운트될 때 바로 보여져요.
**ex**: `const [open, setOpen] = useState(false) <> <Button onClick={() => setOpen(!open)}>Snackbar {open ? '닫기' : '열기'}</Button> <Snackbar type="success" open={open} onClose={() => setOpen(false)}> <Snackbar.Title>타이틀</Snackbar.Title> <Snackbar.Description>디스크립션</Snackbar.Description> <Snackbar.Action> <Snackbar.Close> <TextButton>닫기</TextButton> </Snackbar.Close> </Snackbar.Action> </Snackbar> </>`

---

### Spacer | `import { Spacer } from '@atelier/blue' | 몰드: import { Spacer } from '@atelier-mold/admin'`
컴포넌트 간 간격을 줄 때 사용하는 레이아웃 유틸리티 컴포넌트입니다.
**props**: x: Spacing \ = string — - · y: Spacing \ = string — -
**note**: 컴포넌트 간 간격을 주고 싶을 때 사용해요.. x, y prop 중 하나를 선택하면 방향도 함께 설정돼요.
**ex**: `<div style={{ display: 'flex' }}> <Button>버튼1</Button> <Spacer x='200' /> <Button>버튼2</Button> </div>`

---

### Stepper | `import { Stepper } from '@atelier/blue' | 몰드: import { Stepper } from '@atelier-mold/admin'`
1 이상의 수량을 입력할 때 사용하는 컴포넌트입니다. '+', '-' 버튼 또는 키보드 입력으로 수량을 변경할 수 있습니다.
**props**: min: number = 1 — 최솟값. value가 min보다 작으면 min으로 설정되고 (-) 버튼이 비활성화 · max: number = 9999 — 최댓값. value가 max보다 크면 max으로 설정되고 (+) 버튼이 비활성화 · step: number = 1 — 증감버튼 클릭 시 값이 변경되는 단위 크기 · value: StepperValue = - — 값 (제어) · onChange: (e, value) => void = - — 값 변경 시 호출되는 핸들러 · defaultValue: number = - — 초기 선택 값 (비제어) · onOverflow: () => void = - — 최댓값일 때 '+' 버튼을 누르면 호출되는 핸들러 · suffix: string = - — value 값 뒤에 붙는 문자열 · invalid: boolean = - — 유효성 검증 통과 여부 · gap: Spacing = 'none' — 간격 · small: boolean = true — 크기 · hideMinusButton: boolean = false — 감소 버튼 숨김 처리 여부
**note**: 1 이상의 수량을 입력할 때 사용해요.. '+', '-' 버튼 또는 키보드 입력으로 수량을 변경할 수 있어요.
**ex**: `const [value, setValue] = useState(1000) <div style={{ width: 200 }}> <Stepper min={1} max={9999} step={1} value={value} onChange={(event) => setValue(event.target.value)} disabled={false} invalid={false} /> </div>`

---

### Switch | `import { Switch } from '@atelier/blue' | 몰드: import { Switch } from '@atelier-mold/admin'`
기능을 켜거나 끌 때 사용하는 토글 컴포넌트입니다.
**props**: checked: boolean = - — 체크 여부 (제어) · defaultChecked: boolean = - — 체크 여부 (비제어) · onChange: ChangeEventHandler<HTMLInputElement> = - — 변경 이벤트 핸들러 · disabled: boolean = false — 비활성화 여부 · small: boolean = false — 작은 크기 여부
**note**: 기능을 켜거나 끌 때 사용하는 컴포넌트에요.
**ex**: `const [checked, setChecked] = useState(false) <Switch checked={checked} disabled={false} small={false} onChange={(e) => setChecked(e.target.checked)} > 켜기 </Switch>`

---

### Tab | `import { Tab } from '@atelier/blue' | 몰드: import { Tab } from '@atelier-mold/admin'`
페이지에서 같은 레벨의 정보를 분류할 때 사용하는 탭 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — Tab 내부에 렌더링되는 요소 · isSubTab: boolean = false — SubTab으로 사용할 지 여부 · value: string = - — 현재 선택된 아이템의 value (제어) · defaultValue: string = - — 초기에 선택된 아이템 value (비제어) · onValueChange: (value, changeType) => void = - — 탭 변경 시 콜백 · interaction: 'swipe' \ = 'scroll' \ — 'none' · infinite: boolean = false — Swipe 시 Infinite 방식 여부 · activation: 'automatic' \ = 'manual' — 'automatic' · fill: boolean = false — 탭 너비 꽉 채움 여부 · preventTriggerAutofocus: boolean = false — 트리거 autofocus 비활성화 여부 · isSubTabScrollable: boolean = false — 데스크탑 SubTab 좌우 스크롤 여부
**subs**: Tab.Trigger(트리거 영역. 보여질 Tab Content를 선택할 때 사용) · Tab.TriggerImage(트리거 내 이미지를 제공할 때 사용) · Tab.ExpandedButton(트리거 목록을 펼칠 수 있는 버튼) · Tab.Content(사용자에게 보여지는 콘텐츠 영역) · prop(설명) · children(탭에서 보여질 Label 영역) · value(Content와 연결되는 value 값) · dot(Dot Badge 유무) · prop(설명) · expandedLabel(펼쳐졌을 때 보여지는 label)
**note**: 페이지에서 같은 레벨의 정보를 분류할 때 사용해요.. Tab, Sub Tab 두 가지 옵션중 상황에 맞게 골라서 사용해요. 둘의 작동 방식은 동일해요.. 위계가 필요하다면 Tab → Sub Tab 순으로 사용해요.. 중복 선택이 불가능한 컴포넌트이므로 Filter 역할로서 SubTab을 사용하지 않아요. 필요한 경우 Chip을 사용해요.
**ex**: `const COLORS = ['red', 'blue', '#EFF8FB', 'yellow', 'pink'] <div style={{ height: '50vh', background: COLORS[num] }}> {`content ${num}`} </div> <div style={{ height: '40vh' }}> <Tab defaultValue='1' interaction='swipe' isSubTab={false}> <Tab.Trigger value='1' dot> <Tab.TriggerImage src='https://atelier-assets.betabaemin.in/images/blue/category_snack@2x.png' alt='' /> Trigger 1 </Tab.Trigger> <Tab.Trigger value='2'>Trigger 2</Tab.Trigger> <Tab.Trigger value='3'>Trigger 3</Tab.Trigger> <Tab.Content value='1'>{renderContent(1)}</Tab.Content> <Tab.Content value='2'>{renderContent(2)}</Tab.Content> <Tab.Content value='3'>{renderContent(3)}</Tab.Content> </Tab> </div>`

---

### Table | `import { Table } from '@atelier/blue' | 몰드: import { Table } from '@atelier-mold/admin'`
행과 열로 데이터를 보여주는 테이블 컴포넌트입니다.
**props**: columns: (TableColumn \ = TableColumnGroup)[] — (필수) · data: DataType[] = (필수) — row 데이터 · headerBackgroundColor: BgColor \ = SfColor \ — FillColor · emptyMessage: ReactNode = - — data가 빈 배열일 때 메시지 · cellPlaceholder: ReactNode = '' — 빈 셀 플레이스홀더 · small: boolean = - — 테이블 td 사이즈 · narrow: boolean = false — 테이블 td 좌우 padding (true: 8px, false: 16px) · draggable: boolean \ = ((id) => boolean) — - · maxHeight: string \ = number — - · rowSelection: 'none' \ = 'checkbox' \ — 'radio' · pagination: PaginationProps = - — 하단 페이지네이션 · border: boolean \ = { outer, innerVertical } — false · hoverDirection: 'row' \ = 'column' \ — 'both'
**note**: 행과 열로 데이터를 보여줘요.. data 프롭으로 값을 넘기고, column 프롭의 `cell`을 사용해 셀을 커스텀할 수 있어요.. `columns`에서 설정한 `id`는 `data` 배열의 각 요소의 `key`값과 일치해야 해요. 단, `column.cell`에서 `data`를 참조하지 않는다면, `key`와 관계 없이 고유한 `id`를 사용할 수 있어요.. 무한 스크롤은 `ref`를 사용해 구현해주세요.
**ex**: `const columns = [ { title: '이름', id: 'name' }, { title: '나이', id: 'age' }, { title: '지역', id: 'region' } ] const data = [ { name: '홍길동', age: 20, region: '서울' }, { name: '김철수', age: 30, region: '수원' } ] return <Table columns={columns} data={data} />`

---

### Tag | `import { Tag } from '@atelier/blue' | 몰드: import { Tag } from '@atelier-mold/admin'`
컨텐츠 키워드를 노출해 내용을 인지할 수 있도록 돕는 역할을 하는 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — Tag 내부에 렌더링되는 요소 · as: 'span' \ = 'button' \ — 'a' · hashtag: boolean = false — 좌측 '#' 표시 여부 · underline: boolean = true — 밑줄 표시 여부 (button, a에서만 동작)
**subs**: Tag.DeleteButton(삭제 버튼 영역)
**note**: 컨텐츠 키워드를 노출해 내용을 인지할 수 있도록 돕는 역할을 해요.
**ex**: `return <Tag hashtag>태그</Tag>`

---

### TextArea
이 컴포넌트는 클레이블루의 TextArea 컴포넌트를 확장한 컴포넌트에요.
**props**: value: string — - · defaultValue: string — - · small: boolean — - · width: 328 | 180 | 600 | "180px" | "328px" | "600px" | "100%" — - · rows: number — - · invalid: boolean — - · sizing: "fixed" | "auto" | "manual" — - · multiple: boolean — 다중 요소 입력 여부 · delimiter: string — 다중 요소 입력 구분자 · variant: "float" — 소수점 입력 여부 · ref: Ref\<HTMLTextAreaElement\> — Allows getting a ref to the component instance. Once the component unmounts, React will set “ref.current” to “null” (or call the ref with “null” if you passed a callback ref). · children(필수): ReactNode — - · children(필수): ReactNode — -

---

### TextButton | `import { TextButton } from '@atelier/blue' | 몰드: import { TextButton } from '@atelier-mold/admin'`
좁은 영역에서 공간을 절약하기 위해 사용하는 텍스트 버튼 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — 버튼 내부 콘텐츠 · color: 'primary' \ = 'primaryDanger' \ — 'secondary' \ · size: 'xsmall' \ = 'small' \ — 'medium' \ · underline: boolean = false — 밑줄 여부 (secondary, tertiary에서만 적용) · colorOverride: FgColor = - — 텍스트 색상 재정의 · ellipsis: boolean = true — 텍스트 말줄임 처리 여부
**subs**: TextButton.Left(왼쪽 아이콘 영역) · TextButton.Right(오른쪽 아이콘 영역)
**note**: 좁은 영역에서 공간을 절약하기 위해 사용하는 버튼이에요.. 아이콘의 기본 크기는 16px로 적용돼요. `<Icon size>`를 직접 지정해서 수동으로 변경할 수도 있어요.. 디자인 가이드라인에 따르면 `Left`와 `Right` 아이콘을 동시에 둘 다 배치할 수는 없어요.
**ex**: `<TextButton color='primary' size='medium' type='button'> <TextButton.Left> <CheckIcon /> </TextButton.Left> <strong>조회</strong> 확인 </TextButton>`

---

### TextInput
이 컴포넌트는 클레이블루의 TextInput 컴포넌트를 확장한 컴포넌트에요.
**props**: type: "number" | "text" | "tel" | "url" | "email" | "password" — 다중요소 / 소수점 입력 시에는 type을 지정할 수 없습니다. (‘text’로 고정) · defaultValue: string | number — - · value: string | number — 다중요소 / 소수점 입력 시에는 type을 지정할 수 없습니다. (‘text’로 고정) · small: boolean — - · width: 328 | 180 | 600 | "180px" | "328px" | "600px" | "100%" — - · invalid: boolean — - · textAlign: "center" | "left" | "right" — - · delimiter: string — 다중 요소 입력 구분자 · variant: "float" — 소수점 입력 여부 · ref: Ref\<HTMLInputElement\> — Allows getting a ref to the component instance. Once the component unmounts, React will set “ref.current” to “null” (or call the ref with “null” if you passed a callback ref). · children(필수): ReactNode — - · children(필수): ReactNode — - · children(필수): ReactNode — -

---

### TextListItem | `import { TextListItem } from '@atelier/blue' | 몰드: import { TextListItem } from '@atelier-mold/admin'`
정적인 텍스트 요소를 나열할 때 사용하는 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — 내부에 렌더링되는 요소 · indent: Spacing = 'none' — 들여쓰기 · layout: 'block' \ = 'space-between' — -
**subs**: TextListItem.Content(실제 내용이 들어가는 영역. 단독 사용 가능) · TextListItem.Label(Label 영역. 단독 사용 가능) · prop(설명) · as(HTML 태그) · children(내용) · variant(왼쪽 심볼) · typographyProps(텍스트 스타일) · alignItems(아이템 정렬 방향) · index(variant가 'number'일 때 보여지는 숫자) · numberMarkerWidth(number variant에서 숫자 너비) · paddingTop(상단 여백) · prop(설명) · as(HTML 태그) · children(내용) · variant(왼쪽 심볼) · typographyProps(텍스트 스타일) · width(Label 너비) · alignItems(아이템 정렬 방향) · paddingTop(상단 여백)
**note**: 정적인 텍스트 요소를 나열할 때 사용해요.. TextListItem.Label 혹은 TextListItem.Content를 단독으로 사용해도 괜찮아요.. 기존의 Data List는 TextListItem을 통해 만들 수 있어요.. indent prop을 통해 들여쓰기를 할 수 있어요.
**ex**: `<TextListItem indent='none' layout='block'> <TextListItem.Label as='dt' width={'120px'}> <ClockIcon color='fg_secondary' size={16} /> <span>주문 시각</span> </TextListItem.Label> <TextListItem.Content typographyProps={{ color: 'fg_secondary', variant: 'body2' }} as='dd' > <span>2023.02.15.(수) 오후03:21:52</span> <Badge size='small' variant='lightBlue'>배지</Badge> </TextListItem.Content> </TextListItem>`

---

### Thumbnail | `import { Thumbnail } from '@atelier/blue' | 몰드: import { Thumbnail } from '@atelier-mold/admin'`
이미지를 나타낼 때 사용하는 컴포넌트입니다. 폭을 변경하면 지정한 비율을 유지하면서 사이즈가 변경됩니다.
**props**: children: React.ReactNode = - — 내부에 렌더링되는 요소 · as: 'div' \ = 'a' \ — 'button' \ · ratio: '1:1' \ = '16:9' \ — '3:2' \ · width: number \ = string — '100%' · height: number \ = string — 'auto' · circle: boolean = false — 원 모양 여부 (1:1에서만) · backgroundColor: FillColor = 'fill_secondary' — 배경색 · hoverEffect: boolean = false — 마우스 인터랙션 효과 · inactive: boolean = false — 비활성화 여부 · border: boolean = true — 테두리 표시 여부 · borderWidth: number \ = string — '1px' · borderColor: LineColor = 'line_primary' — 테두리 색상
**subs**: Thumbnail.Image('img' 태그로 렌더링하는 Image 영역) · Thumbnail.Info('div' 태그로 렌더링하는 Info 영역) · Thumbnail.Scrim(요소 전체를 어둡게 표현하는 레이어) · Thumbnail.ScrimDescription(Scrim 위에 표시하는 텍스트) · Thumbnail.Picture('picture' 태그로 렌더링하는 Picture 영역) · prop(설명) · src(이미지 소스 URL) · fallbackSrc(이미지 로드 실패 시 대체 URL) · alt(대체 텍스트) · objectFit(이미지 fit 방식) · prop(설명) · spacing(내부 여백)
**note**: 이미지 나타낼 때 사용하는 컴포넌트에요.. 폭을 변경하면 지정한 비율을 유지하면서 사이즈가 변경돼요.
**ex**: `const SRC = 'https://example.com/image.jpg' const FALLBACK_SRC = 'https://placehold.co/200' <Thumbnail ratio='1:1' width={200}> <Thumbnail.Image src={SRC} fallbackSrc={FALLBACK_SRC} alt='대체 텍스트' /> <Thumbnail.Info> <Flex justifyContent='space-between'> <Badge variant='green'>판매중</Badge> <IconButton color='ghost' label='찜하기' onClick={() => alert('찜콩')}> <HeartFillIcon color='fg_danger' /> </IconButton> </Flex> </Thumbnail.Info> </Thumbnail>`

---

### TimePicker | `import { TimePicker } from '@atelier/blue' | 몰드: import { TimePicker } from '@atelier-mold/admin'`
시간을 선택할 수 있는 컴포넌트입니다. desktop에서는 ComboBox, mobile에서는 ActionSheet로 표현합니다.
**props**: children: React.ReactElement = - — 커스텀 Trigger · small: boolean = false — Input 높이 · width: number \ = string — '100%' · showClockIcon: boolean = false — 시계 아이콘 표시 여부 · value: Time \ = '' — - · defaultValue: Time = - — 시간값 (비제어) · onTimeChange: (value?) => void = - — 시간 변경 핸들러 · sameDate: boolean = false — 같은 날짜 여부 · listStart: Time = { hour: 9, minute: 0 } — 목록 시작 시간 · listEnd: Time = { hour: 23, minute: 30 } — 목록 끝 시간 · listInterval: number = 30 — 목록 시간 간격(분) · exact: boolean = true — 정확한 시간 일치 필수 여부 · timeFormat: '12h' \ = '24h' — '12h' · listDisableFn: (time) => boolean = - — 시간 제외 판단 함수
**note**: 시간을 선택할 수 있어요.. desktop에서는 ComboBox, mobile에서는 ActionSheet로 표현해요.
**ex**: `const [value, setValue] = useState({ hour: 9, minute: 0 }) <TimePicker value={value} onTimeChange={(time) => setValue(time)} />`

---

### TimeRangePicker | `import { TimeRangePicker } from '@atelier/blue' | 몰드: import { TimeRangePicker } from '@atelier-mold/admin'`
시작 시간과 종료 시간을 선택할 수 있는 컴포넌트입니다.
**props**: small: boolean = false — 높이 · width: number \ = string — '100%' · value: TimeRange = - — range 값 (제어) · defaultValue: TimeRange = - — range 값 (비제어) · sameDate: boolean = false — 같은 날짜 여부 · onRangeChange: (range) => void = - — 값 변경 핸들러
**subs**: TimeRangePicker.Start(시작 시간 TimePicker) · TimeRangePicker.End(종료 시간 TimePicker) · prop(설명) · label(라벨 텍스트) · placeholder(플레이스홀더) · disabled(비활성화 여부)
**note**: 시작 시간과 종료 시간을 선택할 수 있어요.
**ex**: `const [range, setRange] = useState([undefined, undefined]) <TimeRangePicker value={range} onRangeChange={(r) => setRange(r)} small> <TimeRangePicker.Start placeholder='오전 12:00' label='시작시간' /> <TimeRangePicker.End placeholder='오전 12:00' label='종료시간' disabled /> </TimeRangePicker>`

---

### Tooltip | `import { Tooltip } from '@atelier/blue' | 몰드: import { Tooltip } from '@atelier-mold/admin'`
특정 엘리먼트 위치에서 간단한 부가정보를 서술하고자 할 때 사용하는 컴포넌트입니다.
**props**: fixedWidth: boolean = false — 너비 280px 고정 여부 · title: string = - — 툴팁 제목 · content: React.ReactNode = (필수) — 툴팁 컨텐츠 · direction: 'top' \ = 'bottom' \ — 'left' \ · margin: { top, bottom, left, right } = { 16, 16, 16, 16 } — 오버레이 마진 · delay: number = 200 — 등장 지연시간 (ms) · asChild: boolean = false — children을 그대로 렌더링 여부 · container: RefObject<HTMLElement> = - — 부모 엘리먼트 · portal: boolean = true — portal 렌더링 여부 · children: React.ReactNode = (필수) — 트리거 요소 · autoPosition: boolean = true — 위치 재조정 여부 · onOpen: () => void = - — 노출 시 핸들러
**note**: 특정 엘리먼트 위치에서 간단한 부가정보를 서술하고자 할 때 사용해요.. 툴팁에 children으로 전달하는 컴포넌트가 툴팁을 트리거하는 역할을 해요. 트리거 요소는 하나의 단일 컴포넌트여야 해요.. PC: 터치 타겟에 hover시 노출, 커서를 밖으로 옮기면 미노출.. 모바일: 트리거를 탭하거나 focus될 때 노출, 스크롤 또는 바깥 터치 시 미노출.. 명시된 direction이 없는 경우 기본적으로 top 포지션으로 노출되나, 공간이 부족한 경우 다른 포지션으로 노출될 수 있어요.
**ex**: `<Tooltip title="베이직" content="고객이 결제한 금액"> <CircleInformationIcon color='fg_secondary' /> </Tooltip>`

---

### TopBar | `import { TopBar } from '@atelier/blue' | 몰드: import { TopBar } from '@atelier-mold/admin'`
현재 페이지의 위치를 알려주고 페이지 이동 등의 기능을 제공하는 상단 바 컴포넌트입니다.
**props**: children: React.ReactNode = (필수) — 내부에 렌더링되는 요소 · position: 'static' \ = 'sticky' \ — 'fixed' · inverse: boolean = - — 스크롤 최상단 시 색상 반전 · bgColor: FillColor = - — 배경색 (지정 시 inverse 무관하게 고정)
**subs**: TopBar.Title(타이틀 영역) · TopBar.Logo(로고 영역. 로고 이미지의 경로를 src prop으로 전달) · TopBar.Left(왼쪽 영역) · TopBar.Right(오른쪽 영역) · prop(설명) · children(타이틀 내용) · tooltip(호버 시 제공되는 툴팁 메시지) · prop(설명) · src(로고 이미지 URL) · label(대체 텍스트 및 접근성 레이블)
**note**: 현재 페이지의 위치를 알려주고 페이지 이동 등의 기능을 제공해요.
**ex**: `<TopBar> <TopBar.Left> <IconButton> <HomeIcon /> </IconButton> </TopBar.Left> <TopBar.Title>타이틀</TopBar.Title> <TopBar.Right> <IconButton> <SearchIcon /> </IconButton> </TopBar.Right> </TopBar>`

---

### Typography | `import { Typography } from '@atelier/blue' | 몰드: import { Typography } from '@atelier-mold/admin'`
텍스트를 렌더링하는 기본 타이포그래피 컴포넌트입니다.
**props**: as: keyof React.ReactHTML = 'span' — HTML 태그 · maxLines: number = 0 — 최대 줄 수 (0 = 제한 없음) · variant: string = 'body1' — 타이포그래피 스타일 · weight: 'regular' \ = 'medium' \ — 'bold' · color: FgColor \ = 'inherit' \ — 'initial' \
**note**: 단독 텍스트에는 항상 `<Typography>`를 사용해주세요.. `variant`는 기반 스타일 기준일 뿐, 렌더링되는 HTML 태그와는 무관해요.. HTML 태그는 `as` prop을 통해 명시해주세요.. `line-height` 값만큼 높이가 지정되지 않는다면 as 프롭을 블록 레벨 요소로 지정하거나, 스타일에서 직접 `display: inline-block`을 적용해주세요.. 너비와 높이 관련한 스타일은 `<Typography>`에 직접 적용하지 않고, 부모 요소에 적용해주세요.. 구형 브라우저에서 flex-grow가 적용된 아이템에 maxLines이 지정되지 않는다면 `word-break: break-word`을 적용해주세요.
**ex**: `<Typography as="p" variant='body1' color='fg_accent' weight='bold' maxLines={0}> 텍스트 </Typography>`

---

### Uploader
이 컴포넌트는 클레이블루의 Uploader 컴포넌트를 확장한 컴포넌트에요.
**props**: validate: { maxFileSizeFilter?: { value: number; onError?: ((params: { value: number; }) =\> void); }; fileTypeFilter?: { value: string[]; onError?: ((params: { value: string; }) =\> void); } | undefined; dimensionFilter?: { ...; } | undefined; } | undefined — 업로드할 파일의 기본 유효성 검증 규칙 · children: ReactNode — Uploader 내부에 렌더링되는 요소 · id: string — Uploader Input의 고유 아이디 · maxCount(필수): number — 업로드 가능한 최대 파일 수 - layout “column1”일 때는 maxCount가 1로 정해져요. · files(필수): UploaderFile[] — 업로드하는 파일 리스트 · showOrder: boolean = false — Uploader 아이템 왼쪽 상단에 아이템 순서 표시 여부 · draggable: boolean = false — ”Uploader.Preview”의 순서 변경 가능 여부 - true일 때 “Uploader.Preview” 오른쪽 아래에 드래그 핸들이 표시돼요. · onUpload(필수): (acceptedFiles: File[]) =\> Promise\<UploaderFile[]\> — 새롭게 추가된 파일들을 업로드하는 함수 - “input”의 “onChange” 헨들러 내부에서 호출돼요. - 반환하는 값은 “files” 앞쪽에 추가되어 “onUpdateFiles”의 인자로 전달돼요. - 파일 검증 로직은 해당 함수에 포함시켜주세요.   - “undefined”를 반환하면, “onChange” 핸들러는 종료돼요. - “onUpload”에서 “Promise<UploaderFile[]>“를 반환하지 않고 자체적으로 상태를 변경해도 돼요.   - 🚨 단, 가장 최신 “File”을 맨 앞으로 위치시켜주세요. · onUpdate(필수): (newFiles: UploaderFile[]) =\> void — 파일 변경(순서, 삭제, 추가) 되었을때, 호출되는 함수 - 다음의 경우에 호출돼요.  - 드래그를 통한 Uploader.Preview의 순서 변경  - “Uploader.Preview”의 삭제  - “onUpload” 함수의 반환값과 누적된 “File” 리스트를 더해서 files 상태를 업데이트 · secure: boolean = false — ImageViewer를 숨김 및 url 유효성 검사 생략 여부 - 보안상 민감한 파일이 있어 미리보기 화면을 노출시킬 수 없는 경우에 사용해요. - 🚨 “true”일 때 Uploader.Preview을 클릭해도 ImageViewer가 열리지 않아요. - “preventImageViewer”와 달리 이미지 url이 유효하지 않아도 “UploaderFile[‘fileName’]“이 있으면 에러로 표시되지 않고 “UploaderFile[‘fileName’]“으로 파일명이 보여져요. · ratio: FixedThumbnailRatio = 1:1 — Uploader.Preview의 가로세로 비율 - type=‘multiple’이고 Uploader.Preview를 사용할 때만 이용할 수 있어요. · viewerFullscreen: boolean = true — ImageViewer의 fullscreen 여부 · type: "multiple" | "single" = multiple — Uploader.Preview의 레이아웃 타입  - “multiple”일 때는 여러 개의 파일을 볼 수 있어요.  - “single”일 때는 하나의 파일만 볼 수 있어요.    - “single”일 때는 “wrap”과 “columnCount”를 사용할 수 없어요. · wrap: boolean = false — Uploader.Preview 배치 방식 - wrap이 “true”이면 grid 형식으로 배치돼요.   - “columnCount”를 통해 몇 개의 칼럼을 구성할지 결정할 수 있어요. - wrap이 “false”이면 flex 형식으로 배치돼요.   - “columnCount”를 사용할 수 없어요. · columnCount: number — PreviewList의 columns 수 - wrap이 “true”일 때만 사용할 수 있어요. - type이 “multiple”이고 wrap이 “false”일 때는 사용할 수 없어요. - type이 “single”일때 사용할 수 없어요. · disabled: boolean — Uploader를 비활성화할지 여부 - “true”일 때는 파일을 추가할 수 없어요. · width: string | number = 100% — ”Uploader”의 width - 🚨 type이 “single”일 때만 사용할 수 있어요. · height: string | number = 184px — ”Uploader”의 height - 🚨 type이 “single”일 때만 사용할 수 있어요. · preventImageViewerOpen: boolean = false — Uploader의 ImageViewer 숨김 여부 - 아래 상황일 때 사용해요.   - “Uploader”에서 제공하는 기본 “ImageViewer” 동작이 아닌, 다른 UX를 제공하고 싶을 때 사용해요. (e.g. “ImageViewer”를 열었을 때 쿼리파람을 추가)   - secure와 달리, 이미지 url이 잘못된 경우, 에러로 표시해요. - 🚨 “true”일 때 “Uploader.Preview”을 클릭해도 “ImageViewer”가 열리지 않아요. · ref: Ref\<HTMLInputElement\> — Allows getting a ref to the component instance. Once the component unmounts, React will set “ref.current” to “null” (or call the ref with “null” if you passed a callback ref). · showCount: boolean = true — 업로드된 파일 수 표시 여부 - 🚨 “type”이 “single”일 때만 사용할 수 있어요. · onClick: (event: MouseEvent\<HTMLLabelElement, MouseEvent\>) =\> void — Uploader Button을 클릭 시 호출되는 콜백이에요. 내부는 label로 구현되어있기 때문에 클릭하면 기본동작으로 input 창을 열어요. input 창을 열고 싶지 않으면 event.preventDefault를 호출해주세요. · fullWidth: boolean = false — 좌우를 꽉 채우는 버튼 영역에서 드래그 앤 드롭 파일 업로드 기능을 제공할 수 있어요. · guideMessage: string — 업로드관련 가이드 문구 · onKeyUp: KeyboardEventHandler\<HTMLLabelElement\> — 키보드 인터렉션을 통해서 DropDown을 여는 용도로 사용해요. · children: ReactNode — Uploader Button의 아이콘을 변경하고 싶을 때 사용해요. · preventFilePickerOpen: boolean = false — Uploader Button의 기본 동작을 막고 싶을 때 사용해요. - Uploader Button을 클릭해도 파일 선택창이 열리지 않아요. - Uploader Button을 포커스하고 “엔터키”또는 “스페이스바”를 눌러도 파일 선택창이 열리지 않아요. · ref: Ref\<HTMLLabelElement\> — Allows getting a ref to the component instance. Once the component unmounts, React will set “ref.current” to “null” (or call the ref with “null” if you passed a callback ref). · children: ReactNode — 🚨 Badge 컴포넌트만 올 수 있어요. · dimmerText: string — Dimmer 위에 표시하는 텍스트 · file(필수): UploaderFile — 파일이 업로드된 URL · objectFit: "contain" | "cover" = cover — PreviewItem 이미지의 object-fit · isDeleteButtonHidden: boolean = false — 삭제버튼 숨김 여부 · onDelete: (file: UploaderFile) =\> void — Uploader.PreviewItem이 삭제될 때 호출되는 함수 · onBeforeDelete: (file: UploaderFile) =\> Promise\<boolean\> — Uploader.PreviewItem 삭제 전 호출되는 함수 - 반환값에 따라 삭제가 진행되거나 중단될 수 있어요.  - “true”를 반환하면 삭제가 진행돼요.  - “false”를 반환하면 삭제가 중단돼요. · onClick: MouseEventHandler\<HTMLDivElement\> — - · children: ReactNode — - · file(필수): UploaderFile — 파일이 업로드된 URL · onClick: MouseEventHandler\<HTMLDivElement\> — -

---

### AddressSearch
주소 검색을 위한 컴포넌트에요
**props**: open: boolean — 주소 검색 페이지 시트를 열고 닫을 수 있어요. · loading: boolean — 주소 검색 결과를 가져오는 중에 로딩 화면을 보여줄 수 있어요. · children: ReactNode — 주소 검색 결과를 보여줄 수 있어요. “AddressSearch.Item” 컴포넌트를 사용해야 해요.   서브 컴포넌트를 활용해서 커스터마이징할 수 있어요. · searchPlaceholder: string — 주소 검색 입력창에 표시할 placeholder를 설정할 수 있어요. · onSearch: (keyword: string) =\> void — 주소를 검색할 때 호출되는 콜백 함수를 설정할 수 있어요. · onClose: () =\> void — 주소 검색 페이지 시트를 닫을 때 호출되는 콜백 함수를 설정할 수 있어요. · onReset: () =\> void — 주소 검색 결과를 초기화할 때 호출되는 콜백 함수를 설정할 수 있어요. · closeButtonLabel: string — 닫기 버튼 레이블 · onClick: (e: MouseEvent\<Element, MouseEvent\>) =\> void — - · title(필수): string — - · jibun: string — - · road: string — - · noResultText: string — -

---

### BottomActionBar
입력형 페이지에서 작업 버튼들에 쉽게 접근하기 위해 사용해요.
**props**: children(필수): ReactNode — - · children(필수): ReactNode — -

---

### CategoryPicker
카테고리를 선택할 때 사용해요.
**props**: children: ReactNode — - · tab: string — 현재 선택된 탭 지정 (제어 방식으로 사용할 때) · onChangeTab: (tab: string) =\> void — 탭이 변경됨에 따라서 URL 변경하는 함수 · pushRouter: (href: string) =\> void — URL 변경 함수 e.g. …?tab=탭이름 · categories(필수): T[] — 카테고리 목록 · onSearch(필수): (category: T) =\> void — 카테고리 검색 결과 선택시 실행되는 함수 · disabled: boolean — 검색창 비활성화 여부 · options: { nodeOptions?: SearchbarNodeOptions\<T\>; } — 검색 결과 옵션 · inputOptions: Omit\<SearchInputProps, "onChange"\> — 그 외 검색바 인풋 옵션 · tabName: string — - · selectedCategoryId: any — 선택한 카테고리 id. 모듈 렌더링시 해당 id의 카테고리가 선택된 UI로 노출됩니다. · selectedCategory: any — 선택한 카테고리. 모듈 렌더링시 해당 카테고리가 선택된 UI로 노출됩니다. · categoryTree(필수): T[] — InternalCategory 타입으로 decode한 카테고리 트리 · middleNodeSelectable: true — leaf가 아닌 중간 카테고리를 선택할 수 있도록 버튼이 추가됩니다. · disabled: boolean — 카테고리 선택 비활성화 여부 · resetAfterSelect: boolean — 카테고리를 선택한 후에 선택한 카테고리 UI를 리셋합니다. defualt=false · onSelect(필수): (category: T) =\> void — 카테고리 선택시 실행되는 함수 · options: { nodeOptions?: SelectorNodeOptions\<T\>; } — 카테고리 옵션 · itemWidth: string | number — 카테고리 열의 아이템 너비 - “220px” 이상의 값을 설정해주세요. · height: string | number = 366px — 카테고리셀렉터의 높이 · standalone: boolean = false — 단독으로 쓰임 · maxWidth: string | number — 최대 너비 - 좌우 스크롤 필요 시 설정해주세요. · tabName: string — -

---

### CategoryTree
내용이 없습니다.
**props**: categoryTreeRef: ForwardedRef\<CategoryTreeRef\> — - · categories: any — 카테고리 리스트 데이터를 의미합니다. 만약 데이터가 없다면 placeholder를 띄웁니다. · width: number | "${number}px" — 넓이를 의미합니다. 기본값은 464px이에요. · height: number | "${number}px" | "100%" — 높이를 의미합니다. 기본값은 400px이에요. · isLoading: boolean — 데이터를 가져오는 중인지 여부를 의미합니다. 만약 로딩 중이라면 placeholder를 띄웁니다. · draggable: boolean — 드래그를 사용할지 여부를 의미합니다. 기본값은 false입니다. · placeholder: ReactNode — 데이터가 없거나 로딩중일때 표시할 컴포넌트를 의미합니다. · headerOptions: HeaderOptions — 헤더 영역을 컨트롤하기 위한 옵션을 의미합니다. (추가 버튼, 열기/닫기 버튼 제어) · nodeOptions: NodeOptions\<T\> — 노드 영역을 컨트롤하기 위한 옵션을 의미합니다. (노드 추가 및 삭제 제어, 뱃지 추가 등) · selectedNode: any — 선택된 노드를 의미합니다. · searchable: boolean = false — 검색기능을 사용할지 여부를 의미합니다. · onHeightChange: (height: number) =\> void — 높이가 변경됐을 때 호출되는 함수입니다. · onBeforeChange: OnBeforeChangeHandler\<T\> — optimistic update 전에 호출되는 함수입니다. false를 반환하면 optimistic update를 수행하지 않고, onChange를 호출하지 않습니다. 노드의 데이터에 따라 드래깅을 제한하거나, 이전 onChange에서 아직 API 업데이트가 완료되지 않은 경우에 false를 반환하면 됩니다. · onChange: OnChangeHandler\<T\> — 데이터가 변경됐을 때 호출되는 함수입니다. (드래그로 인해 데이터가 변경됐을 때) · onDelete: (selectedNode: T) =\> void — 특정 노드를 삭제했을 때 호출되는 함수입니다. · onSelect: (selectedNode: T) =\> void — 특정 노드를 선택했을 때 호출되는 함수입니다. · onCreate: (selectedNode: T | null) =\> void — 특정 노드에서 자식 노드를 생성하기 버튼을 클릭했을 때 호출되는 함수입니다. · expandAll: boolean — 카테고리 전체열기 여부를 의미합니다.

---

### Dashboard
페이지의 주요 정보를 모아볼 때 사용해요.
**props**: children: ReactNode — - · title(필수): string — - · subTitle: string — - · children(필수): ReactNode — - · children(필수): ReactNode — - · label(필수): string — - · tooltipTitle: string — - · tooltipContent: ReactNode — - · isSelected: boolean — - · children(필수): ReactNode — -

---

### DataView
Data를 보여줄 때 사용하는 컴포넌트에요
**props**: vertical: boolean — - · wide: boolean — - · children: ReactNode — - · children(필수): ReactNode — - · tooltip: Omit\<TooltipProps, "children"\> — - · small: boolean — - · children(필수): ReactNode — - · children(필수): ReactNode — -

---

### FormCoat
본 가이드는 react-hook-form의 기본적인 사용법에 대한 이해를 전제로 작성되었으니 참고해주세요.
**props**: children(필수): (props: { ref: RefCallBack; value?: PathValue\<TFieldValues, TName\>; errorMessage?: string | undefined; onChange: (value?: PathValue\<TFieldValues, TName\> | undefined) =\> void; onBlur?: (() =\> void) | undefined; extras: UseControllerReturn\<...\>; }) =\> ReactElement\<...\> — - · control(필수): Control\<TFieldValues, any\> — react-hook-form 참고 · name(필수): string — react-hook-form 참고 · rules: Omit\<RegisterOptions\<TFieldValues, TName\>, "valueAsNumber" | "valueAsDate" | "setValueAs" | "disabled"\> — react-hook-form 참고 · shouldUnregister: boolean — react-hook-form 참고 · defaultValue: any — react-hook-form 참고 · disabled: boolean — react-hook-form 참고 · shouldUseControllerValue: boolean — -

---

### GNB
좌측 사이드바를 구성하는 컴포넌트입니다.
**props**: open: boolean — GNB가 열려 있는지 여부를 나타냅니다. · searchable: boolean — GNB가 검색 가능한지 여부를 나타냅니다. 활성화된 경우 GNB 최상단에 검색 인풋이 위치합니다. 검색 시 키워드에 필터링된 메뉴만 나타납니다. · menus(필수): GNBMenuType[] — GNB의 메뉴 항목 목록입니다.

---

### AccordionCardHeader
Card에서 접기 / 펼치기 필요할 때 사용해요
**props**: open: boolean — 헤더 접기 / 펼치기 여부  - true인 경우 펼치기, false인 경우 접기를 의미해요 · onOpen: (open: boolean) =\> void — 헤더 접기 / 펼치기 이벤트  - 함수의 파라미터로 open 여부를 받아요. · title(필수): string — 헤더 제목  - 제목을 입력할 때 사용해요. · subTitle: string — 헤더 보조 제목  - 보조 제목을 입력할 때 사용해요. · caption: ReactNode — 헤더 오른쪽 영역  - 오른쪽 부분을 입력할 때 사용해요.

---

### EditableEditCardHeader
Card에서 수정 중인 헤더가 필요할 때 사용해요.
**props**: title(필수): string — 헤더 제목  - 제목을 입력할 때 사용해요. · subTitle: string — 헤더 보조 제목  - 보조 제목을 입력할 때 사용해요. · caption: string — 헤더 오른쪽 영역  - 오른쪽 부분을 입력할 때 사용해요. · disabled: boolean — 헤더 저장 버튼의 disabled 여부를 의미해요. · onCancel: () =\> void — 헤더 취소 버튼 클릭 시 이벤트  - 취소 버튼을 클릭했을 때 사용해요. · cancelText: string — 취소 버튼 텍스트 · saveText: string — 확인 버튼 텍스트 · saveType: "button" | "submit" — 저장 버튼의 타입 결정  - 저장 버튼 타입을 결정할 때 사용해요. - Form 태그와 함께 사용할 때 유용해요. · onSave: () =\> void — -

---

### EditableViewCardHeader
Card에서 수정 버튼을 이용해서 수정 가능한 헤더가 필요할 때 사용해요
**props**: title(필수): string — 헤더 제목  - 제목을 입력할 때 사용해요. · subTitle: string — 헤더 보조 제목  - 보조 제목을 입력할 때 사용해요. · caption: string — 헤더 오른쪽 영역  - 오른쪽 부분을 입력할 때 사용해요. · onEdit: () =\> void — 헤더 수정 버튼 클릭 시 이벤트  - 수정 버튼을 클릭했을 때 사용해요. · editText: string — 수정 버튼 텍스트

---

### SimpleCardHeader
간단한 CardHeader가 필요할 때 사용해요.
**props**: title(필수): string — 헤더 제목  - 제목을 입력할 때 사용해요. · subTitle: string — 헤더 보조 제목  - 보조 제목을 입력할 때 사용해요. · caption: string — 헤더 오른쪽 영역  - 오른쪽 부분을 입력할 때 사용해요. · required: boolean — 필수 표시  - 카드 헤더에 필수 표시를 할 때 사용해요.

---

### TableHeader
내용이 없습니다.
**props**: children(필수): ReactNode — - · title(필수): string — - · children: ReactNode — - · children(필수): ReactNode — - · children: string | (string | number)[] — 접두사, 접미사를 포함한 전체 문구 · selectedCount(필수): number — - · totalCount(필수): number — - · size(필수): number — - · onSizeChange(필수): (size: number) =\> void — - · sizeList: number[] — - · children(필수): ReactNode — -

---

### Layout
기본 글로벌 레이아웃을 정의할 때 사용해요
**props**: children(필수): ReactNode — - · gnbControl: { isGnbOpen: boolean; setIsGnbOpen: (active: boolean) =\> void; } — - · children(필수): ReactElement\<any, string | JSXElementConstructor\<any\>\> — - · children(필수): ReactElement\<any, string | JSXElementConstructor\<any\>\> — -

---

### MultiPicker
Tree 데이터를 다중 선택할 때 사용해요
**props**: data(필수): T[] | Node — 노드 데이터 · selectedNodes(필수): T[] — 선택된 노드 목록 · width: string — 컴포넌트의 너비 · height: string — 컴포넌트의 높이 · ellipsis: boolean — 노드 라벨이 길 경우 말줄임 처리 여부 · exact: boolean — 직접 선택된 노드만 표시할지 여부 · listTitle: string — 입력 탭의 노드 목록 제목 · selectLabel: string — 선택 탭의 라벨 · textareaLabel: string — 입력 탭의 라벨 · applyLabel: string — textarea의 적용 버튼 라벨 · onSelect: (nodes: T[], add?: T, sub?: T) =\> void — 선택 탭에서 노드를 선택하거나 해제할 때 호출되는 콜백 함수 · onApply: (nodes: T[], adds: T[], value: string) =\> void — 입력 탭에서 값을 적용할 때 호출되는 콜백 함수

---

### RequiredMark
Required 아이콘이 단독으로 필요할 때 사용해요

---

### SearchFilter
검색 조건을 입력하여 데이터를 조회할 때 사용해요.
**props**: onSubmit: FormEventHandler\<HTMLFormElement\> — - · children(필수): ReactNode — - · collapsible: boolean = false — 검색 필터 열고/닫기 기능 사용 여부를 결정합니다 · simple: boolean = false — 심플 레이아웃 사용 여부를 결정합니다 · children(필수): ReactNode — - · children(필수): ReactNode — - · fieldGap: "none" | "px" | "25" | "50" | "75" | "100" | "125" | "150" | "200" | "250" | "300" | "400" | "500" | "600" | "700" | "800" | "900" | "1000" | "1100" | "1200" | "1300" | "1400" | "1500" = 200 — 하위 Form.Field 사이 간격  - 스페이싱 토큰을 지원해요. - Form.Field가 아닌 Form 하위 요소의 간격은 Container, Flex 등을 활용해 직접 스타일링해야 해요. · vertical: boolean = false — 레이블과 컨트롤/메시지의 배치 방향  - Form 또는 Form.Field에서 지원돼요. - Form.Field 전달되는 값이 더 높은 우선순위를 가져요. · wide: boolean = false — 레이블 너비  - 뷰포트 너비가 넓은 환경에 사용해요. - Form 또는 Form.Field에서 지원돼요. - Form.Field 전달되는 값이 더 높은 우선순위를 가져요. - 🚨 vertical prop이 “false”일 때만 반영돼요. · children: ReactNode — - · validateOn: ValidateOn = submit — 폼 검증 시점  - 아래 값 중 하나를 지원해요.   - submit: 폼 제출 시   - blur: 포커스 해제 시   - change: 값 변경 시   - off: 검증 비활성화 - blur는 submit을 포함하고, change는 blur와 submit을 포함해요. · pin: boolean — 검색 필터를 접었을 때, 필드 고정 노출 여부를 결정합니다. SearchFilter 컴포넌트의 collapsible이 true일 때만 동작합니다. · required: boolean — - · width: string | number — - · height: string | number — - · children(필수): ReactElement\<any, string | JSXElementConstructor\<any\>\> — -

---

### SelectWithSearch
Custom Select와 클레이블루 SearchInput을 조합한 컴포넌트에요
**props**: width: 180 | 328 | 600 | "180px" | "328px" | "600px" | "100%" = 100% — 너비 · fetchNextPage: () =\> void — - · hasNextPage: boolean — 무한스크롤이 가능한지 여부를 지정해요. · multiple: boolean = false — 옵션 여러개 선택 다중 선택 가능 여부  - 활성화되면 옵션을 선택해도 드롭다운이 닫히지 않아요. 백드롭 영역을 눌러 닫을 수 있어요. - 🚨 native에서는 지원되지 않아요. · value: string | string[] — 옵션값 (제어) - “multiple”이 false이고, 선택 중인 값이 없다면 빈 문자열을 전달해주세요. - “multiple”이 true이고, 선택 중인 값이 없다면 빈 배열을 전달해주세요. · defaultValue: string | string[] — 옵션값 (비제어) · showCount: boolean = false — 다중 선택 시 ‘외 n건’ 레이블 제공 여부 · maxSelectionCount: number = Infinity — 최대 선택 가능한 옵션 개수 - multiple이 true일 때 사용가능 선택 가능한 최대 옵션 수 · onChange: (event: ChangeEvent\<HTMLSelectElement\>, value: string | string[]) =\> void — 선택 옵션 변경 시 호출되는 이벤트 핸들러 · small: boolean = false — 트리거 UI 높이를 작게 표현할지 여부 - “false”: 48px - “true”: 40px · invalid: boolean — 유효성 검증 통과 여부  - true인 경우 유효성 검증에 실패한 상태로 취급돼요. - 서버 응답(비동기)에 따른 유효성 처리가 필요하거나 ref에 접근할 수 없는 경우 활용해주세요. · native: false — - · placeholder: string — 드롭다운 방식(“native”가 false인 경우)에서 제공할 플레이스홀더  - 플레이스홀더는 옵션 목록으로 제공되지 않아요. · enableVirtualFocus: boolean = false — 드롭다운 옵션 목록을 가상 포커스로 제어할지 여부 · virtualFocusKey: string = &#x27;&#x27; — Option의 가상 포커스를 초기화 시키기 위한 키 - “enableVirtualFocus”가 “true”일 때만 동작해요. - 값이 달라질때마다 가상 포커스를 첫 아이템으로 초기화 시켜요. - Option들이 동적으로 추가되거나 사라지는 경우(검색 필터링)에 사용해요. · fitToViewport: boolean — - · searchValue(필수): string — 검색어 · onChangeSearch(필수): (nextValue: string) =\> void — 검색어 변경 이벤트 핸들러 · searchPlaceholder: string — 검색어 placeholder · fixedSearchArea: boolean — 검색바 영역을 고정시킬지 여부 · ref: Ref\<HTMLSelectElement\> — Allows getting a ref to the component instance. Once the component unmounts, React will set “ref.current” to “null” (or call the ref with “null” if you passed a callback ref).

---

### 개발 시작하기
몰드어드민은 아래의 peer-dependency를 포함합니다.
**의존성 개요**: 몰드어드민은 아래의 peer-dependency를 포함합니다. · `react@18` · `react-dom@18` · `react-hook-form@^7.46.2` · - FormCoat, Form presets 등 강화된 Form 기능을 사용하기 위해서는 이 의존성을 추가해주셔야 합니다. · 몰드어드민은 다음의 의존성을 포함하니 참고해주세요. · `@atelier/blue@^1.37.0` · - 1.37.0 버전까지 우아한공방 블루의 정상 적용이 확인되었습니다.
**설치하기**: 프로젝트 루트 디렉토리의 `.npmrc` 파일에 아래 사내 레지스트리 설정이 추가되어 있어야 합니다.
`pnpm add @atelier-mold/admin`
**사용하기**: 프로젝트 내에서 모든 몰드어드민 컴포넌트를 포함하는 적절한 위치에서 AtelierRoot Provider 컴포넌트를 추가해주세요. · 그리고 기본 css 스타일을 적용하기 위해 `@atelier-mold/admin/style.css`를 import 해주세요.
`<AtelierRoot> {children} </AtelierRoot>`
**가이드 읽기 전, 알아두면 좋은 점**: 몰드어드민은 우아한공방 블루 컴포넌트를 re-export 하고 있어요. — **Blue** 문서에서 현재 re-export하고 있는 우아한공방 블루 컴포넌트의 목록을 확인하실 수 있어요. · 몰드어드민은 일부 우아한공방 블루 컴포넌트를 재정의하고 있어요. — **Blue Customs** 문서에서 재정의된 우아한공방 블루 컴포넌트의 설명을 확인하실 수 있어요. · 몰드어드민은 우아한공방 블루 컴포넌트와 토큰을 기반으로 확장 컴포넌트를 제공하고 있어요. — **Extension** 문서에서 확장 컴포넌트들의 설명을 확인하실 수 있어요. · 블루어드민 (`@atelier/blue-admin`)에서 몰드어드민 (@atelier-mold/admin)으로 마이그레이션 하시는 경우, **마이그레이션 가이드**의 내용을 참고해주세요. · 본 가이드 사이트 내 상단바의 우측에 위치한 링크를 통해 몰드어드민의 소스코드 / 피그마 / 스토리북를 확인하실 수 있어요. · 본 가이드 사이트 내 상단바의 최우측에 위치한 `</>` 버튼을 통해 우아한플레이그라운드의 에디터 기본 활성여부를 전환하실 수 있어요.
**체험**: [우아한플레이그라운드](https://playground.betawoowa.in)를 통해 몰드어드민을 체험해보실 수 있어요. · Last updated on August 28, 2025
**ex**: `프로젝트 루트 디렉토리의 `.npmrc` 파일에 아래 사내 레지스트리 설정이 추가되어 있어야 합니다.`

---

### toFormArrayNumber
숫자 배열의 데이터를 Form에서 사용할 때 유용한 변환 함수입니다.
**props**: params 명: 타입 = 기본값 — 설명 · value: Nullable<string> | undefined — 입력값 · onChange: onChange(value?: number[]) => void — 최종적으로 호출될 이벤트 핸들러 · type: &#x27;float&#x27; | &#x27;integer&#x27; = integer — 값의 유형 · delimiter: string | undefined = ’,” — 배열 요소 구분자  기본 = ’,‘ · maxLength: number | undefined = 배열 최대 길이 · fractions: number | undefined — 소수점 자릿수 제한 (type이 float일 때만 사용할 수 있어요) · round: number | undefined — 소수점 반올림 (type이 float일 때만 사용할 수 있어요) · itemProps: { min?: number; max?: number } | undefined = 배열 내 요소에 제약할 사항들 · value: Nullable<string> = 변환된 값 · onChange: (value?: string) => void = 변환 로직이 포함된 이벤트 핸들러

---

### toFormArrayString
문자열들의 배열 꼴 데이터를 Form에서 활용할 떄 도움을 주는 변환 함수입니다.
**props**: value: string[] | null | undefined = 입력값 · onChange: onChange(v?: string[]) => void = 최종적으로 호출될 이벤트 핸들러 · type: StringFormatType (= \&#x27;string\&#x27; | \&#x27;noEmoji\&#x27; | \&#x27;noSpecialChar\&#x27; | \&#x27;noSpace\&#x27; | \&#x27;hangul\&#x27; | \&#x27;email\&#x27; | \&#x27;alphaNumeric\&#x27; | \&#x27;alphaNumericHangul\&#x27;) | undefined = 문자열 포맷팅 종류 기본 = ‘string’ · delimiter: string | undefined = 배열 요소 구분자  기본 = ’,‘ · maxLength: number | undefined = 배열 최대 길이 · itemProps: { maxLength?: number } | undefined = 각 요소에 전달할 속성 · value: string[] | undefined | null = 변환된 값 · onChange: onChange(value?: string) => void = 변환 로직이 포함된 이벤트 핸들러

---

### toFormNumber
숫자 데이터를 Form에서 사용할 때 유용한 변환 함수입니다.
**props**: params 명: 타입 = 기본값 — 설명 · value: number | undefined — 입력값 · onChange: onChange(v?: number) => void — 최종적으로 호출될 이벤트 핸들러 · type: &#x27;float&#x27; | &#x27;integer&#x27; | ‘monetary’ — 값의 유형 · round: number | undefined — 소수점 반올림 (type이 float일 때만 사용할 수 있어요)

---

### toFormString
문자열 데이터를 Form에서 처리할 때 사용하는 유틸리티 함수입니다.
**props**: params 명: 타입 = 기본값 — 설명 · value: string | undefined — 입력값 · onChange: (e: string | undefined) => void — 변환된 문자열을 처리하는 콜백 함수 · type: StringFormatType = ’string’ — 문자열 포맷팅 타입 · maxLength: number | undefined — 최대 문자열 길이 (유니코드 문자 기준) · value: string | undefined = 포맷팅된 문자열 값 · onChange: (e: string | undefined) => void = 포맷팅 로직이 포함된 이벤트 핸들러 · type: 설명 · string: 기본 문자열 처리 · noEmoji: 이모지 제외 · noSpecialChar: 특수문자 제외 · noSpace: 공백 제외 · hangul: 한글만 허용 · email: 이메일 형식 · alphaNumeric: 영문과 숫자만 · alphaNumericHangul: 영문, 숫자, 한글만

---

### useAlert
useSimpleAlert
**props**: alert: (alertMeta: AlertInput) => Promise<boolean> | void = alert 호출 함수 · confirm: (confirmMeta: ConfirmInput) => Promise<boolean> | void = confirm 호출 함수 · close: () => void = alert 및 confirm 닫기 함수 · params 명: 타입 = 기본값 — 설명 · title: string — 알림 다이얼로그의 제목 · description: string | AlertDescriptionFn — 알림 다이얼로그의 내용 · color: primary | primaryDanger = primary — 알림 다이얼로그에서 확인 버튼의 색상 · closeText: string = 확인 — 확인 버튼 문구 텍스트 · onSuccess: () => void — 확인(닫기) 시 호출되는 콜백 · Promise<boolean>: Promise<boolean> = 확인 버튼 클릭 시 false 반환 · params 명: 타입 = 기본값 — 설명 · title: string — 알림 다이얼로그의 제목 · description: string | AlertDescriptionFn — 알림 다이얼로그의 내용 · color: primary | primaryDanger = primary — 알림 다이얼로그에서 확인 버튼의 색상 · closeText: string = 취소 — 닫기 버튼 문구 텍스트 · confirmText: string = 확인 — 확인 버튼 문구 텍스트 · onSuccess: () => void — 확인(닫기) 시 호출되는 콜백 · Promise<boolean>: Promise<boolean> = 확인 버튼 클릭 시 true, 닫기 버튼 클릭 시 false 반환 · void: void = 현재 열려있는 가장 마지막 다이얼로그를 닫음

---

### 소개
- Wiki) [몰드]어드민가이드 사용 온보딩
**💡 사용방법**: Wiki) [몰드]어드민가이드 사용 온보딩
**💡 문의사항**: Slack) #support-몰드-어드민가이드
**💡 연관링크**: 🌏 Web - [몰드]어드민가이드: 어드민 가이드를 간편하게 웹페이지에서 확인할 수 있어요. (현재 페이지) · 🎨 Figma - [몰드]어드민가이드: 어드민 가이드를 확인하고 예시들을 사용해 볼 수 있어요. · 🧩 Storybook) [몰드]어드민가이드: Web으로 구현된 어드민용 컴포넌트들을 볼 수 있어요.
**1. [몰드]어드민 가이드는 무엇인가요?**: 운영을 위해 어드민은 항상 필요하기 마련인데, 매번 반복적인 논의와 비용을 들여 제작하고 있어요. · 어드민 가이드는 이러한 어드민 제작시 발생하는 기획/디자인/개발의 비용을 줄이기 위해 만들어졌어요. · 어드민에서 자주 사용 되는 패턴을 모아 재사용할 수 있고 안정성과 통일된 사용성까지 더해 효율적으로 활용할 수 있는 어드민가이드를 사용해 보세요! · 더 자세한 안내와 설명은 온보딩 문서에서 확인해주세요! (목적 및 배경, 구조, 자주 묻는 질문 등) · 🔗 Wiki) [몰드]어드민가이드 사용 온보딩
**2. [몰드]어드민 가이드를 이렇게 활용해 보세요!**: 기획에 어드민가이드를 활용할 수 있는 방법이에요. · 개발 요청 시 어드민가이드를 활용해 어드민 화면 기획을 설명할 수 있어요. 기획 의도를 전달하기 위함이니 간격, 사이즈 등이 완벽하지 않아도 괜찮아요! · (어드민가이드를 활용해서 설명했다면 개발자분들이 잘 해석해 주실 거예요👍)
**a. 예시 화면 활용하기**: 직접 피그마를 사용하지 않아도 디자인가이드 예시를 사용(캡쳐 등)하여 기획에 맞는 내용을 구성할 수 있어요. · 디자인가이드를 활용해 구축된 실제 어드민 화면을 가지고 설명해도 좋아요!
**b. 피그마 활용하기**: 직접 피그마를 사용하지 않아도 디자인가이드 예시를 사용(캡쳐 등)하여 기획에 맞는 내용을 구성할 수 있어요. · 디자인가이드를 활용해 구축된 실제 어드민 화면을 가지고 설명해도 좋아요!
**c. 와이어프레임 활용하기**: 직접 피그마를 사용하지 않아도 디자인가이드 예시를 사용(캡쳐 등)하여 기획에 맞는 내용을 구성할 수 있어요. · 디자인가이드를 활용해 구축된 실제 어드민 화면을 가지고 설명해도 좋아요!
**3. 궁금한 점이 있다면? 서포트 채널로 오세요!**: 몰드-어드민가이드 서포트채널로 오세요! 모든 문의, 제안, 이야기들을 환영합니다~! · Last updated on August 28, 2025

---

### BottomActionBarGuide
마이그레이션 가이드BottomActionBar 변경사항

---

### FormCoatGuide
마이그레이션 가이드Form 프리셋 👉 FormCoat
**props**: values: values.map((v) => ({ label: v.toString(), value:: v })), · values: values.map((v) => ({ label: v.toString(), value:: v })),

---

### GnbGuide
마이그레이션 가이드GNB 변경사항

---

### LayoutGuide
마이그레이션 가이드Layout 변경사항

---

### V2Guide
마이그레이션 가이드v1 -> v2

---

### Blue
아래 목록은 현재 몰드어드민에서 re-export 하고 있는 **우아한공방 clayblue** 모듈들입니다.
**Re-export 목록**: AtelierRoot · Accordion · AssistiveText · Badge: Badge, NotificationBadge · Banner · Bar: TopBar, BottomBar · Breadcrumb · Button: Button, IconButton, TextButton
