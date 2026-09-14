# Design-to-Code Specification: Interactive Control Icons & Checkbox Asset Group

## 1. 피그마 메타데이터
- Library Name: 
- Page: 
- Component Name: 
- Figma Link: 

## 2. 컴포넌트 구조 (Hierarchy)
- RootContainer (Wrapper with border radius and purple util border)
  - ControlGroupContainer (Absolute positioned interactive elements)
    - CheckboxControlBox (24x24px bounding box with neutral outline and subtle inner fill)
    - KebabMenuIconAsset (24x24px vertical dots menu icon button)
    - ChevronBackIconAsset (24x24px rotated navigation chevron icon button)
    - LikeFavoriteIconAsset (28x28px heart or favorite icon asset slot)

## 3. 속성 정의 (Properties & Variants)
| Property Name | Variant Type | Description & Values |
| :--- | :--- | :--- |
| `data-checked` | State | `false` |
| `data-disabled` | State | `false` |
| `data-variant` | Variant | `like`, `menu`, `checkbox` |
| `data-size` | Dimension | `24px`, `28px` |

## 4. 상세 레이아웃 스펙
- **컨테이너 및 영역 치수**
  - Checkbox Bounding Box: Width 24px, Height 24px, Radius: 8px (Inner box: 20x20px, Radius: 6px)
  - Menu & Chevron Icon Buttons: Bounding Box 24x24px, Radius: 4px
  - Like / Favorite Icon Asset: Bounding Box 28x28px
- **벡터 및 아이콘 그래픽 스펙**
  - Checkbox Placeholder Vector: 12.36x10.33px positioned at left 3.82px, top 5.03px
  - Kebab Menu Vertical Bars: 3x15px asset positioned at left 10.50px, top 4.50px
  - Chevron Arrow Graphic: 7.29x13.50px with 180-degree rotation transform
  - Favorite Heart Asset: 21.08x19.54px vector graphic centered within 28x28px frame

## 5. 토큰 바인딩 종합 (Token Mapping Matrix)
| Control Element / State | Background Token | Icon / Graphic Token | Border / Outline Token |
| :--- | :--- | :--- | :--- |
| **Unchecked Checkbox** | `transparent` | `var(--icon-accent-brand-alt, #111827)` (10% opacity) | `1px var(--border-neutral-quaternary, #9CA3AF) solid` |
| **Kebab Menu & Chevron Icons** | `transparent` | `var(--icon-neutral-primary, #111827)` | `transparent` |
| **Like / Favorite Icon Asset** | `transparent` | `var(--icon-neutral-secondary-muted, #E5E7EB)` | `transparent` |

## 6. 구현 가이드라인
- **Precision Icon Sizing & Bounding Containers**
  - Interactive control assets enforce rigid square framing (`24x24px` or `28x28px`) with centered flex layouts to guarantee consistent touch targets across forms, headers, and action bars.
- **Checkbox Outline and Opacity Rendering**
  - Unchecked checkboxes apply negative outline offsets (`outlineOffset: '-1px'`) with neutral quaternary borders (`#9CA3AF`) and a low-opacity internal indicator graphic (`opacity: 0.10`) to indicate interactive states cleanly.
