# Component Specification: CenterInput (Amount & Password Flow)

Figma Component Set 메타데이터 및 Claude Design-to-Code 파이프라인 연동을 위한 전송/송금 및 인증 핵심 입력 컴포넌트 명세서입니다.

---

## 1. Figma Metadata

- Library Name: 진행중) MO 디자인 라이브러리 v0.1
- Page: 02 Input & Selection - 02 CenterInput
- Component NAme: CenterInput
- Figma Link: https://www.figma.com/design/7UdOVppsPPUFvQf57u7Ypc/%E1%84%8C%E1%85%B5%E1%86%AB%E1%84%92%E1%85%A2%E1%86%BC%E1%84%8C%E1%85%AE%E1%86%BC--MO-%E1%84%83%E1%85%B5%E1%84%8C%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%AB-%E1%84%85%E1%85%A1%E1%84%8B%E1%85%B5%E1%84%87%E1%85%B3%E1%84%85%E1%85%A5%E1%84%85%E1%85%B5-v0.1?node-id=5345-140085&t=VJjlk08YauUBRwvm-4

---

## 2. Component Hierarchy

```text
CenterInput Root Container (Width: 390px, Vertical Flex, Center)
├── Primary Display Row (alignSelf: stretch, Align Center, Gap: 2px)
│   ├── [Case A: Placeholder] Text Node ("얼마를 보낼까요?", 32px/45px Bold, Center)
│   ├── [Case B: Typing Focus] 
│   │   ├── Numeric Value Node ("240", 38px/53px SemiBold, Right)
│   │   └── Active Caret Indicator (1.60 x 45px, Accent Brand Fill)
│   ├── [Case C: Value Entered] 
│   │   ├── Formatted Amount Node ("2,400,000", 38px/53px SemiBold, Right)
│   │   └── Currency Unit Node ("원", 26px/36px Medium, Right)
│   └── [Case D: Error State] 
│       ├── Max Amount Node ("9,999,999,999", 38px/53px SemiBold, Status Negative Red)
│       └── Currency Unit Node ("원", 26px/36px Medium, Status Negative Red)
└── Dynamic Sub-Information Row (alignSelf: stretch, Align Center, Gap: 8px or 10px)
    ├── [State: Initial Guide with Badge] (data-hasbadge="true", data-status="amount")
    │   ├── Balance Meta Container (Gap: 1px)
    │   │   ├── Caption Label ("출금가능금액", 13px/18px Light 300)
    │   │   └── Balance Value ("3,000,000원", 13px/18px Medium 500)
    │   └── Tint Badge (data-tone="red", data-variant="tint", 20x20px Min, Radius 4px)
    │       └── Badge Label ("한도제한", 11px/15px Bold 700)
    ├── [State: Korean Currency Preview] (data-hasbadge="false", data-status="amount")
    │   └── Converted Amount Node ("240원" / "240만원", 13px/18px Medium 500)
    └── [State: Error Feedback] (data-hasbadge="true", data-status="error")
        ├── Status Negative Icon Viewport (12x12px, Inner Vector 9x9px)
        └── Validation Error Text ("에러메시지입니다.", 13px/18px Medium 500)
```

---

## 3. Properties & Variants

### 3.1 Container & Presentation Variants

| Property | Attribute | Type | Default Value | Value Range | Description |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Field State** | `data-status` | String | `amount` | `amount`, `error`, `focused` | 서브 정보 영역 노출 모드 및 에러 트리거 |
| **Badge Visibility** | `data-hasbadge` | Boolean | `true` | `true`, `false` | 우측 한도제한 뱃지 또는 상태 인디케이터 표시 여부 |
| **Badge Tone** | `data-tone` | String | `red` | `red`, `neutral` | 안내 뱃지 시각 테마 |
| **Badge Variant** | `data-variant` | String | `tint` | `tint`, `solid` | 배경 틴트 처리형 뱃지 스타일 |

### 3.2 Visual State Matrix

