# Design-to-Code Specification: Action Button Group & Service Link Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ActionComponentWrapperGroup (Absolute positioned layout containers)
    - DualActionButtonGroup (Horizontal flex row with 2 equal-width secondary action buttons)
      - ActionButtonLeft ("버튼명", Medium size, secondary variant, 40px min-height, 10px radius)
      - ActionButtonRight ("버튼명", Medium size, secondary variant, 40px min-height, 10px radius)
    - DividerLineComponent (`1px` thickness, tertiary muted border token)
    - ServiceLinkButtonRow (Small size secondary button with trailing chevron arrow icon)
      - LinkButtonLabel ("서비스 바로가기" or "버튼명", 14px bold KBFG Text)
      - TrailingChevronIconSlot (`16x16px` bounding box with rotated arrow asset)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-count` | Number | `2` (Dual button layout count) |
| `data-orientation` | Orientation | `horizontal` |
| `data-ratio` | Ratio | `one-to-one` (Equal width distribution) |
| `data-size` | Dimension | `medium`, `small` |
| `data-variant` | Variant | `secondary` |
| `data-hassuffix` | Boolean | `true` (For link buttons with trailing chevrons) |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Component Container Width: 310px fixed width across all groups
  - Positioning: Absolute positioning offsets (`left: 130px`, `461px`, `top: 126px`, `127px`, `207px`)
  - Dual Action Button Min-Height: 40px, Padding: Horizontal 8px, Vertical 2px, Radius: 10px, Gap: 8px between buttons
  - Divider Line: Height 1px, full stretch width with 20px gap spacing
  - Small Link Button Gap: 2px spacing between button text and trailing chevron icon
- **타이포그래피 및 아이콘 스펙**
  - Dual Button Label Text: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px, Text Center
  - Service Link Button Text: Font Family `KBFG Text`, Size 14px, Weight 700 (Bold), Line-height 20px
  - Trailing Chevron Arrow: Size 16x16px bounding box with 180-degree rotation transform

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component Element | Background Token | Text / Icon Token | Border Token |
| :--- | :--- | :--- | :--- |
| **Dual Action Buttons** | `var(--surface-neutral-secondary-muted, #F4F6F9)` | `var(--text-accent-brand-alt, #111827)` | `transparent` |
| **Divider Line** | `transparent` | N/A | `1px var(--border-neutral-tertiary-muted, #F4F6F9) solid` |
| **Service Link Button** | `transparent` | `var(--text-neutral-quaternary, #6B7280)` / `var(--icon-neutral-quaternary, #9CA3AF)` | `transparent` |

## 6. 구현 가이드라인
- **Equal-Width Dual Button Sizing**
  - Dual action button groups utilize flex distribution (`flex: '1 1 0'`) to ensure both buttons share a strict `1:1` ratio width (`one-to-one`) with a comfortable `40px` minimum height and `10px` border radius for optimal touch accessibility.
- **Divider and Link Alignment**
  - Full-width divider lines (`1px`, `#F4F6F9`) cleanly separate card content sections from footer service link buttons, which align cleanly to the right (`justify-content: flex-end`) with accompanying navigation chevrons.
