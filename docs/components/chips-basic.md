# Design-to-Code Specification: Chip / Filter Group Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ChipScrollContainer (Horizontal scrollable or flex-wrap wrapper)
    - GradientFadeMask (Left/Right overlay for scroll indication)
    - ChipItemList (Flex inline container for individual filter chips)
      - ChipItem (Supports selected, default, and outline variants)
        - ChipInnerContent (Padding, gap, and text container)
          - ChipLabelText ("텍스트", 14px KBFG Text)
    - ScrollIndicatorArrow (Navigation overflow indicator icon)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-selected` | State | `true`, `false` |
| `data-hasdotbadge` | Boolean | `false` |
| `data-hasicon` | Boolean | `false` |
| `data-hasnumber` | Boolean | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Chip Container Width: 390px (Fixed standard mobile width)
  - Chip Item Min-Height: 36px
  - Chip Item Padding: Left 12px, Right 12px, Internal Text Padding: Left 4px, Right 4px
  - Border Radius: 9999px (Fully rounded pill shape)
  - Item Gap: 8px spacing between chips
- **폰트 및 타이포그래피 스펙**
  - Selected Chip Label: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Default / Unselected Chip Label: Font Family `KBFG Text`, Size 14px, Weight 500 (Medium), Line-height 20px

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| State / Variant | Background Token | Text / Label Token | Outline / Border Token |
| :--- | :--- | :--- | :--- |
| **Selected (Filled)** | `var(--surface-accent-brand-alt, #111827)` | `var(--text-neutral-primary-on, white)` | `transparent` |
| **Selected (Outlined)** | `transparent` | `var(--text-neutral-primary, #111827)` | `var(--border-accent-brand-alt, #111827)` (1.60px solid) |
| **Default / Unselected** | `var(--background-neutral-light-gray, #F9FAFB)` | `var(--text-neutral-secondary, #374151)` | `var(--border-neutral-secondary-muted, #E5E7EB)` (1px solid) |

## 6. 구현 가이드라인
- **Scroll Gradient & Masking**
  - Scrollable chip groups incorporate linear gradient masks (`linear-gradient(90deg, white 83%, rgba(255, 255, 255, 0) 91%)`) over overflow zones to visually cue horizontal scrollability.
- **Outline Offset Handling**
  - Outlined selected chips use an explicit negative outline offset (`outline-offset: -1.60px` or `-1px`) with precise stroke weights (`1.60px` or `1px`) to prevent visual clipping along pill radii.
- **Flex Wrap & Alignment**
  - Non-scrolling variant groups utilize `flex-wrap` with `align-content: flex-start` to maintain clean multi-line wrapping behavior across variable content lengths.
