# Component Specification: InputField & InputField Items

Figma Component Set 메타데이터 및 Claude Design-to-Code 파이프라인 연동을 위한 UI 컴포넌트 상세 명세서입니다.

---

## 1. Figma Metadata

- **Component Set Name**: `Form / InputField` (Items: `InputField.Item`)
- **Figma Layer Architecture**: 
  - `InputField` (Root Frame: Vertical Auto Layout / Width: 350px, Gap: 8px)
  - `InputField.Item` (Input Control Base: Horizontal/Vertical Auto Layout / Min-Height: 56px)
- **Design System Domain**: Banking / Financial Services Framework (KBFG System)
- **Default Frame Setup**: Fixed Width (`350px`), Height `Hug Contents` (Textarea 등 일부 제외)

---

## 2. Component Hierarchy

### 2.1 Complete Form Field Structure (InputField Root)
```text
InputField (Container: Width 350px, Column, Gap 8px)
├── Header Area (data-required="true", data-tooltip="true", Gap 8px)
│   └── Title Row (Flex Row, Gap 2px, Align Center)
│       ├── Label Text ("타이틀입니다", 14px/20px, Bold 700)
│       ├── Required Indicator ("(필수)", 11px/15px, Red 500)
│       └── Tooltip Action Button (16x16px, Secondary, Radius 4px)
│           └── Suffix Icon Viewport (16x16px, Inner Vector 12x12px)
├── Control Area: InputField.Item (Min-Height 56px, Radius 12px, Data States)
│   ├── Prefix Slot (Segmented Control / Action / None)
│   ├── Content Core (Flex 1 1 0, Text Node, Caret Cursor Indicator 1.6x22px)
│   └── Suffix Slot (Delete Button / Action Button / Unit Text / Caret Icon / Timer)
└── Footer Area (Column, Gap 2px or 10px)
    ├── [Optional] Error Message Row (Icon 12x12px + Error Text 13px/18px, Gap 1px)
    └── [Optional] Helper Caption Row (data-variant="single", Padding H 6px, Text 13px/18px)
```

### 2.2 Input Control Unit (`InputField.Item` Variations)
```text
InputField.Item (Control Base: Min-Height 56px, Radius 12px)
├── [Case A: Basic Input]
│   ├── Content (Flex 1 1 0, 16px/22px Text, Caret 1.6x22px)
│   └── Clear Action (data-variant="secondary", 24x24px, Icon 18x18px)
├── [Case B: Unit Text (금액/기간)]
│   ├── Value Text Area (Align Right, 16px/22px)
│   └── Unit Label ("원" / "월", 16px/22px, Bold 700)
├── [Case C: Account Dropdown]
│   ├── Left Column (Bank CI Badge 20x20px + Sub Label 15px + Main Text 16px + Helper 12px)
│   └── Right Caret Icon (24x24px Viewport, Rotated -90deg Vector 7.29x13.5px)
├── [Case D: Segmented Prefix/Suffix]
│   ├── Segment Container (Background #F4F6F9, Radius 10px, Padding 4px, Gap 2px)
│   │   ├── Active Segment (White Fill, Shadow, Radius 6px, Min-Width 26px, Text 12px Bold)
│   │   └── Inactive Segment (Shadow, Radius 6px, Min-Width 26px, Text 12px Medium)
│   └── Text Node Area
├── [Case E: Button / ButtonWithTimer Suffix]
│   ├── [Optional] Timer Display ("3:00", 15px/21px, Positive Blue)
│   └── Action Button (Min-Height 32px, Radius 8px, Padding H 8px V 2px, Text 12px Bold)
├── [Case F: Multi-Column / Complex Layout]
│   ├── Range Control (Input Item + "~" Delimiter 17px/24px Bold + Input Item)
│   ├── Email Row (ID Item + "@" Delimiter 17px/24px Bold + Domain Item + Direct Input)
│   ├── Tel / Account Number Block (Item + "-" + Item + "-" + Item, Inner Gap 4px)
│   └── Preset Amount Chips (4-Column Equal Grid, Min-Height 32px, Radius 9999px)
└── [Case G: Multi-line Textarea]
    └── Expandable Box (Height 140px, Padding H 16px V 12px, Text 16px Regular 300)
```

