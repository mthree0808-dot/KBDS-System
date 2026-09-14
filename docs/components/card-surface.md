# Design-to-Code Specification: Selection Card & Agreement Box Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - AgreementBoxCardContainer (Width: 350px, supporting border outlines, drop shadows, and background fills)
    - ContentStackWrapper (Vertical flex layout with 20px padding and 20px gaps)
      - HeaderSlot (Top structural slot for title or agreement clauses)
      - BodyContentGroup (Nested content block with 12px gap)
      - FooterSlot (Bottom structural slot for description or metadata)
    - TrailingActionOrCheckboxSlot (Absolute positioned top-right control slot supporting menu buttons or checkboxes)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `menu`, `check` |
| `data-checked` | State | `true`, `false` |
| `data-disabled` | State | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Card Width: 350px fixed, Padding: 20px all sides, Radius: 20px
  - Internal Element Gap: 20px vertical gap between content blocks, 16px vertical gap within content stack, 12px horizontal gap
- **컨트롤 및 액션 스펙**
  - Checkbox Bounding Box: 24x24px, Radius: 8px (Inner check target: 20x20px, Radius: 6px)
  - Menu Action Icon: Size 24x24px bounding box with absolute positioning (`left: 306px`, `top: 20px`)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Card Style / State | Background Token | Outline / Border Token | Shadow Token |
| :--- | :--- | :--- | :--- |
| **Neutral White Surface** | `var(--surface-neutral-quaternary-muted, white)` | `transparent` | `transparent` |
| **Neutral Tertiary Muted** | `var(--surface-neutral-tertiary-muted, #F9FAFB)` | `transparent` | `transparent` |
| **Outlined Secondary** | `var(--surface-neutral-quaternary-muted, white)` | `1px var(--border-neutral-secondary-muted, #E5E7EB) solid` | `transparent` |
| **Elevated Shadow Surface**| `var(--surface-neutral-quaternary-muted, white)` | `transparent` | `0px 4px 6px rgba(12, 17, 29, 0.10)` |
| **Active Selected State** | `var(--surface-neutral-quaternary-muted, white)` | `2px var(--border-neutral-primary, #111827) solid` | `transparent` |

## 6. 구현 가이드라인
- **Absolute Positioning for Top-Right Controls**
  - Top-right action controls (such as kebab menu buttons or selection checkboxes) use absolute positioning (`top: 20px`, `left: 306px`) to remain fixed independently of dynamic text expansion within the card body.
- **Stateful Outlines & Negative Offsets**
  - Selection and active states utilize 2px primary outlines (`2px solid #111827`) with negative outline offsets (`outlineOffset: '-2px'`) to preserve clean geometry without altering box model dimensions.
