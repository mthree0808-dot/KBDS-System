# Design-to-Code Specification: Slider / Range Slider with Input Field Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - SliderGroupContainer (Vertical flex layout)
    - HeaderSection (Title label, required indicator tag, and info tooltip)
    - SliderControlSection (Interactive slider track with thumbs and optional step stepper buttons)
      - TrackBackgroundBar (Height 8px, fully rounded, neutral muted surface)
      - ActiveFillRangeBar (Height 8px, neutral primary fill or accent brand alt)
      - ThumbHandle (24x24px circular interactive knob with drop shadow and accent border)
      - TooltipBadge (Floating percentage or value label, e.g., "100%")
    - StepperOrInputSection (Optional step buttons or dual input fields for range values)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `barBg`, `single`, `range` |
| `data-required` | Boolean | `true`, `false` |
| `data-tooltip` | Boolean | `true`, `false` |
| `data-haslefttooltip` | Boolean | `true`, `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Slider Track Height: 8px, Radius: 9999px (Fully rounded)
  - Thumb Handle Size: Width 24px, Height 24px, Radius: 9999px, Border: 6px solid accent brand alt
  - Input Field Min-Height: 56px, Padding: 16px, Radius: 12px, Outline: 1px solid neutral primary muted (`#D1D5DB`)
- **타이포그래피 스펙**
  - Title Label: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Tooltip Badge Text: Font Family `KBFG Text`, Size 13px, Weight 700 (Bold) / 500 (Medium)
  - Input Placeholder: Font Family `KBFG Text`, Size 16px, Weight 500 (Medium), Line-height 22px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Element | Background Token | Text / Value Token | Border / Shadow Token |
| :--- | :--- | :--- | :--- |
| **Track Background** | `var(--surface-neutral-primary-muted, #ECEEF2)` | N/A | `transparent` |
| **Active Range Fill** | `var(--surface-neutral-primary, #111827)` | N/A | `transparent` |
| **Thumb Handle Knob** | `var(--surface-neutral-quaternary-muted, white)` | N/A | `0px 4px 16px rgba(12, 17, 29, 0.10)` (Shadow), 6px solid `var(--border-accent-brand-alt, #111827)` |
| **Tooltip Bubble** | `var(--surface-neutral-primary, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Input Field Outline** | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-placeholder, #9CA3AF)` | `1px var(--border-neutral-primary-muted, #D1D5DB) solid` |

## 6. 구현 가이드라인
- **Thumb Handle Positioning & Layering**
  - Slider thumbs utilize absolute positioning (`top: -8px` or `-36px` for tooltips) over the 8px track container to maintain proper touch target dimensions (`24x24px`) without shifting layout baselines.
- **Single vs. Range Slider Behavior**
  - Range variants support dual thumbs (start and end points) with an active fill connecting bar, whereas single variants anchor from the minimum boundary. Stepper buttons or input fields synchronize bi-directionally with the slider position value.