---

## 3. Properties & Variants

### 3.1 Field Container & Control Attributes (`data-*`)

| Component Scope | Attribute | Type | Default Value | Value Range | Description |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **InputField Root** | `data-required` | Boolean | `true` | `true`, `false` | 필수 입력 항목 `(필수)` 표기 여부 |
| | `data-tooltip` | Boolean | `true` | `true`, `false` | 도움말 툴팁 아이콘 노출 제어 |
| | `data-hassuffix` | Boolean | `false` | `true`, `false` | 헤더 영역 보조 컨트롤 여부 |
| | `data-emailfiled2_show` | Boolean | `true` | `true`, `false` | 복합 이메일 도메인 필드 노출 제어 |
| | `data-hasquickbutton` | Boolean | `true` | `true`, `false` | 금액 빠른 선택 칩 버튼 활성화 플래그 |
| **InputField.Item** | `data-variant` | String | `basic` | `basic`, `column`, `account`, `textarea`, `basic-unittext` | 입력 필드 시각/기능 템플릿 구조 |
| | `data-disabled` | Boolean | `false` | `true`, `false` | 비활성화 상태 (Opacity 0.50, 음영 채움) |
| | `data-focused` | Boolean | `false` | `true`, `false` | 포커스 및 캐럿 커서 활성화 상태 |
| | `data-entered` | Boolean | `false` | `true`, `false` | 값 입력 완료 상태 (폰트 가중치 변경) |
| | `data-error` | Boolean | `false` | `true`, `false` | 검증 실패 상태 (Border Red 2px 아웃라인) |
| | `data-haslogo` | Boolean | `true` | `true`, `false` | 계좌/기관 CI 엠블럼 표시 |
| | `data-prefix` | Boolean | `false` | `true`, `false` | 좌측 프리픽스 컨트롤 노출 여부 |
| | `data-suffix` | Boolean | `false` | `true`, `false` | 우측 액션/아이콘 컨트롤 노출 여부 |
| | `data-textdel` | Boolean | `true` | `true`, `false` | 입력 텍스트 일괄 삭제(Clear) 버튼 사용 여부 |
| **Sub-Controls** | `data-variant` (Suffix) | String | - | `icon`, `button`, `buttonWithTimer`, `segmentedControl` | 우측 애드온 컨트롤 변형값 |
| | `data-selected` | Boolean | `false` | `true`, `false` | 세그먼트 버튼 선택 활성화 여부 |

---

## 4. Detailed Layout Specifications

### 4.1 Root Container & Header/Footer Metrics

- **Field Total Width**: Fixed `350px`
- **Field Gap**: `8px` (Vertical Column Layout)
- **Header Structure**:
  - Min-Height: `20px`
  - Gap: `8px`
  - Title Text: Font `'KBFG Text'`, Size `14px`, Weight `700`, Line-height `20px`
  - Required Tag: Font `'KBFG Text'`, Size `11px`, Weight `500`, Line-height `15px`
  - Tooltip Button: Hit-area `16x16px`, Radius `4px`, Inner Vector Inset `top 2px, left 2px`, Size `12x12px`
- **Footer Structure**:
  - Gap: `2px` (Error + Helper 간) 또는 `10px` (Helper 단독)
  - Horizontal Padding: `6px`
  - Error Text: Font `'KBFG Text'`, Size `13px`, Weight `500`, Line-height `18px`
  - Error Icon: Viewport `12x12px`, Vector `9x9px` (Inset Top `1.50px`, Left `1.50px`)
  - Helper Caption: Font `'KBFG Text'`, Size `13px`, Weight `500`, Line-height `18px`

### 4.2 Control Box Dimensions & Inset Paddings