| State Type | Primary Text Layer | Secondary Text Layer | Sub Indicator Element | Applied Token / Color |
| :--- | :--- | :--- | :--- | :--- |
| **Placeholder** | "얼마를 보낼까요?" | - | 출금가능금액 + 한도제한 뱃지 | `var(--text-neutral-secondary-on)` |
| **Typing (Focused)**| 숫자 ("240") | - | 캐럿 커서 (1.6x45px) + 단위 프리뷰 ("240원") | `var(--text-neutral-primary)`, `var(--icon-accent-brand-alt)` |
| **Entered** | 서식 숫자 ("2,400,000") | 단위 ("원") | 한글 금액 프리뷰 ("240만원") | `var(--text-neutral-primary)` |
| **Error** | 최대치 숫자 | 단위 ("원") | 에러 아이콘 (12px) + 에러 메시지 | `var(--text-status-negative)` |

---

## 4. Detailed Layout Specifications

### 4.1 Master Container

- **Width**: Fixed `390px`
- **Internal Padding**: Left `20px`, Right `20px`, Top `16px`, Bottom `16px`
- **Flex Direction**: Column (`flex-direction: column`)
- **Alignment**: `justify-content: center`, `align-items: center`
- **Gap**: `12px` (Primary Text와 Sub Info 사이 수직 간격)

### 4.2 Primary Display Row Metrics

- **Row Container**: Width `100%` (`alignSelf: stretch`), `display: inline-flex`, `justify-content: center`, `align-items: center`, `gap: 2px`
- **Placeholder Text Node**:
  - Font Family: `'KBFG Text', -apple-system, sans-serif`
  - Font Size: `32px`
  - Font Weight: `700` (Bold)
  - Line Height: `45px` (140.6%)
  - Text Align: `center`
- **Entered Amount Text Node**:
  - Font Family: `'Pretendard', -apple-system, sans-serif` (가독성 최적화 영문/숫자 서체)
  - Font Size: `38px`
  - Font Weight: `600` (SemiBold)
  - Line Height: `53px` (139.4%)
  - Text Align: `right`
- **Currency Unit Text Node ("원")**:
  - Font Family: `'KBFG Text', -apple-system, sans-serif`
  - Font Size: `26px`
  - Font Weight: `500` (Medium)
  - Line Height: `36px` (138.4%)
  - Text Align: `right`
- **Blinking Caret Bar**:
  - Width: `1.60px`
  - Height: `45px`
  - Margin Left: `2px` (gap으로 치환)
  - Background: `var(--icon-accent-brand-alt, #111827)`

### 4.3 Dynamic Sub-Information Row Metrics

- **Row Container**: Width `100%` (`alignSelf: stretch`), Height Auto, `align-items: center`
- **A. Guide & Limit Badge Row**:
  - Gap: `8px`
  - Inner Balance Group: Padding Top/Bottom `1px`, Gap `1px`
  - Caption Label: 13px, Line-height 18px, Weight `300` (Light), Color `var(--text-neutral-quaternary)`
  - Balance Value: 13px, Line-height 18px, Weight `500` (Medium), Color `var(--text-neutral-quaternary)`
  - Tint Badge Base: Min-Width `20px`, Height `20px`, Min-Height `20px`, Padding Left/Right `6px`, Border Radius `4px`
  - Badge Text: Font Size `11px`, Line-height `15px`, Weight `700` (Bold), Text Align `center`
- **B. Korean Preview Row**:
  - Gap: `10px`
  - Preview Text Node: Font Size `13px`, Line-height `18px`, Weight `500` (Medium), Text Align `center`
- **C. Error Message Row**:
  - Gap: `8px` (Icon과 Container 간 내부 Gap `1px`)
  - Error Viewport: Width `12px`, Height `12px`, Position `relative`, Overflow `hidden`
  - Error Vector: Width `9.00px`, Height `9.00px`, Inset Top `1.50px`, Left `1.50px`, Absolute
  - Error Text Node: Font Size `13px`, Line-height `18px`, Weight `500` (Medium), Color `var(--text-status-negative)`

---

## 5. Token Mapping Matrix

