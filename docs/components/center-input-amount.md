# Design-to-Code Specification: Amount Input Display Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - StateVariant1 (Placeholder / Initial State)
    - QuestionLabel ("얼마를 보낼까요?")
    - SubInfoSection (Withdrawal limit text + Limit Badge)
  - StateVariant2 (Active Input State with Cursor)
    - AmountValueText (Pretendard 38px)
    - CursorIndicator (Vertical bar: 1.60x45px)
    - HelperSubText ("240원")
  - StateVariant3 (Completed Standard Amount)
    - AmountValueText ("2,400,000")
    - UnitText ("원")
    - HelperSubText ("240만원")
  - StateVariant4 (Error State / Exceeded Limit)
    - AmountValueText (Negative status color, "9,999,999,999")
    - UnitText ("원")
    - ErrorMessageSection (Icon + Error Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-hasbadge` | Boolean | `true`, `false` |
| `data-status` | Status | `amount`, `error` |
| `data-tone` | Tone | `red` |
| `data-variant` | Variant | `tint` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Root Container Width / Height: 100% (Absolute layout grid variants span horizontally)
  - Inner Section Padding: Left 20px, Right 20px, Top 16px, Bottom 16px
  - Container Radius: 6px
- **타이포그래피 및 컨트롤 스펙**
  - Prompt / Placeholder Text: Font Family `KBFG Text`, Size 32px, Weight 700 (Bold), Line-height 45px
  - Main Numeric Input (Pretendard): Font Family `Pretendard`, Size 38px, Weight 600 (SemiBold), Line-height 53px
  - Unit Text ("원"): Font Family `KBFG Text`, Size 26px, Weight 500 (Medium), Line-height 36px
  - Helper / Sub Text: Font Family `KBFG Text`, Size 13px, Weight 300/500, Line-height 18px
  - Status Badge / Error Text: Font Family `KBFG Text`, Size 11px/13px, Line-height 15px/18px
- **커서 및 인디케이터 치수**
  - Input Cursor: Width 1.60px, Height 45px, Background `var(--icon-accent-brand-alt)`
  - Error Icon Container: Size 12x12px (Inner icon 9x9px)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Variant | Background Token | Text / Value Token | Accent / Border Token |
| :--- | :--- | :--- | :--- |
| **Root Container Border** | `var(--background-neutral-white, white)` | N/A | `var(--color-util-purple, #893DE7)` (1px solid) |
| **Placeholder State** | `transparent` | `var(--text-neutral-secondary-on, #D1D5DB)` | `transparent` |
| **Active / Standard State** | `transparent` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Limit Warning Badge** | `var(--surface-accent-red-muted, #FFF6F5)` | `var(--text-accent-red, #E53838)` | `transparent` |
| **Error / Negative State** | `transparent` | `var(--text-status-negative, #E53838)` | `transparent` |

## 6. 구현 가이드라인
- **Cursor Blinking & Flex Alignment**
  - The active cursor indicator uses a strict fixed width (`1.60px`) and height (`45px`) aligned vertically next to the numeric string using flexbox (`align-items: center`).
- **Dynamic Numeric Formatting & Unit Scaling**
  - Large currency inputs separate the numeric value and the currency unit ("원") into independent flex child nodes to allow responsive font scaling (`Pretendard 38px` vs `KBFG Text 26px`) without vertical baseline misalignment.
- **Error State Handling**
  - When `data-status="error"`, both the numeric value and the inline badge/helper message switch to the status-negative token (`#E53838`) to maintain visual accessibility and alert coherence.