| Variant Type | Min-Height / Height | Padding Inset | Border Radius | Internal Gap |
| :--- | :--- | :--- | :--- | :--- |
| **Basic (Default)** | Min `56px` | Top `16px`, Bottom `16px`, Left `16px`, Right `16px` | `12px` | `8px` |
| **Basic (Action Suffix)** | Min `56px` | Top `8px`, Bottom `8px`, Left `16px`, Right `12px` | `12px` | `8px` |
| **Segment Attached** | Min `56px` | Top `8px`, Bottom `8px`, Left `16px`, Right `16px` | `12px` | `8px` |
| **Column Splitted** | Min `56px` | Top `16px`, Bottom `16px`, Left `8px`, Right `8px` | `12px` | `8px` |
| **Textarea** | Fixed `164px` (Inner 140px) | Top `12px`, Bottom `12px`, Left `16px`, Right `16px` | `12px` | - |

### 4.3 Sub-Elements Layout & Typography Specifications

#### A. Input Core & Blinking Caret Indicator
- **Text Layer**:
  - Font Family: `'KBFG Text', -apple-system, sans-serif`
  - Font Size: `16px`
  - Line Height: `22px`
  - Font Weight: Placeholder / Empty 상태 시 `500` (Medium), Textarea `300` (Light), Entered 상태 시 `700` (Bold)
- **Caret Bar (Focused State)**:
  - Width: `1.60px`
  - Height: `22px`
  - Background: `var(--icon-accent-brand-alt, #111827)`
  - Gap from text: `1px`

#### B. Suffix Clear Action Button (`data-size="24"`, `secondary`)
- Hit Target Box: `24x24px`
- Border Radius: `4px`
- Vector Area: Width `18px`, Height `18px`, Inset Top `3px`, Left `3px`
- Vector Fill: `var(--icon-neutral-quaternary, #9CA3AF)`

#### C. Segmented Switcher (`data-variant="segmentedControl"`)
- Track Base: Background `#F4F6F9`, Radius `10px`, Padding `4px`, Gap `2px`
- Segment Item:
  - Min-Width: `26px`, Padding `4px`
  - Border Radius: `6px`
  - Active: Background `#FFFFFF`, Box-Shadow `0px 2px 4px -1px rgba(12, 17, 29, 0.10)`
  - Inactive: Background `transparent`, Box-Shadow `0px 4px 6px rgba(12, 17, 29, 0.10)`
  - Label Typography: Font Size `12px`, Line Height `17px`, Active Weight `700`, Inactive Weight `500`

#### D. Quick Preset Chips (`data-variant="tertiary"`)
- Layout: 4-Column Equal Flex (`flex: 1 1 0`), Total Container Gap `4px`
- Dimensions: Min-Height `32px`, Radius `9999px` (Pill), Padding Top/Bottom `2px`, Left/Right `8px`
- Outline: `1px solid var(--border-neutral-primary-muted, #D1D5DB)` (Offset `-1px`)
- Typography: Font Size `12px`, Line Height `17px`, Font Weight `700`, Align Center

---

## 5. Token Mapping Matrix

