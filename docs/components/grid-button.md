# Design-to-Code Specification: Selection Card & Option List Item Component

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - SelectionCardContainer / OptionListItemContainer (Supports grid cards and full-width list items)
    - IconOrAssetContainer (Bounding box for core vector glyphs, size 36x36px)
    - TextContentWrapper (Flex column layout)
      - MainLabelText ("Label", 15px bold KBFG Text)
      - SubLabelText ("subLabel", 13px medium KBFG Text)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-variant` | Variant | `primary`, `secondary` |
| `data-selected` | State | `true`, `false` |
| `data-hassublabel` | Boolean | `true` |
| `data-disabled` | State | `false` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Grid Card Variant: Width ~111.33px, Height 121px, Padding: 16px, Radius: 16px
  - List Item Variant: Self-stretch, Height 65px, Padding: Vertical 12px, Horizontal 20px (Right padding 28px), Radius: 16px
  - Element Gap: 12px spacing between icon asset and text group
- **타이포그래피 및 아이콘 스펙**
  - Main Label Text: Font Family `KBFG Text`, Size 15px, Weight 700 (Bold), Line-height 21px
  - Sub Label Text: Font Family `KBFG Text`, Size 13px, Weight 500 (Medium), Line-height 18px
  - Icon Graphic Box: Size 36x36px bounding box

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Component State / Variant | Background Token | Text / Icon Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Primary Card (Default)** | `var(--surface-neutral-quaternary-muted, white)` | `var(--text-neutral-primary, #111827)` | `1px var(--border-neutral-secondary-muted, #E5E7EB) solid` |
| **Secondary Card (Default)** | `var(--surface-neutral-tertiary-muted, #F9FAFB)` | `var(--text-neutral-primary, #111827)` | `transparent` |
| **Selected State (Active)** | `var(--surface-accent-brand-alt-muted, #F4F6F9)` (or white) | `var(--text-neutral-primary, #111827)` | `2px var(--border-accent-brand-alt, #111827) solid` |

## 6. 구현 가이드라인
- **Active Selection Outlines**
  - Selected states apply a distinct 2px brand outline (`2px var(--border-accent-brand-alt, #111827) solid`) with negative outline offsets (`outlineOffset: '-2px'`) to maintain container dimensions without shifting grid or list alignment.
- **Flexible Grid vs. List Architectures**
  - Supports both vertical grid card layouts (optimized for compact multi-choice selections) and horizontal list rows (optimized for detailed setting options with sub-labels).
