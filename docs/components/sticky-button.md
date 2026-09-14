# Design-to-Code Specification: Sticky Bottom CTA Footer with Checkbox & Link

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - StickyFooterWrapper (Width: 390px, Background: White / Light Gray)
    - TopFadeGradientMask (Height: 28px linear gradient blending transparent to surface background)
    - PrimaryCtaButtonContainer (Padding: Bottom 8px, Left/Right 20px)
      - ConfirmButton (Primary CTA, min-height 56px, radius 16px, accent brand background)
    - SecondaryActionRow (Padding: Top 12px, Bottom 8px, Left 28px, Right 32px, space-between layout)
      - AgreementCheckboxGroup (Checkbox item with bold tertiary text label "레이블")
      - UnderlinedTextLinkButton (Small underlined secondary link button "Button")

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-count` | Number | `1` (Single primary CTA orientation) |
| `data-variant` | Variant | `primary`, `secondary` |
| `data-size` | Dimension | `large` (CTA button), `medium` (Checkbox), `small` (Text link) |
| `data-underline` | Boolean | `true` (Underlined text link) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Footer Width: 390px (Standard mobile viewport footer)
  - Top Gradient Mask Height: 28px (`linear-gradient(180deg, rgba(255,255,255,0) 0%, white 75%)`)
  - Primary CTA Padding: Bottom 8px, Left 20px, Right 20px
  - Action Row Padding: Top 12px, Bottom 8px, Left 28px, Right 32px, Space-between alignment
- **컨트롤 및 버튼 스펙**
  - Primary CTA Button: Min-height 56px, Radius: 16px, Padding: Horizontal 12px, Vertical 2px
  - Checkbox Bounding Box: 24x24px, Radius: 8px (Inner target: 20x20px, Radius: 6px)
  - Text Link Underline: Absolute position at top 20px with explicit width matching text bounds (~46px)

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border / Gradient Token |
| :--- | :--- | :--- | :--- |
| **Footer Background (White)** | `var(--background-neutral-white, white)` | N/A | `transparent` |
| **Footer Background (Gray)** | `var(--background-neutral-light-gray, #F9FAFB)` | N/A | `transparent` |
| **Primary CTA Button** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Agreement Checkbox Box** | `transparent` | `var(--text-neutral-tertiary, #4B5563)` (Label text) | `1px var(--border-neutral-quaternary, #9CA3AF) solid` |
| **Secondary Underlined Link** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` | `1px var(--border-neutral-quaternary, #9CA3AF) solid` (Underline) |

## 6. 구현 가이드라인
- **Sticky Footer Gradient Masking**
  - Sticky bottom footers implement a top fade-out gradient mask (`linear-gradient(180deg, ...)` transitioning from fully transparent surface to opaque background) to seamlessly layer over scrolling page contents.
- **Flexbox Alignment & Row Distribution**
  - The secondary action row utilizes `justify-content: space-between` with custom padding (`left: 28px`, `right: 32px`) to balance the left-aligned terms agreement checkbox against the right-aligned text link button.