| Component State | CSS Token Variable | Fallback HEX / RGBA | Target Applied Layer | CSS Property |
| :--- | :--- | :--- | :--- | :--- |
| **Field Wrapper Border** | `var(--color-util-purple, #893DE7)` | `#893DE7` | Master Canvas Guide Frame | `border-color` |
| **Default Border** | `var(--border-neutral-primary-muted, #D1D5DB)` | `#D1D5DB` | Input Item Frame Outline | `outline-color: 1px` |
| **Focused Caret** | `var(--icon-accent-brand-alt, #111827)` | `#111827` | Caret Vertical Bar | `background` |
| **Error Border** | `var(--border-status-negative, #E53838)` | `#E53838` | Input Item Frame Outline | `outline-color: 2px` |
| **Error Icon & Text** | `var(--icon-status-negative, #E53838)`<br>`var(--text-status-negative, #E53838)` | `#E53838` | Error Viewport Vector<br>Error Text Label | `background`<br>`color` |
| **Required Label** | `var(--text-accent-red, #E53838)` | `#E53838` | Header `(필수)` Text | `color` |
| **Disabled Surface** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `rgba(102, 112, 133, 0.10)` | Disabled Input Item Frame | `background-color` |
| **Disabled Text** | `var(--text-neutral-disabled, #9CA3AF)` | `#9CA3AF` | Disabled Action / Chip Text | `color` |
| **Text Primary** | `var(--text-neutral-primary, #111827)` | `#111827` | Title / Entered Text / Delimiters | `color` |
| **Text Placeholder** | `var(--text-neutral-placeholder, #9CA3AF)` | `#9CA3AF` | Unfilled Input Text / Unit Label | `color` |
| **Text Helper/Caption** | `var(--text-neutral-quaternary, #6B7280)` | `#6B7280` | Bottom Helper Label / Delimiters | `color` |
| **Timer Text** | `var(--text-status-positive, #1F6AFF)` | `#1F6AFF` | Timer Countdown ("3:00") | `color` |
| **Icon Standard Fill** | `var(--icon-neutral-primary, #111827)` | `#111827` | Arrow / Suffix Action Vector | `background` |
| **Icon Muted Fill** | `var(--icon-neutral-quaternary, #9CA3AF)` | `#9CA3AF` | Tooltip / Clear Button Vector | `background` |

---

## 6. Implementation Guidelines

### 6.1 State Switching & Outline Rendering Rules
- **Error vs Default Outline**: 
  - 기본 상태는 `outline: 1px solid var(--border-neutral-primary-muted)` 및 `outline-offset: -1px`를 사용합니다.
  - `data-error="true"` 상태로 변경 시 테두리가 두꺼워지면서 레이아웃이 밀리는 것을 방지하기 위해 `outline: 2px solid var(--border-status-negative)` 및 `outline-offset: -2px` 규칙을 반드시 유지해야 합니다.
- **Disabled State Handling**:
  - `data-disabled="true"`인 경우 배경색을 `var(--surface-neutral-disabled)`로 채우고, 미입력 상태(`data-entered="false"`)일 때는 전체 레이어 투명도를 `opacity: 0.50`으로 강제 처리합니다. 단, 이미 입력된 텍스트(`data-entered="true"`)가 있는 상태에서 비활성화된 경우 투명도 오버라이드 없이 고대비 텍스트 색상을 보존합니다.

### 6.2 Complex Inline Layout Splitting
- **Delimiter Centering**:
  - 기간 선택(`~`), 이메일(`@`), 전화번호/계좌번호(`-`) 구분자는 `font-size: 17px`, `line-height: 24px`, `font-weight: 700`으로 고정하며 수직 중앙 정렬합니다.
- **Segmented / Action Add-on Clipping**:
  - 버튼형 및 세그먼트 컨트롤형 서픽스가 결합될 경우 입력 필드 상/하 패딩은 기본 `16px`에서 `8px`로 자동 축소되어 컨트롤의 Hit Target(`32px`) 높이를 충돌 없이 유지합니다.

```css
/* InputField.Item Base Styling & States */
.inputfield-item {
  width: 100%;
  min-height: 56px;
  padding: 16px;
  border-radius: 12px;
  outline: 1px solid var(--border-neutral-primary-muted, #D1D5DB);
  outline-offset: -1px;
  display: flex;
  align-items: center;
  gap: 8px;
  box-sizing: border-box;
}

/* Error State */
.inputfield-item[data-error="true"] {
  outline: 2px solid var(--border-status-negative, #E53838);
  outline-offset: -2px;
}

/* Disabled State */
.inputfield-item[data-disabled="true"] {
  background: var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10));
  outline: none;
}
.inputfield-item[data-disabled="true"][data-entered="false"] {
  opacity: 0.50;
}

/* Textarea Variant */
.inputfield-item[data-variant="textarea"] {
  min-height: 164px;
  padding: 12px 16px;
  align-items: flex-start;
}

/* Caret Cursor Keyframes */
.inputfield-caret {
  width: 1.6px;
  height: 22px;
  background-color: var(--icon-accent-brand-alt, #111827);
  animation: blink 1s step-end infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}
```
