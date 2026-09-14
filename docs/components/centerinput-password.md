# Design-to-Code Specification: Password / PIN Input Indicator Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - PinIndicatorGroupContainer
    - InputSlotsContainer (Flex Wrap Container)
      - PinSlotItem (Supports Dot Variant & Numeric Box Variant)
        - DotIndicator (`16x16px`, circular active/disabled/error states)
        - NumericBoxItem (`48x56px` Min Size, rounded 12px, filled or outlined states)
          - NumericValueText (Pretendard 22px SemiBold)
    - HelperMessageSection (Info or Error text with optional status icon)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-state` | State | `disabled`, `entered`, `error` |
| `data-variant` | Variant | `dot`, `numeric` |
| `data-type` | Type | `empty`, `numeric`, `outline` |
| `data-error` | Boolean | `true`, `false` |
| `data-hasbadge` | Boolean | `true`, `false` |
| `data-status` | Status | `info`, `error` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Root Container Width / Height: 100% (Positioned grid variants spanning horizontally)
  - Inner Padding: Left 20px, Right 20px, Top 28px, Bottom 28px
  - Container Radius: 6px
- **슬롯 및 컨트롤 스펙**
  - Dot Variant Slot: Size 16x16px, Padding: 2px, Border Radius: 9999px (Fully rounded)
  - Numeric Box Variant Slot: Min-Width 48px, Min-Height 56px, Border Radius: 12px
  - Active Outline Focus Box: Border Width 3px, Box Shadow `0px 4px 6px rgba(12, 17, 29, 0.10)`
- **타이포그래피 스펙**
  - Entered Numeric Value: Font Family `Pretendard`, Size 22px, Weight 600 (SemiBold), Line-height 31px
  - Helper / Error Message Text: Font Family `KBFG Text`, Size 13px, Weight 300/500, Line-height 18px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Indicator Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Disabled Dot Slot** | `var(--surface-neutral-disabled, rgba(102, 112, 133, 0.10))` | `var(--border-neutral-disabled, #D1D5DB)` (Border) | `var(--border-neutral-disabled, #D1D5DB)` |
| **Entered Dot Slot** | `var(--icon-neutral-primary, #111827)` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Empty Numeric Box** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | N/A | `var(--border-neutral-primary-muted, #D1D5DB)` |
| **Active Focus Box** | `var(--surface-neutral-quaternary-muted, white)` | N/A | `var(--border-accent-brand-alt, #111827)` (3px solid) |
| **Error Status State** | `var(--surface-status-negative-muted, #FFF6F5)` | `var(--icon-status-negative, #E53838)` | `var(--border-status-negative-muted, #FFBDBD)` |

## 6. 구현 가이드라인
- **Flexible Grid & Slot Alignment**
  - PIN code slots implement flex-wrap with item alignment centering to support dynamic digit lengths (e.g., 4-digit or 6-digit configurations) cleanly within container boundaries.
- **Outline Offset Rendering**
  - Numeric input boxes utilize `outline` with `outline-offset: -1px` or precise border properties to prevent layout shifting during focus states or error validation states.
- **Error State Propagation**
  - When `data-error="true"`, background tokens shift to negative muted states (`#FFF6F5`), dot/numeric indicators switch to status-negative (`#E53838`), and helper messaging displays error tokens uniformly.