| State | CSS Token Variable | Fallback HEX | Applied Target Layer | Property |
| :--- | :--- | :--- | :--- | :--- |
| **Canvas Background** | `var(--background-neutral-white, white)` | `#FFFFFF` | CenterInput Master Viewport | `background-color` |
| **Guide Stroke** | `var(--color-util-purple, #893DE7)` | `#893DE7` | Master Canvas Frame Border | `border-color` |
| **Placeholder Text** | `var(--text-neutral-secondary-on, #D1D5DB)` | `#D1D5DB` | "얼마를 보낼까요?" Label | `color` |
| **Primary Value** | `var(--text-neutral-primary, #111827)` | `#111827` | Main Numeric Input / Unit | `color` |
| **Focused Cursor** | `var(--icon-accent-brand-alt, #111827)` | `#111827` | 45px Caret Indicator Bar | `background-color` |
| **Sub Caption Meta** | `var(--text-neutral-quaternary, #6B7280)` | `#6B7280` | 출금가능금액 / 한글 금액 프리뷰 | `color` |
| **Badge Fill (Tint)** | `var(--surface-accent-red-muted, #FFF6F5)` | `#FFF6F5` | 한도제한 뱃지 배경 | `background-color` |
| **Badge Text (Red)** | `var(--text-accent-red, #E53838)` | `#E53838` | 한도제한 뱃지 라벨 | `color` |
| **Error Value & Text**| `var(--text-status-negative, #E53838)` | `#E53838` | 에러 발생 시 입력 금액 / 에러 메시지 | `color` |
| **Error Icon Fill** | `var(--icon-status-negative, #E53838)` | `#E53838` | 12px 에러 인디케이터 백터 | `background-color` |

---

## 6. Implementation Guidelines

### 6.1 Font Hierarchy & Numeric Alignment Rule
- 숫자 입력 데이터의 자간 정밀도와 가독성을 위해 메인 금액에는 `'Pretendard'`를 적용하고, 통화 단위("원") 및 안내 문구에는 디자인 시스템 기본 서체인 `'KBFG Text'`를 합성(Font Fallback / Dual Stack)하여 렌더링합니다.
- 금액 자릿수가 늘어나더라도 상위 컨테이너(`width: 390px`, `padding: 0 20px`) 내부에서 수평 중앙 균형을 맞추기 위해 Primary Row는 `display: inline-flex; justify-content: center;`를 기본으로 유지합니다.

### 6.2 Keyframe & Caret Animation Rule
- 포커스 시 노출되는 `1.6x45px` 수직 캐럿 바는 텍스트 입력 유무와 상관없이 입력 위치 바로 오른쪽에 고정되며 깜빡임(Blink) 처리를 수행합니다.

```css
/* CenterInput Base CSS Rule */
.center-input-container {
  width: 390px;
  box-sizing: border-box;
  padding: 16px 20px;
  display: inline-flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 12px;
  background-color: var(--background-neutral-white, #FFFFFF);
}

/* Primary Number Display */
.center-input-value {
  font-family: 'Pretendard', -apple-system, sans-serif;
  font-size: 38px;
  font-weight: 600;
  line-height: 53px;
  text-align: right;
  color: var(--text-neutral-primary, #111827);
}

.center-input-unit {
  font-family: 'KBFG Text', -apple-system, sans-serif;
  font-size: 26px;
  font-weight: 500;
  line-height: 36px;
  text-align: right;
  color: var(--text-neutral-primary, #111827);
}

/* Large Blinking Caret (45px) */
.center-input-caret {
  width: 1.6px;
  height: 45px;
  background-color: var(--icon-accent-brand-alt, #111827);
  animation: centerInputBlink 1s step-end infinite;
}

@keyframes centerInputBlink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

/* Limit Red Badge */
.limit-tint-badge {
  min-width: 20px;
  height: 20px;
  min-height: 20px;
  box-sizing: border-box;
  padding: 0 6px;
  background-color: var(--surface-accent-red-muted, #FFF6F5);
  border-radius: 4px;
  display: inline-flex;
  justify-content: center;
  align-items: center;
}
```
